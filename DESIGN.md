# DESIGN.md — Design System | Data Engineering Portfolio Landing Page

---

## Direção Estética: "Terminal Noir meets Data Flow"

Uma fusão entre a brutalidade elegante de interfaces de terminal e a fluidez visual de pipelines de dados. O visual transmite **competência técnica profunda** sem parecer genérico ou "AI-generated". Pensa num cruzamento entre a sofisticação dark do Linear/Vercel e a crueza visual de um terminal Gruvbox customizado — com toques de data visualization como elemento decorativo.

**Palavras-chave do mood:** *cinematic dark, precision engineering, controlled chaos, data in motion, monospace elegance*

---

## Paleta de Cores

### Cores Base (Dark Theme)

```css
:root {
  /* Background layers — do mais profundo ao mais superficial */
  --bg-void:        #0A0A0F;     /* fundo absoluto, quase preto com hint azulado */
  --bg-deep:        #0F1117;     /* background principal das seções */
  --bg-surface:     #161922;     /* cards, containers elevados */
  --bg-elevated:    #1C2030;     /* hover states, elementos destacados */

  /* Texto — hierarquia clara */
  --text-primary:   #E8ECF4;     /* títulos, texto principal — off-white frio */
  --text-secondary: #8B92A8;     /* descrições, labels — cinza médio azulado */
  --text-muted:     #4A5068;     /* timestamps, metadados — cinza escuro */
  --text-ghost:     #2A3048;     /* linhas decorativas, watermarks */

  /* Accent — Pipeline Green (cor principal de destaque) */
  --accent-primary:    #00E59B;  /* verde vibrante — CTAs, links ativos, highlights */
  --accent-glow:       #00E59B33; /* versão com alpha para glows e shadows */
  --accent-subtle:     #00E59B15; /* backgrounds sutis de accent */
  --accent-hover:      #00FFAD;  /* hover intensificado */

  /* Accent Secundário — Data Blue */
  --accent-secondary:  #3B82F6;  /* azul para tags, badges, elementos secundários */
  --accent-secondary-glow: #3B82F633;

  /* Accent Terciário — Warning/Streaming Amber */
  --accent-warm:       #F59E0B;  /* para badges de "streaming", indicadores live */
  --accent-warm-glow:  #F59E0B33;

  /* Semânticas */
  --border-default:    #1E2235;  /* bordas sutis */
  --border-hover:      #2A3050;  /* bordas em hover */
  --border-accent:     #00E59B44; /* bordas com accent */

  /* Gradientes especiais */
  --gradient-hero:     linear-gradient(135deg, #0A0A0F 0%, #0F1520 50%, #0A1A15 100%);
  --gradient-card:     linear-gradient(180deg, #161922 0%, #121520 100%);
  --gradient-accent:   linear-gradient(90deg, #00E59B, #3B82F6);
  --gradient-text:     linear-gradient(90deg, #00E59B 0%, #3B82F6 50%, #00E59B 100%);
}
```

### Uso das Cores por Contexto

| Elemento | Cor | Variável |
|---|---|---|
| Background da página | Void/Deep | `--bg-void`, `--bg-deep` |
| Cards de projeto | Surface + borda sutil | `--bg-surface`, `--border-default` |
| Títulos H1/H2 | Primary text | `--text-primary` |
| Corpo de texto | Secondary text | `--text-secondary` |
| Links e CTAs | Pipeline Green | `--accent-primary` |
| Tags de tecnologia | Background accent sutil + texto | `--accent-subtle` + `--accent-primary` |
| Badges "Streaming" | Warm amber | `--accent-warm` |
| Badges "Batch" | Data Blue | `--accent-secondary` |
| Hover em cards | Borda accent + glow | `--border-accent` + `--accent-glow` |
| Linha da timeline | Gradient accent | `--gradient-accent` |

---

## Tipografia

### Font Stack

