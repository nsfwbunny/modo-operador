# Case — JARVAS 2

## Nome do caso
JARVAS 2 — agente autônomo local-first com gate de aprovação humana

## Problema
Construir um sistema de agente autônomo que execute tarefas reais — automação, pesquisa, operações externas — sem depender de infraestrutura cloud, sem expor dados a serviços externos e sem perder controle sobre ações irreversíveis.

## Sistema construído

JARVAS 2 é um OS de agente autônomo rodando 100% local. O sistema é constituído por:

- **Planner:** define estratégia e fluxo de trabalho a partir de um objetivo
- **Simulator:** executa dry-run antes de qualquer mutação de estado
- **Human Approval Gate:** pausa operações de médio e alto risco até autorização manual
- **Execution Engine:** executa ações aprovadas com verificação de idempotência
- **Outcome Memory:** registra resultados em SQLite local para feedback loop
- **Operator Console:** dashboard FastAPI com Jinja2 para monitorar filas, aprovar ações e consultar audit logs

Arquitetura: `Objetivo → Planner → Simulator → Gate → Execution → Memory → loop`

Milestones concluídos:
- [x] Core Foundation: persistência local, JSON stores, orquestrador CLI
- [x] Operator Observability: dashboard Jinja2, Audit Trails, Policy Gates
- [x] Execution Connectors: sandbox guards, simulações, capability registry

## Stack usada

- Python 3.10+
- FastAPI + Uvicorn (dashboard local)
- SQLite (ledger de auditoria: `jarvas.db`)
- Playwright (automação de browser)
- JSON stores locais (sem Redis, sem Celery, sem bancos externos)
- GitHub para versionamento

## Evidência

- Repositório: https://github.com/nsfwbunny/jarvas-2 (privado — evidencia vía estrutura documentada)
- `main.py` existe e inicializa o orquestrador
- `requirements.txt` lista dependências reais (FastAPI, Playwright, etc.)
- `uvicorn.log` presente — servidor rodou localmente
- `dashboard/` e `core/` existem como módulos separados
- `AGENTS.md` documenta comportamento esperado dos agentes
- 3 milestones concluídos conforme README

## Status

⚠️ EM DESENVOLVIMENTO — Milestones 1-3 concluídos. Milestone 4 (execução real com Playwright) em andamento.

## Próxima ação

Tornar repositório público ou gravar demo do Operator Console rodando localmente para usar como evidência pública no Capítulo 3 do playbook.
