# Capítulo 3 — Agentes como unidade de trabalho

> Um agente não é um chatbot mais esperto. É uma unidade autônoma de execução com acesso a ferramentas, contexto e capacidade de agir no mundo.

---

## O que é um agente de verdade

A palavra "agente" foi diluída. Todo produto de IA agora se chama agente.

Para os fins deste playbook, agente é:

> **Um modelo de linguagem com acesso a ferramentas que pode executar sequências de ações para atingir um objetivo, tomando decisões intermediárias sem intervenção humana a cada passo.**

Os três componentes críticos:
- **Modelo** — o cérebro (GPT-4o, Gemini, Claude)
- **Ferramentas** — o que o agente pode fazer (ler arquivos, escrever código, chamar APIs, buscar na web)
- **Loop de execução** — o agente age, observa o resultado, decide o próximo passo

Sem ferramentas, é só geração de texto.
Sem loop de execução, é só uma resposta.

---

## Os três tipos de agente que você vai usar

### Tipo 1 — Agente de coding (Jules)
Especializado em repositórios. Lê código, escreve código, testa, cria branches, abre PRs.

**Quando usar:** build, refactor, documentação técnica, testes automatizados.

**O que faz sozinho:** análise do repositório, escrita de código com contexto do projeto, commit com mensagem semântica, abertura de PR com description.

**O que precisa de você:** spec clara da tarefa, aprovação do PR, definição de critérios de aceite.

### Tipo 2 — Agente de orquestração (MCP + Antigravity)
Conecta ferramentas e gerencia fluxos. Não escreve código — coordena quem escreve e o que acontece com o resultado.

**Quando usar:** workflows multi-passo, integração entre sistemas, automações que cruzam múltiplas ferramentas.

**O que faz sozinho:** chamar APIs, passar dados entre sistemas, acionar outros agentes, gerenciar estado.

**O que precisa de você:** definição do fluxo completo, tratamento de edge cases, monitoramento de falhas.

### Tipo 3 — Agente de pesquisa (Perplexity MCP)
Busca, filtra e sintetiza informação em tempo real. Retorna dados estruturados que outros agentes consomem.

**Quando usar:** validação de mercado, monitoramento de concorrência, pesquisa para conteúdo, dados em tempo real.

**O que faz sozinho:** múltiplas buscas paralelas, síntese de resultados, formatação para downstream.

**O que precisa de você:** definição do que é relevante vs. ruído, critérios de qualidade.

---

## Como dar tarefas para agentes

O erro mais comum: tratar agente como chatbot e dar tarefas vagas.

**Errado:**
```
"Melhora o README do projeto"
```

**Certo:**
```
Lê o arquivo README.md atual.
O produto é um playbook de IA operacional chamado Modo Operador.
Reescreve a seção '## O que é o Modo Operador' para:
- Ser mais direto (máx 3 parágrafos)
- Remover a linguagem de marketing genérica
- Deixar claro que é um sistema documentado, não um curso
- Manter o tom técnico mas acessível
Faz commit com mensagem: docs: rewrite what-is section para clareza
```

Especificidade é respeito pelo tempo do agente — e pelo seu.

---

## A anatomia de uma boa spec para agente

```markdown
## Contexto
[O que o agente precisa saber sobre o projeto/estado atual]

## Tarefa
[O que deve ser feito, em linguagem precisa]

## Critérios de aceite
[Como saber que está correto]

## Restrições
[O que NÃO fazer]

## Output esperado
[Formato, localização, nome de arquivo, mensagem de commit]
```

Esse template funciona para Jules, para automações MCP e para qualquer agente de execução.

---

## Quando não usar agente

Agente não é a resposta para tudo.

**Não use agente quando:**
- A tarefa leva menos de 2 minutos para você fazer manualmente
- O critério de aceite é subjetivo e você não consegue descrever o que "certo" significa
- A tarefa requer julgamento que só você tem (estratégia, relacionamento, intuição de produto)
- O custo de erro é alto e não existe loop de revisão antes do impacto

**Use agente quando:**
- A tarefa é repetitiva e bem definida
- Você consegue descrever o output correto com precisão
- O loop de revisão é mais rápido que fazer manualmente
- O volume justifica o setup inicial

---

## Resumo operacional

- Agente = modelo + ferramentas + loop de execução
- Três tipos: coding (Jules), orquestração (MCP), pesquisa (Perplexity)
- Spec específica = resultado utilizável
- Use o template: contexto + tarefa + critérios + restrições + output
- Não automatize o que não está bem definido
