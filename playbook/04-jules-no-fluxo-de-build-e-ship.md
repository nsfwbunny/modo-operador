# Capítulo 4 — Jules no fluxo de build e ship

## Objetivo

Mostrar como usar Jules para construir e entregar código, documentação e estrutura de projeto sem depender de IDE ou terminal — usando um caso real executado neste próprio repositório como exemplo.

---

## 1. O que é Jules e como ele se conecta ao GitHub

Jules é um agente de IA da Google que opera diretamente em repositórios GitHub. Você conecta um repositório, dá uma tarefa em linguagem natural, e o Jules executa: cria arquivos, modifica código, abre pull requests.

A diferença em relação a usar ChatGPT ou Claude diretamente: o Jules não te entrega texto para você copiar e colar. Ele opera no repositório, faz o commit e abre o PR. Você revisa e aprova.

**Como conectar:**
1. Acesse https://jules.google.com
2. Clique em "New Task"
3. Selecione o repositório GitHub (precisa autorizar acesso na primeira vez)
4. Selecione o branch de trabalho
5. Cole o prompt da tarefa
6. Aguarde — Jules executa de forma assíncrona, você recebe notificação quando termina

---

## 2. Tarefas que Jules executa bem

- Criar estrutura de pastas e arquivos de scaffold
- Escrever e atualizar arquivos Markdown (docs, READMEs, changelogs)
- Modificar campos específicos em arquivos existentes sem alterar o resto
- Criar arquivos de configuração (JSON, YAML, TOML)
- Adicionar rodapés, cabeçalhos e metadados em arquivos existentes
- Abrir PR com título e body já definidos no prompt

Regra: quanto mais determinístico o prompt, mais fiel a execução. Instrua linha por linha. Não deixe espaço para o Jules "decidir" o que fazer.

---

## 3. Tarefas que Jules não deve executar sozinho

- Escrever conteúdo de produto (capítulos, copy, argumentos de venda)
- Tomar decisões de arquitetura sem especificação prévia
- Refatorar código crítico sem gate de revisão humana
- Fazer merge direto em `main` sem PR
- Qualquer ação com efeito externo (deploy, envio de email, publicação)

Regra: Jules é execução dentro de um branch. O merge é sempre gate humano.

---

## 4. Como revisar e aprovar um PR gerado por Jules

Depois que Jules termina, ele abre um PR. Antes de fazer merge:

1. Abra o PR no GitHub
2. Vá em "Files changed"
3. Verifique arquivo por arquivo: Jules fez só o que foi pedido?
4. Se algum arquivo foi alterado fora do escopo, não faça merge — comente e peça correção
5. Se estiver correto, faça merge com squash (um commit limpo no histórico)

---

## 5. Caso real — scaffold do modo-operador

Este capítulo foi escrito depois de uma execução real. Aqui estão os fatos:

**Data:** 2026-07-24

**Tarefa dada ao Jules:**
Validar a estrutura de pastas do repositório `modo-operador`, verificar arquivos obrigatórios, atualizar campos específicos em dois arquivos e abrir PR.

**O que Jules fez:**
- Verificou estrutura de pastas
- Atualizou `README.md`: trocou emojis por texto limpo, adicionou linha de rodapé
- Atualizou `proofs/cases/jules-github.md`: preencheu campos Sistema construído, Stack, Evidencia e Status
- Abriu PR #3 com título e body corretos

**O que Jules não fez:**
- Não alterou conteúdo dos capítulos do playbook
- Não inventou dados
- Não abriu PR direto para `main` (foi para o branch correto)

**Resultado:**
- PR #3 aberto: https://github.com/nsfwbunny/modo-operador/pull/3
- Task Jules: https://jules.google.com/task/9025743338291513607
- Merge feito com squash, histórico limpo
- Arquivos alterados: 2
- Linhas adicionadas: 8 | Linhas removidas: 6

**Conclusão do caso:**
Jules executou dentro do escopo. O prompt determinístico funcionou. O fluxo completo — prompt → execução assíncrona → PR → revisão → merge — levou menos de 10 minutos com zero uso de terminal.

---

## O que você faz agora

1. Acesse https://jules.google.com
2. Conecte ao seu repositório
3. Copie o prompt em `prompts/jules-task-active.md` como base
4. Adapte para sua tarefa específica
5. Aguarde o PR
6. Revise arquivo por arquivo
7. Faça merge só se estiver dentro do escopo

Esse fluxo funciona para qualquer repositório. Não é necessário saber programar para usar Jules em tarefas de documentação, scaffold e organização.
