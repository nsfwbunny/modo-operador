# Prompts — Acervo Operacional

> Prompts reais usados no build do Modo Operador.
> Cada arquivo é uma spec testada em uso real — não exemplo teórico.

---

## Como usar

1. Escolha o prompt pelo caso de uso
2. Copie o conteúdo do arquivo
3. Preencha os campos `[entre colchetes]`
4. Cole no agente (Jules, Claude, Cursor)
5. Ajuste o resultado com o loop de refinamento — veja [`STACK.md`](../STACK.md)

---

## Índice

### [`jules-task-active.md`](./jules-task-active.md)
**Quando usar:** task ativa para Jules em repositório existente.\
**O que entrega:** spec completa com objetivo, contexto, comportamento esperado, constraints e critério de done.\
**Pré-requisito:** repositório com README que descreve arquitetura e padrões.

```
Estrutura:
├── ## Objetivo
├── ## Contexto do projeto
├── ## Comportamento esperado
├── ## Constraints técnicas
├── ## Critério de done
└── ## O que NÃO fazer
```

---

### [`jules-scaffold.md`](./jules-scaffold.md)
**Quando usar:** projeto novo do zero — Jules monta a estrutura inicial.\
**O que entrega:** scaffold de repositório com pastas, arquivos base e README.\
**Pré-requisito:** você sabe o stack e o objetivo do projeto.

```
Estrutura:
├── ## Objetivo do projeto
├── ## Stack técnica
├── ## Estrutura esperada
├── ## Arquivos que Jules deve criar
└── ## O que não criar
```

---

### [`antigravity-playbook-fill.md`](./antigravity-playbook-fill.md)
**Quando usar:** automação de preenchimento de conteúdo em lotes via Antigravity.\
**O que entrega:** workflow que lê lista de tópicos, gera conteúdo para cada um e salva em pasta organizada.\
**Pré-requisito:** Antigravity instalado + modelo Ollama local ou chave de API configurada.

```
Estrutura:
├── Trigger: lista de tópicos em CSV ou pasta
├── Ação: gera conteúdo com LLM por item
├── Output: arquivo .md por tópico em /output
└── Log: registro de execução com timestamp
```

---

## O que não está aqui — está no produto

Este acervo tem 3 prompts operacionais. O produto completo inclui:

- **12 specs prontas** — feature, refatoração, testes, bugfix, migração, documentação, review de código, API, componente UI, script de automação, query de banco e deploy
- Cada spec com **variações para Jules, Cursor e Claude Code**
- Templates com campos pré-preenchidos para os casos de uso mais comuns
- **MCP Starter Kit** — servidor MCP funcional em TypeScript pronto para instalar
- **3 workflows Antigravity** exportáveis em JSON

**→ [modooperadorplaybook.netlify.app](https://modooperadorplaybook.netlify.app)**

---

## Princípio de escrita de spec

Uma spec que funciona tem quatro componentes obrigatórios:

| Componente | O que escrever | Erro comum |
|---|---|---|
| **Objetivo** | O que precisa existir ao final | Descrever o processo em vez do resultado |
| **Contexto** | O que o agente precisa saber que não está óbvio | Deixar implícito |
| **Constraints** | O que **não** pode acontecer | Só listar o que pode |
| **Critério de done** | Como validar sem testar tudo | "Funcionar" sem definir o que é funcionar |

O loop de refinamento: execute → observe onde o agente divergiu → identifique o constraint implícito → adicione à spec → execute de novo. Com 3–4 ciclos, a spec estabiliza e vira template.
