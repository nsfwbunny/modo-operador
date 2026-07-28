# Stack do Operador — Documentação Técnica

> Este documento descreve a stack usada para construir e operar o Modo Operador.
> Cada ferramenta tem uma função específica no sistema. Nenhuma é opcional na arquitetura atual.

---

## Visão geral da arquitetura

```text
┌────────────────────────────────────────────────────────┐
│                    CAMADA DE INTENÇÃO                    │
│              (você define o que precisa ser feito)       │
└──────────────────────────────┬─────────────────────────┘
                               │  spec
           ┌───────────────────┼───────────────────┐
           ▼                   ▼                   ▼
    ┌─────────────┐  ┌──────────────┐  ┌─────────────────┐
    │    Jules    │  │     MCP      │  │   Antigravity   │
    │  (coding)  │  │  (contexto)  │  │  (automações)   │
    └──────┬──────┘  └──────┬───────┘  └──────┬──────────┘
           │                │                  │
           └────────────────┼──────────────────┘
                            │  output
           ┌────────────────▼──────────────────┐
           │       BENNI CONTROL PLANE          │
           │   Decision Ledger + Snapshots      │
           └────────────────────────────────────┘
```

**Princípio de arquitetura:** cada camada tem uma responsabilidade única. Jules escreve código. MCP conecta ferramentas. Antigravity orquestra workflows. O Control Plane rastreia decisões. Você define a intenção e revisa o output.

---

## Jules — Agente de Coding Assíncrono

**O que faz:** recebe uma spec em linguagem natural, lê o repositório inteiro, cria uma branch, implementa a solução e abre um PR com descrição do raciocínio.

