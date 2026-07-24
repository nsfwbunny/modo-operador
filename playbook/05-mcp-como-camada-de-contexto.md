# Capítulo 5 — MCP como camada de contexto

> Model Context Protocol não é uma ferramenta. É um protocolo — a camada que permite que qualquer modelo de IA se conecte a qualquer sistema externo de forma padronizada.

---

## O que é MCP e por que importa

Antes do MCP, cada integração de IA com ferramenta externa era um hack:
- Plugin proprietário que só funciona com um modelo
- API wrapper que você constrói do zero
- Dependência de uma plataforma específica

O MCP muda isso. Ele define um protocolo aberto:
- Qualquer servidor MCP expõe ferramentas de forma padronizada
- Qualquer cliente compatível (Claude, Cursor, Antigravity, sistemas customizados) conecta
- As ferramentas são descobertas automaticamente

O resultado prático: você monta uma vez, conecta em qualquer lugar.

---

## A arquitetura em três linhas

```
Modelo de IA  ←→  Cliente MCP  ←→  Servidor MCP  ←→  Sistema externo
(raciocina)      (protocolo)       (traduz)           (GitHub, DB, API)
```

- O **modelo** decide quando usar uma ferramenta
- O **cliente** faz a chamada no protocolo correto
- O **servidor** executa a ação no sistema externo
- O **sistema** retorna o resultado

---

## Servidores MCP que este playbook usa

### GitHub MCP
Permite que qualquer agente opere no GitHub:
- Ler/escrever arquivos em repositórios
- Criar issues, PRs, branches
- Listar commits, revisar diffs
- Fazer merge

Neste projeto: usado para criar landing page, escrever capítulos, registrar decisões — tudo via Perplexity + MCP, sem abrir o GitHub no browser.

### Benni Control Plane MCP
O sistema de orquestração central:
- `project_list` / `project_get_active_state` — boot de sessão
- `decision_add` — registra decisões no ledger
- `project_save_snapshot` — salva estado do projeto
- `artifact_create` — persiste artefatos linkados ao projeto

Funciona como a memória do sistema. Cada sessão começa lendo o estado anterior.

### Perplexity MCP
Pesquisa em tempo real integrada ao fluxo:
- Busca web com síntese
- Consultas direcionadas a fontes específicas
- Dados atuais sem alucinação

Caso de uso real: antes de escrever qualquer capítulo, o agente pesquisa o que já existe no mercado para evitar repetição e identificar gaps.

---

## Como montar um servidor MCP

Dois caminhos:

### Caminho 1 — Usar servidor existente (mais rápido)
Lista de servidores MCP prontos: [github.com/modelcontextprotocol/servers](https://github.com/modelcontextprotocol/servers)

Instala, configura o endpoint, conecta no cliente. Feito.

### Caminho 2 — Construir servidor customizado
Use o SDK oficial:
```bash
npm install @modelcontextprotocol/sdk
```

Estrutura básica de um servidor MCP em TypeScript:
```typescript
import { Server } from '@modelcontextprotocol/sdk/server/index.js';
import { StdioServerTransport } from '@modelcontextprotocol/sdk/server/stdio.js';

const server = new Server({ name: 'meu-servidor', version: '1.0.0' }, {
  capabilities: { tools: {} }
});

server.setRequestHandler(ListToolsRequestSchema, async () => ({
  tools: [{
    name: 'minha_ferramenta',
    description: 'O que ela faz',
    inputSchema: { type: 'object', properties: { input: { type: 'string' } } }
  }]
}));

server.setRequestHandler(CallToolRequestSchema, async (req) => {
  // sua lógica aqui
  return { content: [{ type: 'text', text: resultado }] };
});

await server.connect(new StdioServerTransport());
```

O Benni Control Plane foi construído exatamente assim — servidor MCP TypeScript com endpoints de projeto, decisão e artefato.

---

## MCP no Antigravity — orquestração local

Antigravity usa MCP como protocolo nativo.

Fluxo local:
1. Antigravity carrega os servidores MCP configurados
2. Você descreve o workflow em linguagem natural
3. Antigravity orquestra as chamadas entre ferramentas
4. Resultado agregado é retornado

Isso permite criar pipelines como:
```
Pesquisa mercado [Perplexity MCP]
→ Salva resultado [Benni Control Plane MCP]
→ Escreve capítulo [GitHub MCP via Jules]
→ Cria issue de revisão [GitHub MCP]
```

Tudo local, sem depender de plataforma cloud.

---

## Segurança e boas práticas

- **Nunca commite API keys** — use variáveis de ambiente
- **Escopos mínimos** — dê ao servidor MCP só as permissões que ele precisa
- **Audit trail** — o Benni Control Plane já faz isso; use o Decision Ledger
- **Timeout em chamadas** — servidores MCP devem ter timeout explícito
- **Validação de input** — nunca passe input do usuário direto para sistema externo sem sanitizar

---

## Resumo operacional

- MCP = protocolo aberto, modelo ↔ sistema externo
- Arquitetura: modelo → cliente → servidor → sistema
- Servidores usados: GitHub MCP, Benni Control Plane, Perplexity
- Construir servidor: SDK TypeScript, 50 linhas para o básico
- Antigravity = orquestrador local que fala MCP nativamente
- Segurança: env vars, escopos mínimos, audit trail