```css
/* Display / Headings — personalidade forte, geométrica */
@import url('https://fonts.googleapis.com/css2?family=Space+Mono:wght@400;700&family=Outfit:wght@300;400;500;600;700;800&family=JetBrains+Mono:wght@400;500;600&display=swap');

:root {
  /* Heading — moderna, geométrica, limpa */
  --font-display:    'Outfit', sans-serif;

  /* Body — legível, técnica mas amigável */
  --font-body:       'Outfit', sans-serif;

  /* Code / Monospace — identidade de engenheiro */
  --font-mono:       'JetBrains Mono', 'Space Mono', monospace;

  /* Accent monospace — para detalhes especiais */
  --font-accent:     'Space Mono', monospace;
}
```

### Escala Tipográfica (fluid, clamp-based)

```css
:root {
  /* Display — hero title */
  --text-display:    clamp(2.5rem, 5vw + 1rem, 5rem);
  --leading-display: 1.0;
  --tracking-display: -0.03em;

  /* H1 — section titles */
  --text-h1:         clamp(2rem, 3vw + 0.5rem, 3.5rem);
  --leading-h1:      1.1;
  --tracking-h1:     -0.02em;

  /* H2 — subsection titles */
  --text-h2:         clamp(1.25rem, 2vw + 0.25rem, 1.75rem);
  --leading-h2:      1.2;
  --tracking-h2:     -0.01em;

  /* H3 — card titles */
  --text-h3:         clamp(1rem, 1.5vw + 0.25rem, 1.25rem);
  --leading-h3:      1.3;

  /* Body */
  --text-body:       clamp(0.95rem, 1vw + 0.1rem, 1.1rem);
  --leading-body:    1.65;

  /* Small — labels, tags, metadata */
  --text-small:      clamp(0.75rem, 0.8vw + 0.1rem, 0.85rem);
  --leading-small:   1.4;
  --tracking-small:  0.04em;

  /* Mono body — code snippets inline */
  --text-mono:       0.875rem;
  --leading-mono:    1.5;
}
```

### Regras Tipográficas

- **Hero title**: `--font-display` weight 700-800, `--tracking-display` negativo para compactar
- **Section headers**: `--font-display` weight 600, caixa alta **NÃO** (fica genérico) — usar mixed case
- **Section labels** (acima dos títulos): `--font-mono` weight 400, `--text-small`, `--tracking-small`, `--accent-primary`, caixa alta — ex: `// PROJETOS`, `01 — SOBRE`
- **Body text**: `--font-body` weight 300-400, `--text-secondary`
- **Tags/Badges**: `--font-mono`, `--text-small`, letter-spacing 0.05em
- **Números e métricas**: `--font-mono` weight 600, sempre tabular-nums
- **Links**: sem underline default, `--accent-primary`, underline offset animado no hover

---

## Layout & Espacamento

### Grid System

```css
:root {
  /* Container máximo */
  --container-max:     1200px;
  --container-padding: clamp(1.5rem, 4vw, 4rem);

  /* Grid */
  --grid-columns:      12;
  --grid-gap:          clamp(1rem, 2vw, 2rem);

  /* Spacing scale (8px base) */
  --space-xs:    0.25rem;   /*  4px */
  --space-sm:    0.5rem;    /*  8px */
  --space-md:    1rem;      /* 16px */
  --space-lg:    1.5rem;    /* 24px */
  --space-xl:    2rem;      /* 32px */
  --space-2xl:   3rem;      /* 48px */
  --space-3xl:   4rem;      /* 64px */
  --space-4xl:   6rem;      /* 96px */
  --space-hero:  8rem;      /* 128px — entre hero e próxima seção */

  /* Section spacing */
  --section-gap: clamp(5rem, 10vw, 10rem);
}
```

### Layout Rules

1. **Hero**: full viewport height (`100dvh`), conteúdo centralizado verticalmente com leve offset para cima (40/60)
2. **Seções**: espaçamento generoso entre seções (`--section-gap`), padding interno com `--container-padding`
3. **Cards de projeto**: grid de 2 colunas em desktop (gap `--grid-gap`), stack em mobile
4. **Stack section**: flex wrap com gap, ícones/badges em clusters lógicos
5. **Timeline**: layout assimétrico — linha vertical à esquerda, conteúdo à direita (desktop); centralizado (mobile)
6. **Seção de contato**: centralizada, máximo 600px de largura

