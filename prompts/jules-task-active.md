# Jules Task — Scaffold Validation

## Instrucóes de uso

1. Abra Jules: https://jules.google.com
2. Conecte ao repositório `nsfwbunny/modo-operador`
3. Selecione o branch `feat/jules-scaffold-task`
4. Cole o prompt abaixo exatamente como está
5. Aguarde o Jules abrir o PR
6. Revise e faça merge

---

## Prompt para o Jules

```
Task: validate and complete the scaffold of the Modo Operador repository.

Do exactly the following steps in order. Do not skip any step.

Step 1 - Verify folders exist:
  docs/
  playbook/
  proofs/
  proofs/cases/
  prompts/
  assets/
  assets/landing/

If any folder is missing, create a file called .gitkeep inside it.

Step 2 - Verify these files exist:
  README.md
  docs/vision.md
  docs/roadmap.md
  docs/playbook-outline.md
  docs/proof-plan.md
  playbook/00-map.md
  playbook/01-o-novo-jogo-da-ia-aplicada.md
  playbook/02-de-prompt-para-sistema.md
  playbook/03-agentes-como-unidade-de-trabalho.md
  playbook/04-jules-no-fluxo-de-build-e-ship.md
  playbook/05-mcp-como-camada-de-contexto.md
  playbook/06-automacoes-uteis-e-ativos-digitais.md
  playbook/07-portfolio-distribuicao-e-receita.md
  proofs/cases/jarvas.md
  proofs/cases/jules-github.md
  proofs/cases/mcp-stack.md
  proofs/cases/media-engine.md

If any file is missing, create it as an empty markdown file with only a H1 title matching the filename.

Step 3 - Update proofs/cases/jules-github.md:
  - Set field "Status" to: EM ANDAMENTO
  - Set field "Sistema construido" to: Jules conectado ao repositorio modo-operador via branch feat/jules-scaffold-task
  - Set field "Stack usada" to: Jules + GitHub
  - Set field "Evidencia necessaria" to: PR aberto e mergeado com resultado verificavel
  - Set field "Proxima acao" to: Documentar o PR gerado nesta task como evidencia do case
  - Do not change any other field.

Step 4 - Update README.md:
  Replace the line that says "| Landing page | Em construcao |" with:
  "| Landing page | Em construcao |"
  Replace the line that says "| Playbook | Skeleton criado |" with:
  "| Playbook | Skeleton criado |"
  Add a new line below the table:
  "_Ultima atualizacao por Jules via scaffold task._"

Step 5 - Open a pull request:
  - From branch: feat/jules-scaffold-task
  - To branch: main
  - Title: feat: jules scaffold validation complete
  - Body: Este PR foi gerado pelo Jules como parte do case jules-github documentado em proofs/cases/jules-github.md

Do not invent content. Do not write sales copy. Do not modify playbook chapter content.
```
