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

[![Stack](https://img.shields.io/badge/stack-MCP_%7C_Antigravity_%7C_Control_Plane-8052ff?style=for-the-badge&logo=data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAyNCAyNCI+PHBhdGggZmlsbD0id2hpdGUiIGQ9Ik0xMiAyTDIgN2wxMCA1IDEwLTV6bTAgMTBMNCAxMmw4IDQgOC00eiIvPjwvc3ZnPg==)](./STACK.md)
[![Proof](https://img.shields.io/badge/proof-Antigravity_v5_%7C_38_testes-15846e?style=for-the-badge)](https://github.com/nsfwbunny/antigravity)
[![Landing](https://img.shields.io/badge/landing-modooperadorplaybook.netlify.app-0ea5e9?style=for-the-badge)](https://modooperadorplaybook.netlify.app)
[![Produto](https://img.shields.io/badge/produto-R$97_no_Cakto-ffb829?style=for-the-badge)](https://modooperadorplaybook.netlify.app)
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
| 🗺️ | [`docs/playbook-outline.md`](./docs/playbook-outline.md) | Os 7 capítulos + 4 bônus — estrutura completa |

---

## A stack

Este repositório foi construído usando exatamente o que documenta.

```
┌─────────────────────────────────────────────────────────────┐
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

**Este repositório** — proof público
- Commits datados, decisões no [Decision Ledger](./docs/DECISION-LEDGER-public.md)
- Landing page, playbook e bônus — tudo versionado

---

## O produto

Este acervo entrega **método e evidência**. O produto entrega **execução**:

```
7 capítulos         — do prompt isolado ao sistema autônomo
Prompt Library      — 12 specs testadas (Cursor, Claude Code, MCP)
MCP Starter Kit     — servidor TypeScript funcional, 5 tools, roda com npm install
Workflow Pack       — 3 workflows JSON para Antigravity (pronto para importar)
Daily Stack         — checklist operacional .md + .json para Notion/Obsidian
```

**→ [modooperadorplaybook.netlify.app](https://modooperadorplaybook.netlify.app)**

---

## Estrutura

```
modo-operador/
├── README.md                           ← você está aqui
├── STACK.md                            ← stack técnica completa
├── AGENTS.md                           ← como agentes construíram este repo
├── docs/
│   ├── DECISION-LEDGER-public.md       ← decisões rastreáveis
│   ├── playbook-outline.md             ← 7 capítulos + 4 bônus
│   ├── roadmap.md                      ← estado atual e próximos passos
│   └── vision.md                       ← princípios do método
├── prompts/
│   └── README.md                       ← índice + quando usar cada spec
├── proofs/                             ← evidências de execução real
└── index.html                          ← playbook completo (netlify deploy)
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

[`→ Ver o playbook`](https://modooperadorplaybook.netlify.app)

<br/>

</div>