### Breakpoints

```css
/* Mobile first */
--bp-sm:   640px;    /* mobile landscape */
--bp-md:   768px;    /* tablet */
--bp-lg:   1024px;   /* desktop pequeno */
--bp-xl:   1280px;   /* desktop */
--bp-2xl:  1536px;   /* wide */
```

---

## Componentes Visuais

### 1. Cards de Projeto

```
┌─────────────────────────────────────────┐
│  ┌─ type badge ──────┐                  │
│  │ ● STREAMING       │                  │
│  └───────────────────┘                  │
│                                         │
│  Título do Projeto                      │
│  Descrição curta em duas linhas que     │
│  explica o que o projeto faz.           │
│                                         │
│  ┌─────┐ ┌───────┐ ┌──────┐ ┌────┐    │
│  │Spark│ │Delta  │ │Kafka │ │Azure│    │
│  └─────┘ └───────┘ └──────┘ └────┘    │
│                                         │
│  GitHub ↗    Case Study ↗        →     │
└─────────────────────────────────────────┘
```

**Estilo:**
- Background: `--bg-surface` com `--gradient-card`
- Border: 1px `--border-default`, muda para `--border-accent` no hover
- Border-radius: 12px
- Box-shadow no hover: `0 0 30px var(--accent-glow)`
- Transição suave (300ms ease-out) no hover: leve translate-y(-4px)
- Type badge (canto superior): dot colorido + texto mono uppercase
  - Streaming: `--accent-warm` (amber dot)
  - Batch: `--accent-secondary` (blue dot)
  - Lakehouse: `--accent-primary` (green dot)
  - BI/Analytics: `#A78BFA` (roxo suave)

### 2. Tech Tags / Badges

```css
.tech-tag {
  font-family: var(--font-mono);
  font-size: var(--text-small);
  padding: var(--space-xs) var(--space-sm);
  border-radius: 6px;
  background: var(--accent-subtle);
  color: var(--accent-primary);
  border: 1px solid var(--border-default);
  letter-spacing: 0.03em;
  transition: all 200ms ease;
}

.tech-tag:hover {
  background: var(--accent-glow);
  border-color: var(--accent-primary);
}
```

### 3. Section Label (acima dos títulos)

```css
.section-label {
  font-family: var(--font-mono);
  font-size: var(--text-small);
  font-weight: 400;
  color: var(--accent-primary);
  letter-spacing: var(--tracking-small);
  text-transform: uppercase;
  margin-bottom: var(--space-md);
}
/* Exemplo de uso: "// 03 — PROJETOS" */
```

### 4. CTA Buttons

**Primário:**
```css
.btn-primary {
  font-family: var(--font-mono);
  font-size: var(--text-small);
  font-weight: 600;
  padding: var(--space-md) var(--space-xl);
  background: var(--accent-primary);
  color: var(--bg-void);
  border: none;
  border-radius: 8px;
  letter-spacing: 0.04em;
  text-transform: uppercase;
  cursor: pointer;
  transition: all 250ms ease;
  position: relative;
  overflow: hidden;
}

.btn-primary:hover {
  box-shadow: 0 0 25px var(--accent-glow), 0 0 50px var(--accent-glow);
  transform: translateY(-1px);
}
```

**Secundário (outline / ghost):**
```css
.btn-secondary {
  /* mesma tipografia do primário */
  background: transparent;
  color: var(--text-primary);
  border: 1px solid var(--border-hover);
  border-radius: 8px;
}

.btn-secondary:hover {
  border-color: var(--accent-primary);
  color: var(--accent-primary);
}
```

### 5. Timeline Item

```
        ●──── Data Engineer @ CNH Industrial          Ago 2025 — Presente
        │     Pipelines PySpark, Medallion Architecture,
        │     Delta Lake, Power BI dashboards
        │
        ●──── Data Science Intern @ CNH               Nov 2024 — Ago 2025
        │     PFMEA NLP automation, QlikView → Power BI
        │     migration, first data pipelines
        │
        ●──── B.Sc. Data Science — FAE                 2024 — 2028
              Estatística, ML, Engenharia de Dados
```

