<div align="center">

<br/>

```
 ███╗   ███╗ ██████╗ ██████╗  ██████╗      ██████╗ ██████╗ ███████╗██████╗  █████╗ ██████╗  ██████╗ ██████╗
 ████╗ ████║██╔═══██╗██╔══██╗██╔═══██╗    ██╔═══██╗██╔══██╗██╔════╝██╔══██╗██╔══██╗██╔══██╗██╔═══██╗██╔══██╗
 ██╔████╔██║██║   ██║██║  ██║██║   ██║    ██║   ██║██████╔╝█████╗  ██████╔╝███████║██║  ██║██║   ██║██████╔╝
 ██║╚██╔╝██║██║   ██║██║  ██║██║   ██║    ██║   ██║██╔═══╝ ██╔══╝  ██╔══██╗██╔══██║██║  ██║██║   ██║██╔══██╗
 ██║ ╚═╝ ██║╚██████╔╝██████╔╝╚██████╔╝    ╚██████╔╝██║     ███████╗██║  ██║██║  ██║██████╔╝╚██████╔╝██║  ██║
 ╚═╝     ╚═╝ ╚═════╝ ╚═════╝  ╚═════╝      ╚═════╝ ╚═╝     ╚══════╝╚═╝  ╚═╝╚═╝  ╚═╝╚═════╝  ╚═════╝ ╚═╝  ╚═╝
```

### IA como camada de execução — não como ferramenta de consulta.

<br/>

