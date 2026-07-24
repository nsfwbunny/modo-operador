# Capítulo 2 — De prompt para sistema

> A transição mais importante que um operador de IA faz não é de ferramenta. É de mentalidade.

---

## O problema com pensar em prompts

Quando você pensa em termos de prompts, você está pensando em **perguntas**.

"Como faço X?"
"Me explica Y."
"Escreve Z para mim."

O resultado é uma resposta. Você usa, descarta, repete.

Quando você pensa em termos de sistemas, você está pensando em **fluxos**.

"Quero que toda vez que aconteça A, o agente execute B e entregue C."

O resultado é uma máquina. Você configura uma vez, o sistema roda.

---

## Os três elementos de um sistema de IA

Todo sistema de IA operacional tem três partes:

### 1. Contexto
O que o agente sabe antes de começar. Inclui:
- O objetivo da tarefa
- As restrições (o que não fazer)
- O estado atual (onde estamos)
- Os recursos disponíveis (ferramentas, arquivos, APIs)

Sem contexto rico, o agente age no escuro. Com contexto rico, ele age com precisão.

### 2. Instrução
O que o agente deve executar. Não é um prompt genérico — é uma spec.

Diferença:
- **Prompt:** "Crie uma landing page"
- **Instrução de sistema:** "Crie `assets/landing/index.html` com hero dark, Three.js para fundo 3D, copy focado em waitlist, fonte Instrument Serif + Inter, sem dependências externas além de CDN. Commit no branch main com mensagem `feat: landing page`."

Especificidade é o que separa resultado utilizável de resultado genérico.

### 3. Loop de revisão
O agente entrega. Você revisa. Você aprova ou refina. O sistema aprende com o padrão.

Isso não é micromanagement — é calibração. Você só entra quando o resultado sai da spec.

---

## Como migrar um fluxo manual para sistema

Exercício prático. Pense em uma tarefa que você faz repetidamente:

**Antes (manual):**
1. Você abre o ChatGPT
2. Digita a tarefa
3. Recebe resposta
4. Formata manualmente
5. Publica
6. Repete amanhã

**Depois (sistema):**
1. Você define a spec uma vez (qual tarefa, qual formato, qual destino)
2. Agente executa quando acionado
3. Você revisa o output
4. Sistema publica automaticamente
5. Amanhã acontece sem você

O trabalho não desaparece. Ele sobe de nível. Você passa de executor para arquiteto.

---

## O erro mais comum na transição

Tentar automatizar tudo de uma vez.

A transição certa é incremental:

1. **Identifique** uma tarefa repetitiva que você já faz bem manualmente
2. **Documente** o processo em linguagem clara (isso já é 80% do trabalho)
3. **Monte** o contexto + instrução para o agente
4. **Execute** uma vez, revise o output
5. **Refine** a spec com base no que saiu errado
6. **Automatize** só depois que o padrão estiver validado

Sistemas construídos em cima de processos mal entendidos não funcionam. Sistemas construídos em cima de processos que você já executa bem funcionam da primeira vez.

---

## Resumo operacional

- Pense em fluxos, não em perguntas
- Contexto rico = output preciso
- Instrução específica > prompt genérico
- Automatize o que você já faz bem, não o que você quer fazer
- O loop de revisão é onde a qualidade nasce
