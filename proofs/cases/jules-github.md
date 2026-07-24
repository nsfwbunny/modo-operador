# Case — Jules → GitHub

## Nome do caso
Build via Jules sem código manual

## Problema
Construir e validar estrutura de repositório sem usar terminal ou IDE, delegando execução para um agente de IA conectado ao GitHub.

## Sistema construído
Jules conectado ao repositório `nsfwbunny/modo-operador` via branch `feat/jules-scaffold-task`. Recebeu prompt determinístico com 5 passos e executou sem desvio: validou estrutura, atualizou arquivos e abriu PR automaticamente.

## Stack usada
Jules + GitHub MCP + Perplexity (orquestração)

## Evidência
- PR aberto pelo Jules: https://github.com/nsfwbunny/modo-operador/pull/3
- Task Jules: https://jules.google.com/task/9025743338291513607
- Merge feito em: 2026-07-24
- Arquivos alterados: `README.md`, `proofs/cases/jules-github.md`
- Adicionado por Jules: linha de rodapé no README + campos do case atualizados

## Status
✅ CONCLUÍDO — evidencia real publicada

## Próxima ação
Usar este case como exemplo concreto no Capítulo 4 do playbook (`04-jules-no-fluxo-de-build-e-ship.md`).