- Linha vertical: 2px, `--gradient-accent`
- Dots: 12px, filled com `--accent-primary`, com glow ring animado no item ativo
- Texto de cargo: `--font-display` weight 600, `--text-primary`
- Texto de descrição: `--font-body` weight 300, `--text-secondary`
- Datas: `--font-mono`, `--text-muted`, alinhado à direita (desktop)

---

## Animações & Motion

### Filosofia

Animações servem para **guiar o olho** e **criar sensação de fluidez**, não para impressionar. O paradigma é: *dados em movimento* — tudo deve lembrar sutilmente um pipeline processando, dados fluindo.

### Animações Core

```css
/* 1. Fade-in staggered — entrada de seções */
@keyframes fadeInUp {
  from {
    opacity: 0;
    transform: translateY(24px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.reveal {
  animation: fadeInUp 0.7s cubic-bezier(0.16, 1, 0.3, 1) both;
}

/* Stagger delays para children */
.reveal:nth-child(1) { animation-delay: 0.0s; }
.reveal:nth-child(2) { animation-delay: 0.1s; }
.reveal:nth-child(3) { animation-delay: 0.2s; }
.reveal:nth-child(4) { animation-delay: 0.3s; }

/* 2. Glow pulse — dot ativo na timeline */
@keyframes glowPulse {
  0%, 100% { box-shadow: 0 0 8px var(--accent-glow); }
  50% { box-shadow: 0 0 20px var(--accent-glow), 0 0 40px var(--accent-glow); }
}

/* 3. Gradient text shimmer — hero title accent */
@keyframes gradientShift {
  0% { background-position: 0% 50%; }
  100% { background-position: 200% 50%; }
}

.gradient-text {
  background: var(--gradient-text);
  background-size: 200% auto;
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  animation: gradientShift 4s linear infinite;
}

/* 4. Cursor blink — hero, terminal aesthetic */
@keyframes cursorBlink {
  0%, 50% { opacity: 1; }
  51%, 100% { opacity: 0; }
}

.cursor {
  display: inline-block;
  width: 2px;
  height: 1.1em;
  background: var(--accent-primary);
  margin-left: 4px;
  animation: cursorBlink 1s step-end infinite;
}

/* 5. Scroll-triggered reveal via IntersectionObserver */
.scroll-reveal {
  opacity: 0;
  transform: translateY(24px);
  transition: opacity 0.6s ease, transform 0.6s cubic-bezier(0.16, 1, 0.3, 1);
}

.scroll-reveal.visible {
  opacity: 1;
  transform: translateY(0);
}
```

### Motion Guidelines

| Contexto | Duração | Easing | Notas |
|---|---|---|---|
| Hover (cards, links) | 200-300ms | `ease` | Rápido, responsivo |
| Entrada de seções | 600-800ms | `cubic-bezier(0.16, 1, 0.3, 1)` | Stagger 100ms entre items |
| Hero load | 800-1200ms | `cubic-bezier(0.16, 1, 0.3, 1)` | Stagger: label → title → subtitle → CTA |
| Glow effects | 2-4s | `ease-in-out` | Loop infinito, sutil |
| Gradient shift | 3-5s | `linear` | Loop infinito no text gradient |

---

## Elementos Decorativos & Atmosfera

### Background

- **Hero**: gradient radial sutil do centro, com orbs difusos de `--accent-primary` (opacity 0.05-0.08) e `--accent-secondary` (opacity 0.03-0.05)
- **Seções**: alternância sutil entre `--bg-void` e `--bg-deep`
- **Noise overlay**: grain texture sutil (via SVG filter ou CSS `url()`) com opacity 0.03-0.05 para dar textura orgânica ao dark theme

### Grid Decorativo

- Grid de pontos (dot grid) como background decorativo em seções alternadas, opacity 0.04
- Linhas horizontais sutis separando seções (1px, `--border-default`)

