# TruckPlan — Contexto do projeto

## O que é
Planeador de jornada para motoristas de camião profissionais. Single-file HTML/CSS/JS. Trilingue: PT/EN/ES (i18n via T[lang] + atributos data-i no DOM, mais data-i-placeholder).

## Stack & infraestrutura
- HTML/CSS/JS puro, sem build step
- Deploy: Vercel (planeado, ainda não configurado)
- Repo Git inicializado em master
- Sem testes automáticos

## Estado actual (v1 em desenvolvimento)
Lançamento v1 em ~2-3 semanas. Foco: SEO + funcionalidade básica trilingue.

## Plano de ataques (status)

### Tier 1 — Bloqueadores de launch
- [x] Ataque 1: Remover funcionalidade de doação (commit 9f2a887)
- [x] Ataque 2: i18n completa + refactor de pausas (commit anterior)
- [ ] Ataque 3: Integração Formspree para rating + suggestions

### Tier 2 — SEO/infra
- [ ] Ataque 4: Meta tags + OG tags
- [ ] Ataque 5: Schema.org JSON-LD (SoftwareApplication)
- [ ] Ataque 6: hreflang PT/EN/ES
- [ ] Ataque 7: localStorage (lang + darkMode)
- [ ] Ataque 8: robots.txt + sitemap.xml (após domínio)
- [ ] Ataque 9: manifest.json (PWA) + 2 PNGs (192/512 com "TP" em #1A56DB)

### Tier 3 — Pré-launch polish
- [ ] Alinhamento dos valores nos cards de resultado (jornada total, pausas, etc.)
- [ ] Ícones de calendário/relógio invisíveis em dark mode (date/time inputs)
- [ ] Cor do aviso regulamento muito saturada em dark mode
- [ ] Validação de inputs (singleBreak/shortBreak/longBreak/speed)
- [ ] Limpeza: remainDrive triplo, CSS órfão, CSS duplicado

### Pós-launch
- [ ] Comprar domínio .com (recomendado: Porkbun, ~10€/ano)
- [ ] Verificar traduções EN/ES com nativo

### Adiado para v1.5+
- [ ] Stripe: doações com Multibanco/MB Way
- [ ] Mapas e selecção de pontos de partida/chegada
- [ ] Save journeys / diário do motorista (premium)

## Decisões de produto importantes
- v1 lança SEM botão de apoio/doação. Stripe entra em v1.5 quando houver tráfego validado.
- Pausa default: 60min única (margem de segurança ensinada em formação). Toggle "Personalizar" revela campos 15+30 (mínimo legal CE 561/2006).
- Domínio: .com, não .pt — ambição internacional desde início.
- Sem backend em v1. Tudo client-side. Formspree para feedback.
- Validação: lançar, monitorizar 60 dias, decidir features premium com base em métricas reais (não em palpites).

## Convenções de código
- Strings i18n com variáveis usam padrão {x} substitution com .replace(), não concatenação
- data-i para textContent, data-i-placeholder para placeholders de inputs/textareas
- Constantes em UPPERCASE (BLOCK_MAX=270, DAY_MAX=540, DAY_EXT=600)
- Mensagens de commit: feat(v1,scope): descrição — multi-linha com bullets

## Issues conhecidos (não atacar fora da ordem do plano)
- updateDriveCards: triple-assign de remainDrive (linhas ~1006-1013) — dead code
- CSS duplicado: classes Star/Rating definidas duas vezes
- chave card_breaks_title removida em Ataque 2 (era dead code)

## Regulamentação CE 561/2006 (referência rápida)
- Condução contínua: max 4h30 → pausa 45min (pode ser 15+30, nessa ordem)
- Condução diária: 9h normal, 10h max 2x/semana (créditos de extensão)
- Descanso diário: 11h normal, 9h reduzido max 3x/semana
- Compensação de descansos reduzidos: antes do fim da 3.ª semana seguinte

## Postura nesta sessão
Segue o CLAUDE.md global do utilizador (em C:\Users\rui-l\.claude\CLAUDE.md). Sem bajulação. Não concorda por padrão. Resposta directa e curta. Antes de tocar em código, expõe o plano. Um ataque de cada vez, com commit no fim, e pausa para revisão.