[![Stack](https://img.shields.io/badge/stack-Jules_%7C_MCP_%7C_Antigravity-8052ff?style=for-the-badge&logo=data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAyNCAyNCI+PHBhdGggZmlsbD0id2hpdGUiIGQ9Ik0xMiAyTDIgN2wxMCA1IDEwLTV6bTAgMTBMNCAxMmw4IDQgOC00eiIvPjwvc3ZnPg==)](./STACK.md)
[![Proof](https://img.shields.io/badge/proof-Antigravity_v5_%7C_38_testes-15846e?style=for-the-badge)](https://github.com/nsfwbunny/antigravity)
[![Produto](https://img.shields.io/badge/produto-R$97_no_Cakto-ffb829?style=for-the-badge)](https://pay.cakto.com.br/pfuibmt_999515)
[![Status](https://img.shields.io/badge/status-ativo-4ade80?style=for-the-badge)]()

<br/>

> **Se você fechar o laptop agora — o que continua acontecendo?**

<br/>

</div>

---

## O problema

A maioria das pessoas usa IA como uma busca glorificada:

```
[você] → prompt → resposta → copiar → colar → repetir → [você de novo]
```

O gargalo é você. Sempre você. O sistema não age sem você.

O operador usa assim:

```
[você] → intenção → spec → agente executa → sistema entrega → [você revisa]
         └─────────────────────────────────────────────────┘
                     isso acontece sem você presente
```

A diferença não é de velocidade. É de **arquitetura**.

---

## Este repositório

Acervo público do método. Código, decisões e evidências de um sistema real em produção.

| | Arquivo | O que você encontra |
|---|---|---|
| 📐 | [`STACK.md`](./STACK.md) | Stack técnica completa com exemplos reais e copiáveis |
| 🧠 | [`prompts/`](./prompts/) | Specs operacionais usadas no build deste produto |
| 📋 | [`docs/DECISION-LEDGER-public.md`](./docs/DECISION-LEDGER-public.md) | Cada decisão do build — com contexto, evidência e data |
| 🔬 | [`proofs/`](./proofs/) | Evidências verificáveis — sem prova, não entra |
| 🗺️ | [`docs/playbook-outline.md`](./docs/playbook-outline.md) | Os 7 capítulos do playbook — estrutura completa |

---

## A stack

Este repositório foi construído usando exatamente o que documenta.

```
┌─────────────────────────────────────────────────────────────┐
│  JULES (Google Labs)                                        │
│  └─ agente assíncrono de coding                            │
│  └─ cria branch → escreve código → abre PR                 │
│  └─ você escreve a spec. Jules executa.                    │
├─────────────────────────────────────────────────────────────┤
│  MCP — Model Context Protocol                              │
│  └─ Claude Desktop conectado ao GitHub, filesystem, SQLite │
│  └─ agente com acesso real ao ambiente — não só ao chat    │
├─────────────────────────────────────────────────────────────┤
│  ANTIGRAVITY                                               │
│  └─ runtime local de automações e workflows                │
│  └─ FastAPI + SQLite + Ollama — sem custo de API           │
│  └─ proof: github.com/nsfwbunny/antigravity (38 testes)   │
├─────────────────────────────────────────────────────────────┤
│  BENNI CONTROL PLANE                                       │
│  └─ orquestrador com Decision Ledger e snapshots           │
│  └─ rastreia decisões, estado e CI/CD                      │
└─────────────────────────────────────────────────────────────┘
```

→ Documentação técnica completa: [`STACK.md`](./STACK.md)

---

## Prova

> *Proof é código rodando e commits datados. Não é slide.*

**[Antigravity](https://github.com/nsfwbunny/antigravity)** — proof público v5
- FastAPI + SQLite + Ollama rodando local
- Webhooks com HMAC, approval gate, audit trail imutável
- 38 testes passando, 5 fases de build documentadas
- Construído com Jules via spec, operado com MCP

**Este repositório** — proof público v2
- Commits datados, decisões no [Decision Ledger](./docs/DECISION-LEDGER-public.md)
- PRs abertos por Jules — histórico público e auditável
- Landing page, playbook e bônus — tudo versionado

---

## O produto (não está aqui)

Este acervo entrega **método e evidência**. O produto entrega **execução**:

```
7 capítulos         — do prompt isolado ao sistema autônomo
Prompt Library      — 12 specs testadas (Jules, Cursor, Claude Code)
MCP Starter Kit     — servidor TypeScript funcional, 5 tools, roda com npm install
Workflow Pack       — 3 workflows JSON para Antigravity (pronto para importar)
Daily Stack         — checklist operacional .md + .json para Notion/Obsidian
```

**→ [modooperadorplaybook.netlify.app](https://modooperadorplaybook.netlify.app)**

**→ [Adquirir por R$97](https://pay.cakto.com.br/pfuibmt_999515)**

---

## Estrutura

```
modo-operador/
├── README.md                           ← você está aqui
├── STACK.md                            ← stack técnica completa
├── docs/
│   ├── DECISION-LEDGER-public.md       ← decisões rastreáveis
│   ├── playbook-outline.md             ← 7 capítulos detalhados
│   ├── roadmap.md                      ← estado atual e próximos passos
│   └── vision.md                       ← princípios do método
├── prompts/
│   ├── README.md                       ← índice + quando usar cada spec
│   ├── jules-task-active.md            ← spec para Jules (feature ativa)
│   ├── jules-scaffold.md               ← scaffold de projeto novo
│   └── antigravity-playbook-fill.md    ← automação de preenchimento
└── proofs/                             ← evidências de execução real
```

---

## Ecossistema

| Repositório | Papel | Status |
|---|---|---|
| [`modo-operador`](https://github.com/nsfwbunny/modo-operador) | Acervo público do método | `✅ ativo` |
| [`antigravity`](https://github.com/nsfwbunny/antigravity) | Runtime local — 38 testes, 5 fases | `✅ público` |
| [`monomo`](https://github.com/nsfwbunny/monomo) | Agent workspace premium | `🔄 build` |
| [`benni-master-os-skills`](https://github.com/nsfwbunny/benni-master-os-skills) | Skills operacionais | `🔒 privado` |

---

<div align="center">

<br/>

**Operar IA é diferente de usar IA.**

*A diferença está na arquitetura — não na ferramenta.*

<br/>

[`→ Ver o playbook`](https://modooperadorplaybook.netlify.app) &nbsp;·&nbsp; [`→ Adquirir R$97`](https://pay.cakto.com.br/pfuibmt_999515)

<br/>

</div>
