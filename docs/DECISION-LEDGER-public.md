# Decision Ledger — Público

Decisões rastreáveis do build do Modo Operador.
Cada entrada tem contexto, alternativa considerada e data.

> Decisões privadas (infraestrutura, pricing interno, estratégia de distribuição) ficam no Benni Control Plane.

---

## Decisões travadas

### [2026-07-24] Nome do produto
- **Decisão:** Modo Operador
- **Alternativas:** "O Operador de IA", "Stack do Operador", "Sistema Operador"
- **Motivo:** Mais direto, posiciona o método (modo de operar) não o perfil

### [2026-07-24] Formato do produto
- **Decisão:** Playbook digital (HTML entregue via Cakto)
- **Alternativas:** PDF, curso em vídeo, Notion
- **Motivo:** HTML permite interatividade, não depende de plataforma de curso, entrega imediata

### [2026-07-24] Plataforma de venda
- **Decisão:** Cakto
- **Alternativas:** Hotmart, Kiwify, Gumroad
- **Motivo:** Menor fricção para setup inicial, Pix nativo, checkout limpo

### [2026-07-25] Preço de lançamento
- **Decisão:** R$97 — Early Access
- **Alternativas:** R$47, R$147, R$197
- **Motivo:** Low-ticket com percepção de valor técnico; acesso vitalício justifica acima de R$47

### [2026-07-26] Hosting da landing
- **Decisão:** GitHub Pages (`nsfwbunny.github.io/modo-operador`)
- **Alternativas:** Netlify, Vercel, self-hosted
- **Motivo:** Zero custo, integrado ao repo público, reforça credibilidade técnica

### [2026-07-26] Separação landing / produto
- **Decisão:** Landing no GitHub Pages (público), produto no Netlify (acesso controlado via Cakto)
- **Motivo:** Produto protegido, landing auditável e gratuita

### [2026-07-27] Stack do acervo público
- **Decisão:** README + STACK.md + prompts/ + proofs/ + docs/ como acervo livre
- **Motivo:** Acervo público entrega método e prova; produto entrega execução completa. Visitante aprende antes de comprar.

### [2026-08-06] Atualização de preço e checkout
- **Decisão:** R$147 — Checkout Cakto oficial (`https://pay.cakto.com.br/pfuibmt_999515`)
- **Alternativas:** R$97, R$197
- **Motivo:** Ajuste de posicionamento de valor com inclusão de áudios MP3 nativos para todos os 7 capítulos.

### [2026-08-06] Integração de Players de Áudio na Landing Page
- **Decisão:** Embed nativo HTML5 com custom styling para `audio/cap01.mp3` a `audio/cap07.mp3`
- **Motivo:** Permitir degustação/execução direta da narração de cada capítulo na landing page, aumentando engajamento e percepção de valor.
