# AGENTS.md — Como Agentes Construíram Este Repositório

> Este arquivo documenta como MCP e o Benni Control Plane foram usados no build do Modo Operador.
> Proof não é slide. Proof é commit datado.

---

## Stack de Agentes Ativos

| Agente | Papel | Onde atuou |
|---|---|---|
| **MCP + Claude Desktop** | Agente com contexto real do ambiente | Conectou GitHub + filesystem + Control Plane em sessão única |
| **Benni Control Plane** | Orquestrador de estado e decisões | Decision Ledger, snapshots, runs de execução |

---

## Log de Execução — Build do Modo Operador

### Fase 1 — Scaffold do repositório
- **Agente:** MCP + Claude Desktop
- **Spec:** Criar estrutura base com README, STACK.md, docs/, prompts/, proofs/
- **Resultado:** Estrutura commitada com identidade do produto
- **Proof:** Histórico de commits em `github.com/nsfwbunny/modo-operador/commits`

### Fase 2 — Landing page (index.html)
- **Agente:** MCP + Claude Desktop
- **Spec:** Landing page HTML com identidade do produto, CTA para Cakto, prova técnica embutida
- **Resultado:** `index.html` com design completo, dark mode, responsivo
- **Proof:** Histórico de commits auditável no GitHub

### Fase 3 — Decision Ledger público
- **Agente:** Benni Control Plane (via Perplexity MCP)
- **Spec:** Registrar cada decisão arquitetural com contexto, alternativas rejeitadas e data
- **Resultado:** `docs/DECISION-LEDGER-public.md` com decisões rastreáveis
- **Proof:** Arquivo público — cada decisão tem data ISO 8601

### Fase 4 — Curadoria do repositório
- **Agente:** Benni Master OS (via Perplexity MCP)
- **Spec:** Audit completo do repositório — remover tudo que não reflete o produto real
- **Resultado:** Repositório 100% coerente com `modooperadorplaybook.netlify.app`
- **Proof:** Este commit

---

## Padrão de Operação

```
[Benni] → intenção → spec escrita
    ↓
[MCP + Claude Desktop] → spec executada → artefato entregue
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
