# AGENTS.md — Como Agentes Construíram Este Repositório

> Proof não é slide. Proof é commit datado.

---

## Stack de Agentes

| Agente | Papel |
|---|---|
| **MCP + Claude Desktop** | Contexto real do ambiente — GitHub + filesystem + Control Plane |
| **Benni Control Plane** | Orquestrador — Decision Ledger, snapshots, continuidade |

---

## Log de Execução

### Fase 1 — Scaffold
- Agente: MCP + Claude Desktop
- Resultado: estrutura base, README, STACK.md, docs/, prompts/
- Proof: commits em `github.com/nsfwbunny/modo-operador/commits`

### Fase 2 — Documentação técnica
- Agente: MCP + Claude Desktop
- Resultado: STACK.md completo, DECISION-LEDGER, playbook-outline
- Proof: diff auditável no GitHub

### Fase 3 — Decision Ledger público
- Agente: Benni Control Plane (via Perplexity MCP)
- Resultado: `docs/DECISION-LEDGER-public.md` com decisões rastreáveis
- Proof: cada entrada tem data ISO 8601

### Fase 4 — Curadoria
- Agente: Benni Master OS (via Perplexity MCP)
- Resultado: repositório 100% alinhado ao produto real
- Proof: este commit

---

## Padrão

```
[Benni] → intenção → spec
    ↓
[MCP + Claude] → executa → entrega artefato
    ↓
[Control Plane] → decisão no ledger
    ↓
[Benni] → revisa → merge
```

O gargalo não é mais execução. É qualidade da spec.

`→ github.com/nsfwbunny/modo-operador/commits`
