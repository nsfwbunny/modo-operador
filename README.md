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

[![Stack](https://img.shields.io/badge/stack-MCP_%7C_Antigravity_%7C_Decision_Ledger-8052ff?style=for-the-badge)](./STACK.md)
[![Proof](https://img.shields.io/badge/proof-Antigravity_v5_%7C_38_testes-15846e?style=for-the-badge)](https://github.com/nsfwbunny/antigravity)
[![Produto](https://img.shields.io/badge/produto-R$97_%E2%86%92_Acessar-ffb829?style=for-the-badge)](https://nsfwbunny.github.io/modo-operador/)
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

Acervo público do método. Decisões e evidências de um sistema real em produção.

| | Arquivo | O que você encontra |
|---|---|---|
| 📐 | [`STACK.md`](./STACK.md) | Stack técnica completa com exemplos reais |
| 📋 | [`docs/DECISION-LEDGER-public.md`](./docs/DECISION-LEDGER-public.md) | Cada decisão do build — com contexto, evidência e data |
| 🔬 | [`proofs/`](./proofs/) | Evidências verificáveis — sem prova, não entra |
| 🗺️ | [`docs/playbook-outline.md`](./docs/playbook-outline.md) | Estrutura dos 7 capítulos + bônus |

---

## A stack

```
┌─────────────────────────────────────────────────────────────┐
│  MCP — Model Context Protocol                              │
│  └─ Claude Desktop conectado ao GitHub, filesystem, SQLite │
├─────────────────────────────────────────────────────────────┤
│  ANTIGRAVITY                                               │
│  └─ runtime local — FastAPI + SQLite + Ollama              │
│  └─ proof: github.com/nsfwbunny/antigravity (38 testes)   │
├─────────────────────────────────────────────────────────────┤
│  DECISION LEDGER                                           │
│  └─ rastreamento de decisões e continuidade entre sessões  │
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

**Este repositório**
- Commits datados, decisões no [Decision Ledger](./docs/DECISION-LEDGER-public.md)
- Estrutura, stack e decisões — tudo versionado e auditável

---

## O produto

```
7 capítulos         — do prompt isolado ao sistema autônomo
Prompt Library      — 12 specs testadas
MCP Starter Kit     — servidor TypeScript funcional, roda com npm install
Workflow Pack       — 3 workflows JSON prontos para importar
Daily Stack         — checklist operacional para Notion/Obsidian
```

**→ Saiba mais e acesse: [modooperador — landing page](https://nsfwbunny.github.io/modo-operador/)**

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

</div>
