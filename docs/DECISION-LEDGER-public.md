# Decision Ledger — Público

> Registro das decisões relevantes do build do Modo Operador.
> O ledger completo (incluindo infraestrutura privada) é mantido no Benni Control Plane.
> Este arquivo documenta as decisões que afetam o produto e o método publicamente.

---

## Como ler este documento

Cada entrada tem:
- **Decisão** — o que foi decidido, em uma frase
- **Contexto** — por que, com evidência ou raciocínio
- **Data** — quando foi travada
- **Status** — ativa, revisada ou substituída

Decisões travadas não são rediscutidas sem evidência nova. Isso elimina ciclos de debate que não avançam o build.

---

## Decisões de produto

### `PRD-001` — Nome do produto
**Decisão:** O Operador de IA — Modo Operador como nome do sistema e repositório.\
**Contexto:** "Operador" posiciona o comprador como arquiteto de sistemas, não consumidor de ferramenta. Diferencia de cursos genéricos de "IA para iniciantes".\
**Data:** 2026-07-24\
**Status:** ✅ Ativa

---

### `PRD-002` — Formato de entrega
**Decisão:** Playbook HTML com área de membros no Cakto. Sem PDF externo, sem repo público de conteúdo.\
**Contexto:** HTML permite interatividade (reveal, navegação por capítulo, templates copiáveis com highlight). Cakto gerencia checkout, entrega e email automático em uma ferramenta. Simplifica o stack de venda e entrega.\
**Data:** 2026-07-24\
**Status:** ✅ Ativa

---

### `PRD-003` — Preço
**Decisão:** R$97 — preço único, sem upsell inicial.\
**Contexto:** Produto técnico com conteúdo verificável compete com cursos de R$197+. R$97 está abaixo do threshold de fricção para o perfil do comprador (dev ou operador). Upsell pode ser adicionado após validação de conversão.\
**Data:** 2026-07-27\
**Status:** ✅ Ativa

---

### `PRD-004` — Política de conteúdo
**Decisão:** Nenhum capítulo entra no playbook sem ter sido executado e documentado com evidência verificável.\
**Contexto:** O diferencial do produto é ser prova, não teoria. Um claim não verificável destrói a credibilidade de todos os outros. Melhor ter menos capítulos sólidos do que mais capítulos com afirmações não provadas.\
**Data:** 2026-07-24\
**Status:** ✅ Ativa

---

## Decisões de stack

### `STK-001` — Hospedagem da landing
**Decisão:** Netlify para landing page, GitHub Pages para o repo público.\
**Contexto:** Netlify tem deploy contínuo via push, custom domain e CDN sem configuração. GitHub Pages serve o acervo público como portfólio técnico verificável.\
**Data:** 2026-07-27\
**Status:** ✅ Ativa

---

### `STK-002` — LLM local
**Decisão:** Ollama + llama3.1:8b na máquina do operador (RTX 4060, 32GB RAM).\
**Contexto:** Para tarefas de classificação, extração de dados e automações de alta frequência, modelos locais eliminam custo de API. GPT-4o e Claude reservados para raciocínio complexo e geração de código.\
**Data:** 2026-07-25\
**Status:** ✅ Ativa

---

### `STK-003` — Checkout e entrega
**Decisão:** Cakto para checkout e entrega. Link privado de acesso via email pós-compra.\
**Contexto:** Cakto aceita Pix, cartão e boleto. Integra checkout e entrega de produto digital em uma plataforma. Sem necessidade de Stripe, Gumroad ou sistemas externos adicionais para o mercado BR.\
**Data:** 2026-07-24\
**Status:** ✅ Ativa

---

## Decisões de build

### `BLD-001` — Ferramenta de build do playbook
**Decisão:** Jules para geração de código e estrutura. Benni Control Plane para orquestração e rastreamento.\
**Contexto:** Jules cria branches e PRs com descrição de raciocínio — o histórico de commits é ele mesmo uma prova do método. O Control Plane garante continuidade entre sessões sem perder contexto.\
**Data:** 2026-07-24\
**Status:** ✅ Ativa

---

### `BLD-002` — Política de MCP no build
**Decisão:** MCP com escopo mínimo necessário. Tokens read-only para repos de desenvolvimento.\
**Contexto:** MCP com acesso amplo é risco operacional desnecessário. Tokens com escopo específico por repositório e por operação limitam o blast radius de qualquer erro de agente.\
**Data:** 2026-07-25\
**Status:** ✅ Ativa

---

## Decisões substituídas

### `PRD-002-v1` — Entrega via Notion *(substituída por PRD-002)*
**Decisão original:** Link privado de Notion como área de membros.\
**Por que substituída:** Notion não tem controle de acesso por comprador. Um link compartilhado exporia o produto inteiro. Cakto tem gestão de acesso nativa.\
**Data da substituição:** 2026-07-24

---

*Ledger atualizado conforme novas decisões são travadas.*\
*Decisões de infraestrutura privada não aparecem neste documento.*