**Onde vive:** [labs.google.com/jules](https://labs.google.com/jules)

**Fluxo operacional:**

```text
1. Você cria issue ou task descrevendo o que precisa
2. Atribui ao Jules via interface do Google Labs
3. Jules clona o repo e lê o código existente
4. Jules cria branch, implementa, abre PR
5. Você revisa, solicita ajustes ou faz merge
```

**Onde Jules performa melhor:**
- Features com escopo limitado e critério de done claro
- Refatoração seguindo padrão estabelecido no repo
- Testes unitários para funções já escritas
- Correção de bugs com reprodução clara na spec

**Onde Jules falha (e como contornar):**

| Falha | Contorno |
|---|---|
| Ambiguidade de arquitetura | Documente o padrão correto no README ou em comentários |
| Tasks com múltiplos domínios | Separe em tasks distintas — uma por domínio |
| Contexto de produto ausente | Cole o contexto diretamente na spec |
| Scope creep | Adicione seção "O que NÃO fazer" com paths exatos |

**Template de spec que funciona:**

```markdown
## Objetivo
[O que precisa existir ao final — resultado, não processo]

## Contexto
[Stack, padrões existentes, decisões de arquitetura relevantes]

## Comportamento esperado
[Casos de uso reais, estados de loading/erro/sucesso]

## Constraints técnicas
[Bibliotecas permitidas/proibidas, versões, padrões a seguir]

## Critério de done
[Como validar sem testar tudo manualmente]

## O que NÃO fazer
[Arquivos fora do escopo, refatorações não solicitadas]
```

---

## MCP — Model Context Protocol

**O que faz:** padroniza como LLMs se conectam a ferramentas externas. Um servidor MCP expõe ferramentas em formato padrão — qualquer cliente MCP consome sem código de integração customizado.

**Especificação oficial:** [modelcontextprotocol.io](https://modelcontextprotocol.io)

**Arquitetura:**

```text
Host (Claude Desktop / Cursor)
  └── MCP Client (camada de comunicação)
        └── MCP Server (processo que expõe ferramentas)
              └── Ferramenta (GitHub, filesystem, SQLite, APIs)
```

**Instalação no Claude Desktop:**

Edite `~/Library/Application Support/Claude/claude_desktop_config.json` (Mac) ou `%APPDATA%\Claude\claude_desktop_config.json` (Windows):

```json
{
  "mcpServers": {
    "github": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-github"],
      "env": {
        "GITHUB_PERSONAL_ACCESS_TOKEN": "ghp_seu_token"
      }
    },
    "filesystem": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-filesystem", "/Users/seu-usuario/projetos"]
    },
    "sqlite": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-sqlite", "/Users/seu-usuario/data.db"]
    }
  }
}
```

Reinicie o Claude Desktop. Ícone de ferramentas na barra inferior confirma ativação.

**Servidores úteis para começar:**

| Servidor | O que expõe | Caso de uso imediato |
|---|---|---|
| `@mcp/github` | Repos, issues, PRs, commits | Agente que lê e escreve no repositório |
| `@mcp/filesystem` | Leitura e escrita de arquivos | Agente que processa documentos locais |
| `@mcp/sqlite` | Queries SQL em banco local | Agente que consulta e atualiza dados |
| `@mcp/fetch` | Requisições HTTP | Agente que consome APIs externas |
| `@mcp/puppeteer` | Controle de browser | Agente que navega e extrai dados de sites |

**Regras de segurança inegociáveis:**
- Token com escopo mínimo — `read-only` para o repo específico, não para toda a conta
- Ações destrutivas (delete, deploy) sempre com confirmação humana explícita na spec
- Nunca cole tokens no chat — use apenas o arquivo de configuração
- Revogue tokens de desenvolvimento após cada sessão

---

## Antigravity — Runtime Local de Automações

**O que faz:** canvas visual de automações onde você conecta nós — triggers, ações, condições, agentes LLM — sem depender de cloud. Seus dados ficam na sua máquina. Zero custo por execução.

**Repositório público do proof:** [github.com/nsfwbunny/antigravity](https://github.com/nsfwbunny/antigravity)

**Casos de uso reais em produção:**

```text
Content Pipeline
  trigger: schedule diário 08h
  ação: busca artigos via fetch MCP
  ação: filtra por relevância com LLM
  output: resumo em arquivo local + notificação

Code Review Assistant
  trigger: webhook — PR aberto no GitHub
  ação: lê diff via GitHub MCP
  ação: gera review com LLM
  output: comentário automático no PR

Document Processor
  trigger: arquivo novo em /entrada
  ação: extrai dados estruturados com LLM
  output: linha em CSV ou banco SQLite
```

**Ollama como backend local:**

```bash
# Instalar Ollama
curl -fsSL https://ollama.ai/install.sh | sh

# Baixar modelo
ollama pull llama3.1:8b

# Testar
curl http://localhost:11434/api/generate -d '{"model":"llama3.1:8b","prompt":"ok?"}'
```

No nó LLM do Antigravity: `model: ollama/llama3.1:8b` + `base_url: http://localhost:11434`

**AMV — Automação Mínima Viável:**

Antes de construir o workflow perfeito, construa o mais simples que resolve o problema. Um AMV tem três critérios:
1. Roda sem intervenção sua
2. Falha de forma visível (você sabe quando quebrou)
3. Output utilizável sem pós-processamento manual

---

## Benni Control Plane — Orquestração e Rastreamento

**O que faz:** sistema de controle com Decision Ledger (decisões rastreáveis com contexto), snapshots de projeto e MCP ativo. Usado para rastrear o estado de cada projeto, registrar decisões tomadas e garantir continuidade entre sessões.

**Conceito central — Decision Ledger:**

Cada decisão relevante é registrada com:
- O que foi decidido
- Por quê (contexto e evidência)
- Data e ID rastreável

Isso elimina a necessidade de rediscutir decisões já tomadas e cria um rastro auditável do build.

**Exemplo de entrada no ledger:**

```json
{
  "decision": "Entrega do produto via link privado pós-compra no Cakto — sem repo público, sem PDF externo.",
  "context": "Cakto tem checkout nativo, área de membros e envio de email automático. Reduz stack a uma ferramenta.",
  "created_at": "2026-07-24T09:55:34.270Z"
}
```

---

## Princípio de integração

Não use todas as ferramentas ao mesmo tempo desde o início. A ordem de adoção que funciona:

```text
Semana 1: Jules para uma task bem definida
  → aprende a escrever spec que funciona

Semana 2: MCP com github + filesystem no Claude Desktop
  → aprende a dar acesso controlado ao agente

Semana 3: Antigravity para uma automação que você já faz manualmente
  → aprende a converter processo manual em workflow

Semana 4: Control Plane para rastrear decisões do projeto ativo
  → aprende a criar continuidade entre sessões
```

Cada ferramenta resolve um problema específico. A integração é consequência do uso, não pré-requisito.

---

*Documentação técnica viva — atualizada conforme o stack evolui.*\
*Produto completo com specs copiáveis e bônus em [modooperadorplaybook.netlify.app](https://modooperadorplaybook.netlify.app)*
