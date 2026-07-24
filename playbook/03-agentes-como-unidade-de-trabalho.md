# Capítulo 3 — Agentes como unidade de trabalho

## Objetivo

Explicar o que é um agente de IA na prática e como usá-lo como unidade de execução — não como assistente. Usando JARVAS 2 como sistema real de referência.

---

## 1. O que diferencia um agente de um chatbot

Um chatbot responde. Um agente executa.

A diferença não é de inteligência — é de arquitetura. Um chatbot recebe um prompt e devolve texto. Um agente recebe um objetivo, planeja passos, executa ações no mundo real (criar arquivos, abrir PRs, rodar scripts, acessar APIs) e registra o resultado para usar no próximo ciclo.

| Chatbot | Agente |
|---|---|
| Você digita, ele responde | Você define objetivo, ele executa |
| Resultado é texto | Resultado é ação no mundo |
| Cada conversa começa do zero | Tem memória de execuções anteriores |
| Você copia e cola | Ele commita, cria, envia |
| Sem loop de feedback | Aprende com resultados passados |

---

## 2. Os dois tipos de agente que importam agora

**Agentes conectados a ferramentas externas** (Jules, Antigravity):
Operam em repositórios, filesystems e APIs. Você dá a tarefa, eles executam de forma assíncrona e entregam um resultado verificável (PR, arquivo, commit).

**Agentes autônomos locais** (JARVAS 2, sistemas customizados):
Rodam na sua máquina. Você define o objetivo, o agente planeja, simula, pede aprovação para ações críticas e executa em loop. O estado é 100% seu — sem nuvem, sem dependência externa.

Para quem está começando: Jules e Antigravity são o caminho mais rápido. Para quem quer soberania total: um agente local como JARVAS 2 é o objetivo de longo prazo.

---

## 3. Como dar uma tarefa real sem perder controle

O erro mais comum: prompt vago. "Melhore meu projeto" não é uma tarefa para agente — é um convite para invenção.

Uma tarefa real para agente tem:
1. **Escopo fechado** — lista exata de arquivos ou pastas envolvidos
2. **Ações determinísticas** — "criar", "atualizar campo X", "abrir PR com título Y"
3. **Restrições explícitas** — o que não fazer é tão importante quanto o que fazer
4. **Entrega verificável** — o que você vai checar para confirmar que funcionou

Exemplo ruim:
```
Organize meu repositório
```

Exemplo bom:
```
Verifique se as pastas docs/, playbook/ e proofs/ existem.
Se alguma estiver faltando, crie um arquivo .gitkeep dentro.
Não altere nenhum arquivo existente.
Abra um PR com título "chore: scaffold validation".
```

---

## 4. Gates de aprovação — quando deixar o agente rodar sozinho

Todo agente precisa de um gate — um ponto onde a execução para e espera aprovação humana antes de continuar.

A arquitetura do JARVAS 2 formaliza isso em três níveis de risco:

| Nível | Tipo de ação | Comportamento |
|---|---|---|
| Baixo | Leitura, busca, geração de texto | Executa sem parar |
| Médio | Criação de arquivos, commits, PRs | Para, exibe proposta, aguarda OK |
| Alto | Deploy, envio de email, pagamento, delete | Bloqueado até autorização explícita |

Para Jules e Antigravity o gate é o PR: o agente não faz merge sozinho. Você revisa e aprova. Esse é o mínimo viável de controle.

---

## 5. Caso real — JARVAS 2

**Sistema:** agente autônomo local, Python, rodando 100% na máquina do operador.

**Arquitetura real implementada:**
```
Objetivo → Planner → Simulator (dry-run) → Human Gate → Execution → SQLite Memory → loop
```

**O que já funciona hoje:**
- Orquestrador CLI (`main.py`) inicializa o loop de execução
- Dashboard local (`uvicorn dashboard.app:app`) exposta em `localhost:8000`
- Fila de tarefas com inspeção via `/tasks` e `/queue`
- Gate de aprovação via `/approvals` e `/approve-task`
- Audit trail com snapshot e rollback via `/audit/{id}/rollback`
- Simulação de workflow via `/simulate/workflow` antes de executar
- Capability Registry: mapa de permissões por ferramenta

**Stack:** Python 3.10+, FastAPI, SQLite, Playwright, JSON local — zero dependência de cloud.

**Repositório:** https://github.com/nsfwbunny/jarvas-2

**O que este caso prova:**
Você pode construir um agente autônomo real — com memória, gate de aprovação e audit trail — usando só Python e ferramentas open source. Sem assinar nenhum serviço de agente externo.

---

## O que você faz agora

Se quiser começar com agentes hoje, o caminho mais curto é:

1. Use Jules para tarefas de repositório (Capítulo 4 deste playbook)
2. Use Antigravity para tarefas de criação de arquivos e escrita determinística
3. Quando precisar de loop autônomo real com memória — estude a arquitetura do JARVAS 2

A progressão natural: prompt → Jules/Antigravity → agente local → swarm.
