# Prompt Library — Modo Operador

> Specs operacionais usadas no build deste produto. Copiáveis, adaptáveis, testadas.
> O produto completo inclui 12 specs com contexto de uso e variações.

---

## O que é uma spec operacional

Uma spec não é um prompt de chat. É um documento estruturado que define:
- O que o agente precisa entregar (output, não processo)
- O contexto necessário para executar (stack, padrões, decisões)
- Os critérios de done (como validar sem testar tudo manualmente)
- O que **não** fazer (escopo negativo — reduz drasticamente erros)

A qualidade da spec determina a qualidade do output. Não o modelo.

---

## Specs neste repositório

| Arquivo | Agente alvo | Caso de uso |
|---|---|---|
| [`antigravity-playbook-fill.md`](./antigravity-playbook-fill.md) | Claude / MCP | Preencher capítulos do playbook com conteúdo real |

---

## Template base (copiável)

```markdown
## Objetivo
[O que precisa existir ao final — resultado, não processo]

## Contexto
[Stack, padrões existentes, decisões de arquitetura relevantes]

## Comportamento esperado
[Casos de uso reais, estados de loading/erro/sucesso]

## Constraints técnicas
[Bibliotecas permitidas/proibidas, versões, padrões a seguir]

## Critério de done
[Como validar sem testar tudo manualmente]

## O que NÃO fazer
[Arquivos fora do escopo, refatorações não solicitadas]
```

---

*Produto completo com 12 specs + MCP Starter Kit + Workflow Pack em [modooperadorplaybook.netlify.app](https://modooperadorplaybook.netlify.app)*
