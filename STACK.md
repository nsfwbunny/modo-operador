# Stack do Operador — Documentação Técnica

> Este documento descreve a stack usada para construir e operar o Modo Operador.
> Cada ferramenta tem uma função específica no sistema.

---

## Visão geral da arquitetura

```text
┌────────────────────────────────────────────────────────┐
│                    CAMADA DE INTENÇÃO                    │
│              (você define o que precisa ser feito)       │
└──────────────────────────────┬─────────────────────────┘
                               │  spec
                 ┌─────────────┴─────────────┐
                 ▼                           ▼
        ┌──────────────┐         ┌─────────────────┐
        │     MCP      │         │   Antigravity   │
        │  (contexto)  │         │  (automações)   │
        └──────┬───────┘         └──────┬──────────┘
               │                        │
               └───────────┬────────────┘
                           │  output
           ┌───────────────▼───────────────────┐
           │       BENNI CONTROL PLANE          │
           │   Decision Ledger + Snapshots      │
           └────────────────────────────────────┘
```

**Princípio:** cada camada tem uma responsabilidade única. MCP conecta ferramentas. Antigravity orquestra workflows. Control Plane rastreia decisões. Você define intenção e revisa output.

---

## MCP — Model Context Protocol

**O que faz:** padroniza como LLMs se conectam a ferramentas externas. Um servidor MCP expõe ferramentas em formato padrão — qualquer cliente MCP consome sem código de integração customizado.

**Especificação oficial:** [modelcontextprotocol.io](https://modelcontextprotocol.io)

**Arquitetura:**

```text
Host (Claude Desktop / Cursor)
  └── MCP Client
        └── MCP Server
              └── Ferramenta (GitHub, filesystem, SQLite, APIs)
```

**Instalação no Claude Desktop** (`~/Library/Application Support/Claude/claude_desktop_config.json`):

```json
{
  "mcpServers": {
    "github": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-github"],
      "env": { "GITHUB_PERSONAL_ACCESS_TOKEN": "ghp_seu_token" }
    },
    "filesystem": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-filesystem", "/Users/seu-usuario/projetos"]
    }
  }
}
```

**Servidores úteis:**

| Servidor | O que expõe | Caso de uso |
|---|---|---|
| `@mcp/github` | Repos, issues, PRs | Agente que lê e escreve no repo |
| `@mcp/filesystem` | Leitura/escrita de arquivos | Agente que processa docs locais |
| `@mcp/sqlite` | Queries SQL | Agente que consulta banco local |
| `@mcp/fetch` | HTTP requests | Agente que consome APIs |
| `@mcp/puppeteer` | Browser | Agente que navega e extrai dados |

**Segurança:**
- Token com escopo mínimo — apenas o repo necessário
- Ações destrutivas sempre com confirmação humana na spec
- Nunca cole tokens no chat

---

## Antigravity — Runtime Local de Automações

**O que faz:** canvas visual onde você conecta nós (triggers, ações, LLMs) sem depender de cloud. Dados ficam na sua máquina.

**Proof público:** [github.com/nsfwbunny/antigravity](https://github.com/nsfwbunny/antigravity)

**Casos de uso:**

```text
Content Pipeline
  trigger: schedule diário
  ação: busca + filtra com LLM
  output: arquivo local + notificação

Code Review Automático
  trigger: webhook PR aberto
  ação: lê diff + gera review com LLM
  output: comentário no PR
```

**Backend local com Ollama:**

```bash
curl -fsSL https://ollama.ai/install.sh | sh
ollama pull llama3.1:8b
```

**AMV — Automação Mínima Viável:** roda sem intervenção, falha de forma visível, output utilizável direto.

---

## Benni Control Plane — Orquestração

**O que faz:** Decision Ledger (decisões rastreáveis), snapshots de projeto, continuidade entre sessões.

```json
{
  "decision": "Entrega via Cakto — checkout nativo, área de membros, email automático.",
  "context": "Reduz stack a uma ferramenta. Zero infra adicional.",
  "created_at": "2026-07-24T09:55:34.270Z"
}
```

---

## Ordem de adoção

```text
Semana 1: MCP + Claude Desktop → acesso controlado ao agente
Semana 2: Antigravity → converter processo manual em workflow
Semana 3: Control Plane → continuidade entre sessões
Semana 4: integrar as três camadas → sistema que roda sem você
```

---

*Produto completo com specs e bônus via [pay.cakto.com.br/pfuibmt_999515](https://pay.cakto.com.br/pfuibmt_999515)*
