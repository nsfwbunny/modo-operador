# Capítulo 4 — Jules no fluxo de build e ship

> Jules é o agente de coding do Google Labs. Ele lê seu repositório, escreve código com contexto real do projeto e abre PRs. Você revisa e faz merge. Sem terminal, sem setup, sem IDE aberta.

---

## O que Jules faz na prática

Jules não é um autocomplete. Ele é um agente assíncrono:

1. Você descreve a tarefa em linguagem natural
2. Jules analisa o repositório completo
3. Escreve o código (ou documentação, ou configuração)
4. Cria um branch com nome semântico
5. Abre um PR com description detalhando o que foi feito e por quê
6. Você lê, revisa, aprova ou pede ajuste
7. Merge

O repositório `modo-operador` foi parcialmente construído com Jules. Os commits estão no histórico público — auditável por qualquer pessoa.

---

## Como configurar Jules no seu repositório

### Pré-requisitos
- Conta Google com acesso ao Jules (labs.google/jules)
- Repositório GitHub conectado
- Permissões de write no repo

### Setup
1. Acesse `labs.google/jules`
2. Conecte sua conta GitHub
3. Selecione o repositório
4. Jules faz um scan inicial da estrutura do projeto

Presto. Jules agora tem contexto do seu repo.

---

## A anatomia de uma boa tarefa para Jules

Jules funciona melhor com tarefas que têm:
- **Escopo claro** — um problema específico, não "melhora tudo"
- **Contexto de arquivo** — mencione os arquivos relevantes
- **Critério de aceite** — como saber que está correto
- **Restrição de estilo** — se houver padrão de código a seguir

**Exemplo real usado neste projeto:**

```
Lê os arquivos em playbook/. São skeletons vazios com seção '## Notas de desenvolvimento' marcadas como PENDENTE.

Escreve o conteúdo completo do capítulo 03-agentes-como-unidade-de-trabalho.md.

O tom é técnico mas direto — sem linguagem de curso online, sem motivação vazia.
O leitor já sabe o que é IA. Quer saber como operar.

Usa os mesmos padrões de formatação dos capítulos que já têm conteúdo.
Faz commit no branch main com mensagem: feat(playbook): cap 03 completo.
```

---

## Padrões de uso no dia a dia

### Padrão 1 — Feature nova
```
Contexto: [descreve o projeto e o estado atual]
Tarefa: implementa [feature] em [arquivo]
Critério: [como testar que funciona]
Estilo: [linguagem, framework, convenções]
```

### Padrão 2 — Documentação
```
Lê [arquivo de código].
Escreve documentação em [destino] explicando:
- O que faz
- Como usar
- Exemplos de uso reais
Formato: Markdown. Sem jargão desnecessário.
```

### Padrão 3 — Refactor
```
O arquivo [X] tem o problema [Y].
Refatora para [Z] sem quebrar [funcionalidade existente].
Adiciona comentários onde a lógica não é óbvia.
Critério: os testes existentes devem continuar passando.
```

### Padrão 4 — Config e infra
```
Configura [ferramenta] no projeto.
Arquivo de config em [caminho].
Variáveis de ambiente necessárias: [lista].
Não commita secrets — usa nomes de env vars.
```

---

## Revisando PRs do Jules

O PR do Jules tem description automática. Leia ela antes do código.

O que verificar na revisão:

1. **A tarefa foi entendida corretamente?** Jules às vezes interpreta diferente do esperado
2. **Há efeitos colaterais?** Mudanças em arquivos que você não pediu
3. **O estilo segue o padrão?** Nomes de variáveis, formatação, comentários
4. **Os edge cases foram tratados?** Ou Jules assumiu o happy path

Se algo estiver errado, comente no PR com instrução específica. Jules lê o feedback e revisa.

---

## Limitações reais do Jules

Jules não é perfeito. Limitações que você vai encontrar:

- **Contexto de projeto muito grande**: Jules pode perder detalhes em repos com muitos arquivos. Ajuda dar contexto explícito nos arquivos relevantes
- **Lógica de negócio complexa**: Jules não conhece suas regras não escritas. Coloque-as na spec
- **Testes falhando**: Jules nem sempre roda os testes antes de commitar. Verifique o CI
- **Dependências externas**: Jules pode sugerir bibliotecas que não estão no seu stack. Especifique o que pode e o que não pode usar

---

## Jules + MCP — a combinação real

Jules sozinho é poderoso. Jules com MCP é um sistema.

Exemplo de fluxo real:

1. Perplexity MCP pesquisa tendências de mercado
2. Benni Control Plane salva o resultado como snapshot
3. Jules lê o snapshot e escreve um capítulo do playbook baseado nos dados
4. GitHub MCP cria a issue e acompanha o PR
5. Você revisa e faz merge

Cada passo é rastreável. O Decision Ledger registra as decisões. O histórico de commits é a evidência.

---

## Resumo operacional

- Jules = agente assíncrono de coding integrado ao GitHub
- Setup: conecta GitHub, seleciona repo, começa a dar tarefas
- Spec boa: escopo + contexto de arquivo + critério + restrição de estilo
- Revisão: description do PR primeiro, depois o diff
- Limitações: contexto grande, lógica não escrita, dependências
- Jules + MCP = sistema completo de build e ship
