# Playbook Outline — Modo Operador

## Regra de escrita

- Cada capítulo tem pelo menos 1 exemplo real executado pelo autor.
- Nenhum capítulo afirma resultado que não foi comprovado.
- Linguagem funcional, sem jargão motivacional.
- Cada capítulo declara: **o que você sai capaz de fazer**.

---

## Capítulos

### Cap 1 — O novo jogo da IA aplicada
**O que você sai capaz de fazer:** Identificar com precisão se você está usando IA ou operando IA — e o que muda na arquitetura quando você inverte a relação.

**Conteúdo:** O ciclo manual vs. o ciclo do operador. Por que o gargalo é você, não o modelo. A diferença entre velocidade e arquitetura.

**Exemplo real:** Diagrama real do fluxo usado no build do Modo Operador — da intenção ao commit sem presença constante.

---

### Cap 2 — De prompt para sistema
**O que você sai capaz de fazer:** Escrever uma spec operacional — não um prompt — que um agente consegue executar de forma autônoma e verificável.

**Conteúdo:** Anatomia de uma spec vs. anatomia de um prompt. O que precisar estar na spec para o agente não precisar perguntar. Controle por evidência, não por microgestão.

**Exemplo real:** Spec usada para Jules scaffoldar o repositório `modo-operador` — com resultado auditável em commits datados.

---

### Cap 3 — Agentes como unidade de trabalho
**O que você sai capaz de fazer:** Criar um agente especializado para uma tarefa repetível do seu workflow — com spec, execução e entrega sem você em cada passo.

**Conteúdo:** O que define um agente (vs. um assistente). Como escolher a granularidade certa de tarefa. Loop de handoff entre agentes.

**Exemplo real:** Jules executando spec de feature no `antigravity` — PR aberto, testes passando, sem intervenção manual no meio.

---

### Cap 4 — Jules no fluxo de build e ship
**O que você sai capaz de fazer:** Usar Jules para executar tarefas de código reais — do scaffold ao PR — com histórico auditável e reversível.

**Conteúdo:** Setup do Jules no repositório. Como escrever a task-spec para Jules. O que Jules faz bem, o que ele não faz. Revisão do PR como única interação necessária.

**Exemplo real:** 4 PRs abertos por Jules no build do `modo-operador` — commits, diffs e histórico públicos.

---

### Cap 5 — MCP como camada de contexto
**O que você sai capaz de fazer:** Conectar um agente ao seu GitHub, filesystem local e banco de dados usando MCP — sem depender de API cara ou plataforma de terceiro.

**Conteúdo:** O que é MCP e por que é diferente de uma integração comum. Setup do MCP Starter Kit (bônus). 5 tools que resolvem 80% dos casos reais.

**Exemplo real:** Claude Desktop conectado via MCP ao GitHub + Benni Control Plane — executando commits e registrando decisões em sessão única.

---

### Cap 6 — Automações úteis e ativos digitais
**O que você sai capaz de fazer:** Construir um workflow que executa uma tarefa útil recorrente sem sua presença — e entender quais automações valem o tempo de construção.

**Conteúdo:** Critério para decidir o que automatizar. FastAPI + SQLite + Ollama como runtime local. Webhooks com approval gate. O que o Antigravity resolve e como replicar.

**Exemplo real:** Workflow do Antigravity com 3 steps rodando local — sem custo de API, com audit trail imutável e 38 testes passando.

---

### Cap 7 — Portfólio, distribuição e receita
**O que você sai capaz de fazer:** Transformar o sistema que você construiu em portfólio verificável, autoridade técnica e ativo digital que gera receita sem depender da sua presença constante.

**Conteúdo:** Repo público como prova de trabalho. Decision Ledger como narrativa de autoridade. Produto digital construído com a mesma stack que ensina. Distribuição por evidência, não por volume de conteúdo.

**Exemplo real:** Este playbook — produto digital em HTML, distribuído via Cakto, com acervo público no GitHub, construído com Jules + MCP + Control Plane, gerando receita com R$97 Early Access.
