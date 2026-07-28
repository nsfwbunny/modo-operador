<div align="center">

# Modo Operador

**O sistema para usar IA como camada de execução — documentado por quem opera assim.**

*Este repositório é o acervo público. O produto completo está em [modooperadorplaybook.netlify.app](https://modooperadorplaybook.netlify.app).*

[![Stack](https://img.shields.io/badge/stack-Jules%20%7C%20MCP%20%7C%20Antigravity-8052ff?style=flat-square)]()
[![Antigravity](https://img.shields.io/badge/proof-Antigravity%20v5%20%E2%80%94%2038%20testes-15846e?style=flat-square)](https://github.com/nsfwbunny/antigravity)
[![Produto](https://img.shields.io/badge/produto-R%2497%20no%20Cakto-ffb829?style=flat-square)](https://modooperadorplaybook.netlify.app)
[![License](https://img.shields.io/badge/license-MIT-lightgrey?style=flat-square)]()

</div>

---

## O problema que este método resolve

A maioria das pessoas usa IA assim:

```
prompt → resposta → copiar → colar → repetir
```

Isso é uma ferramenta de consulta. Funciona para tarefas isoladas. Não escala. O gargalo é você.

O operador usa assim:

```
intenção → spec → agente executa → sistema entrega → você revisa
```

A diferença não é de velocidade. É de arquitetura. **Você sai do loop sem o sistema parar.**

> **O teste real:** se você fechar o laptop agora, o que continua acontecendo?

---

## O que está neste acervo (gratuito)

| Arquivo | O que entrega |
|---|---|
| [`STACK.md`](./STACK.md) | Documentação técnica completa da stack com exemplos copiáveis |
| [`prompts/`](./prompts/) | Prompts operacionais reais usados no build deste produto |
| [`docs/DECISION-LEDGER-public.md`](./docs/DECISION-LEDGER-public.md) | Decisões rastreáveis do build — com contexto e evidência |
| [`proofs/`](./proofs/) | Evidências reais de execução — sem prova, não entra |
| [`docs/playbook-outline.md`](./docs/playbook-outline.md) | Estrutura completa dos 7 capítulos do playbook |

---

## A stack do operador

Este repositório foi construído usando exatamente o stack que documenta.

```text
Jules (Google Labs)
  └── agente assíncrono de coding
  └── cria branch → escreve código → abre PR
  └── usado para: scaffold do repo, geração de prompts, estrutura de docs

MCP — Model Context Protocol
  └── conecta Claude Desktop ao GitHub, filesystem e SQLite
  └── usado para: commits, leitura de arquivos, queries de estado

Antigravity
  └── runtime local de automações e workflows
  └── usado para: pipeline de conteúdo, processamento de docs, webhooks
  └── proof público: github.com/nsfwbunny/antigravity — 38 testes passando

Benni Control Plane
  └── sistema de orquestração com Decision Ledger e snapshots
  └── usado para: rastreamento de decisões, estado de projeto, CI/CD
```

→ Documentação técnica completa em [`STACK.md`](./STACK.md)

---

## Prova de execução

Nada aqui é afirmado antes de ser executado.

**[Antigravity](https://github.com/nsfwbunny/antigravity)** — o primeiro proof público:
- Runtime local com FastAPI, SQLite e Ollama
- Webhooks com HMAC, approval gate, audit trail imutável
- 38 testes passando, 5 fases de build documentadas
- Construído com Jules, operado com MCP

**Este repositório** — o segundo proof:
- Commits datados com decisões rastreáveis no [Decision Ledger público](./docs/DECISION-LEDGER-public.md)
- PRs criados por agente (Jules) com descrição de raciocínio
- Landing, playbook e bônus — tudo versionado e auditável

> *Proof é código rodando e commits datados. Não é slide.*

---

## O que está no produto (não está aqui)

O acervo público entrega método e evidência. O produto entrega execução:

- **7 capítulos** — do prompt isolado ao sistema autônomo, com specs copiáveis e exemplos de código real
- **Prompt Library** — 12 specs completas testadas em projeto real (Jules, Cursor, Claude Code)
- **MCP Starter Kit** — servidor MCP funcional em TypeScript, 5 tools pré-configuradas, roda com `npm install && npm run build`
- **Workflow Pack Antigravity** — 3 workflows exportáveis em JSON (Content Pipeline, Code Review Assistant, Document Processor)
- **Operador's Daily Stack** — checklist operacional em `.md` + `.json` para Notion/Obsidian

**→ [modooperadorplaybook.netlify.app](https://modooperadorplaybook.netlify.app) — R$97, entrega imediata via Cakto**

---

## Estrutura do repositório

```text
modo-operador/
├── README.md               ← você está aqui
├── STACK.md                ← documentação técnica da stack
├── docs/
│   ├── DECISION-LEDGER-public.md   ← decisões rastreáveis do build
│   ├── playbook-outline.md          ← estrutura dos 7 capítulos
│   ├── proof-plan.md                ← plano de evidências
│   ├── roadmap.md                   ← estado e próximos passos
│   └── vision.md                    ← visão e princípios
├── prompts/
│   ├── README.md                    ← índice dos prompts com quando usar
│   ├── jules-task-active.md         ← spec completa para Jules
│   ├── jules-scaffold.md            ← scaffold de projeto novo
│   └── antigravity-playbook-fill.md ← automação de preenchimento
├── proofs/                 ← evidências reais de execução
└── assets/                 ← landing page e recursos visuais
```

---

## Ecossistema

| Repositório | Papel | Status |
|---|---|---|
| [modo-operador](https://github.com/nsfwbunny/modo-operador) | Este repo — acervo público do método | ✅ Ativo |
| [antigravity](https://github.com/nsfwbunny/antigravity) | Runtime local — proof v5, 38 testes | ✅ Público |
| [monomo](https://github.com/nsfwbunny/monomo) | Agent workspace premium | 🔄 Em build |
| [benni-master-os-skills](https://github.com/nsfwbunny/benni-master-os-skills) | Skills operacionais | 🔒 Privado |

---

<div align="center">

**Operar é diferente de usar.**\
A diferença está na arquitetura — não na ferramenta.

[→ Produto completo](https://modooperadorplaybook.netlify.app)

</div>
