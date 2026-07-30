# AGENTS.md — Como Agentes Construíram Este Repositório

> Este arquivo documenta como Jules e MCP foram usados no build do Modo Operador.
> Proof não é slide. Proof é commit datado.

---

## Stack de Agentes Ativos

| Agente | Papel | Onde atuou |
|---|---|---|
| **Jules (Google Labs)** | Agente de coding assíncrono | Criou branches, escreveu código, abriu PRs |
| **MCP + Claude Desktop** | Agente com contexto real do ambiente | Conectou GitHub + filesystem + Control Plane em sessão única |
| **Benni Control Plane** | Orquestrador de estado e decisões | Decision Ledger, snapshots, runs de execução |

---

## Log de Execução — Build do Modo Operador

### Fase 1 — Scaffold do repositório
- **Agente:** Jules
- **Spec:** Criar estrutura base com README, STACK.md, docs/, prompts/, proofs/
- **Resultado:** Branch criada, estrutura commitada, PR aberto sem intervenção manual
- **Proof:** Histórico de commits em `github.com/nsfwbunny/modo-operador/commits`

### Fase 2 — Landing page (index.html)
- **Agente:** MCP + Claude Desktop
- **Spec:** Landing page HTML com identidade do produto, CTA para Cakto, prova técnica embutida
- **Resultado:** `index.html` (57KB) com design completo, dark mode, responsivo
- **Proof:** Commit `bfa9af6` — diff auditável no GitHub

### Fase 3 — Decision Ledger público
- **Agente:** Benni Control Plane (via Perplexity MCP)
- **Spec:** Registrar cada decisão arquitetural com contexto, alternativas rejeitadas e data
- **Resultado:** `docs/DECISION-LEDGER-public.md` com 8 decisões rastreáveis
- **Proof:** Arquivo público — cada decisão tem data ISO 8601

### Fase 4 — Preview do produto
- **Agente:** Jules
- **Spec:** `preview.html` — teaser do playbook com capítulo 1 parcial, gate de compra
- **Resultado:** Arquivo de 13KB commitado e versionado
- **Proof:** Commit em `bfa9af6` — diff público

### Fase 5 — Curadoria e email de venda
- **Agente:** Benni Master OS (via Perplexity MCP)
- **Spec:** Audit completo do repositório + sequência de 4 emails para Cakto
- **Resultado:** `AGENTS.md` (este arquivo) + `docs/playbook-outline.md` reescrito
- **Proof:** Este commit — `feat: add AGENTS.md + rewrite playbook-outline`

---

## Padrão de Operação

```
[Benni] → intenção → spec escrita
    ↓
[Jules / MCP] → spec executada → artefato entregue
    ↓
[Benni Control Plane] → decisão registrada no ledger
    ↓
[Benni] → revisa e aprova → merge
```

O gargalo não é mais a execução. É a qualidade da spec.

---

## Por que isso importa

Este repositório documenta o método. Este arquivo documenta que o método foi usado para construir o próprio repositório.

Isso não é marketing. É arquitetura verificável.

Cada commit tem data. Cada PR tem histórico. Cada decisão tem contexto.

`→ github.com/nsfwbunny/modo-operador/commits`
