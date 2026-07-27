<div align="center">

# Modo Operador

**O sistema para usar IA como camada de execução.**

*Não é curso. Não é teoria. É o sistema documentado.*

[![Status](https://img.shields.io/badge/status-em%20constru%C3%A7%C3%A3o-yellow)]()
[![Stack](https://img.shields.io/badge/stack-Jules%20%7C%20MCP%20%7C%20Antigravity-blue)]()
[![Proof](https://img.shields.io/badge/proof-engenharia%20real-brightgreen)]()
[![License](https://img.shields.io/badge/license-MIT-lightgrey)]()

</div>

---

## O problema real

As ferramentas de IA avançaram radicalmente em 12 meses.\
O que a maioria está ensinando não acompanhou.

```text
Ciclo de 2024:  prompt → resposta → copiar
Ciclo de 2026:  intenção → agente → sistema → entrega
```

Quem só usa prompt como ferramenta está competindo com todo mundo.\
Quem opera IA como sistema está jogando em outra liga.

> **Vantagem real de execução:** build mais rápido, distribuição mais eficiente, receita com menos trabalho manual.

---

## O que é o Modo Operador

Um **playbook de operação** construído por quem usa Jules, MCP e Antigravity no dia a dia para criar ativos digitais, automações e produtos reais.

Não tem lição gravada. Não tem slide. Tem sistema documentado.

**Resultado que o leitor sai com:**

- Sai do ciclo prompt → resposta — para sempre
- Monta o primeiro fluxo com agente real rodando
- Cria um ativo digital com stack de IA do zero
- Opera Jules, MCP e automações sem precisar ser dev profissional

---

## A stack que este playbook documenta

| Ferramenta | Papel no sistema |
|------------|------------------|
| **Jules** | Agente assíncrono — gera PRs, testa, entrega código revisado |
| **Antigravity** | Runtime local — webhooks, agentes, browser, scheduler, audit |
| **MCP** | Protocolo nativo de conexão de ferramentas |
| **MONOMO** | Workspace de agentes — orquestração cloud + local |
| **Gemini / Perplexity** | Raciocínio, pesquisa e citações em tempo real |

---

## Princípios (não negociáveis)

> Este repositório documenta o que já existe.\
> Nada é afirmado antes de ser executado e provado.

- A landing só afirma o que já existe
- O playbook só descreve o que foi executado de verdade
- Cases sem evidência real ficam marcados como `PENDENTE`
- A oferta só abre depois da prova estar pública

---

## Estado atual

| Componente | Status |
|---|:---:|
| Repositório + documentação base | ✅ Completo |
| Playbook — skeleton dos capítulos | ✅ Criado |
| Cases de prova — scaffold | ✅ Criado |
| [Antigravity](https://github.com/nsfwbunny/antigravity) — proof público v5 | ✅ 38 testes passando |
| [MONOMO](https://github.com/nsfwbunny/monomo) — agent workspace | 🔄 Em build |
| Landing page | 🔄 Em construção |
| Oferta final | ⏳ Abre após prova pública |

---

## Proofs — engenharia como evidência

Este repositório é ele mesmo uma prova do método.

O **[Antigravity](https://github.com/nsfwbunny/antigravity)** é o primeiro proof público:
- Sistema de operação local-first com FastAPI, SQLite e Ollama
- Webhooks com HMAC, approval gate, audit trail imutável
- 38 testes passando, 5 fases de build documentadas
- Construído com Jules, operado com MCP, integrado com MONOMO

> *Proof é código rodando. Não é slide.*

---

## Estrutura do repositório

```text
modo-operador/
├── docs/           # Visão, roadmap, outline do playbook
├── playbook/       # Capítulos do método — sistema documentado
├── proofs/         # Cases e evidências reais — sem prova, não entra
├── prompts/        # Prompts operacionais prontos para Jules e MCP
└── assets/
    └── landing/    # Landing page HTML
```

---

## Roadmap

- [ ] Playbook completo — todos os capítulos escritos e revisados
- [ ] Cases de prova publicados com evidência real e links
- [ ] Landing page no ar com waitlist
- [ ] Oferta aberta

Ver [`docs/roadmap.md`](./docs/roadmap.md) para detalhes.

---

## Ecossistema

| Repositório | Papel |
|------------|-------|
| [modo-operador](https://github.com/nsfwbunny/modo-operador) | Este repo — o playbook e o método |
| [antigravity](https://github.com/nsfwbunny/antigravity) | Runtime local do operador — proof v5 |
| [monomo](https://github.com/nsfwbunny/monomo) | Agent workspace premium — em build |
| [benni-master-os-skills](https://github.com/nsfwbunny/benni-master-os-skills) | Skills operacionais para YouTube e conteúdo |

---

<div align="center">

**Operar é diferente de usar.**

</div>