### Elementos de "Data Flow"

- Linhas conectoras animadas (SVG paths) entre cards de projeto — representando dependência/fluxo
- Partículas de dados fluindo na hero section (opcional, se performance permitir)
- ASCII art sutil como watermark decorativo: `{ }`, `=>`, `|>`, `Δ` (delta icon)

### Glow Effects

- Accent glow sutil atrás do hero title
- Card hover com box-shadow glow
- CTA button com glow ring no hover
- Timeline dot ativo com glow pulse

---

## Iconografia

### Abordagem

Sem ícones pesados de libraries genéricas. Usar:

1. **SVG custom mínimos** para categorias (4-5 ícones únicos)
2. **Logos oficiais** das tecnologias (Spark, Databricks, Azure, etc.) — SVG monocromáticos em `--text-muted`, coloridos em hover
3. **Caracteres mono** como ícones: `→`, `↗`, `●`, `◆`, `//`, `|>`, `$_`
4. **Lucide React** (se React) para ícones utilitários (GitHub, LinkedIn, Mail, ExternalLink)

---

## Responsividade

### Mobile Adaptations

- Hero: título menor, CTA empilhado verticalmente
- Cards de projeto: single column, full width
- Stack/Tech: tags em wrap, menor padding
- Timeline: centralizada, linha à esquerda com offset reduzido
- Navigation: hamburger menu com slide-in panel (bg: `--bg-surface`)
- Seção de contato: full width, padding ajustado

### Hover → Touch Adaptations

- Hover glows desativados em touch devices (`@media (hover: hover)`)
- Tap feedback com scale transform (0.98) em cards e botões
- Touch targets mínimo 44x44px

---

## Acessibilidade

- Contraste mínimo: WCAG AA (4.5:1 para texto, 3:1 para elementos grandes)
- `--text-primary` sobre `--bg-deep` → ratio ~13:1 ✓
- `--accent-primary` sobre `--bg-void` → ratio ~8.5:1 ✓
- Focus visible: outline 2px `--accent-primary` com offset 4px
- `prefers-reduced-motion`: desativar todas as animações, mostrar conteúdo estático
- `prefers-color-scheme: light`: manter dark como default (identidade), mas considerar toggle futuro
- Semântica: `<main>`, `<nav>`, `<section>`, `<article>`, `aria-label` em seções
- Skip-to-content link escondido visualmente

---

## Arquitetura de Arquivo (se React/JSX)

```
src/
├── components/
│   ├── Hero.jsx
│   ├── About.jsx
│   ├── TechStack.jsx
│   ├── Projects.jsx
│   ├── ProjectCard.jsx
│   ├── Timeline.jsx
│   ├── Contact.jsx
│   ├── Navigation.jsx
│   └── shared/
│       ├── SectionLabel.jsx
│       ├── TechTag.jsx
│       ├── Button.jsx
│       └── GlowOrb.jsx
├── styles/
│   ├── variables.css
│   ├── animations.css
│   ├── typography.css
│   └── global.css
├── data/
│   ├── projects.json
│   ├── timeline.json
│   └── techStack.json
├── App.jsx
└── index.html
```

**Se single-file HTML**: tudo em um arquivo, CSS inline no `<style>`, JS inline no `<script>`, seções bem comentadas com `/* === HERO === */` etc.

---

## Checklist de Qualidade

- [ ] Nenhuma font genérica (Inter, Roboto, Arial)
- [ ] Nenhum gradiente roxo genérico
- [ ] Todas as animações respeitam `prefers-reduced-motion`
- [ ] Contraste WCAG AA em todos os textos
- [ ] Mobile responsivo e touch-friendly
- [ ] Performance: < 3s FCP, sem layout shift
- [ ] Cards de projeto demonstram range técnico (batch, streaming, lakehouse, BI)
- [ ] CTAs acessíveis em qualquer scroll position
- [ ] Aesthetic coeso: "Terminal Noir meets Data Flow" consistente
- [ ] Zero "AI slop" — nada genérico, tudo intencional
