# Emoji → Lucide Icons Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Replace all 30 emoji icon nodes in index.html and de.html with Lucide SVG icons, keeping the visual style consistent with the brand blue palette.

**Architecture:** Single CDN script tag loads Lucide at runtime; `lucide.createIcons()` converts every `<i data-lucide="name">` to a proper inline SVG. CSS sizing rules are added as a dedicated block in styles.css. Both HTML files change in one commit (CLAUDE.md golden rule).

**Tech Stack:** [Lucide Icons](https://lucide.dev) via unpkg CDN — no build step, no local assets.

---

## File Map

| File | Change |
|---|---|
| `styles.css` | Add `/* ── LUCIDE ICON SIZING ── */` block after line 358 |
| `index.html` | Add CDN `<script>` in `<head>`, replace 30 emoji nodes, add init call before `</body>` |
| `de.html` | Identical structural changes (different text, same HTML structure) |

---

## Task 1: CSS — Add SVG sizing rules

**Files:**
- Modify: `styles.css` (after line 358, before `/* ── USE CASES ── */`)

- [ ] **Step 1: Add the Lucide sizing block**

Insert the following block into `styles.css` between `.output-card p { ... }` (line 358) and `/* ── USE CASES ── */` (line 360):

```css
/* ── LUCIDE ICON SIZING ── */
.mode-emoji svg { width: 28px; height: 28px; stroke: var(--blue); }
.jc-icon svg    { width: 22px; height: 22px; stroke: var(--blue); }
.ji-icon svg    { width: 24px; height: 24px; stroke: #ffffff; }
.pain-icon svg  { width: 22px; height: 22px; stroke: var(--blue); }
.step-icon svg  { width: 28px; height: 28px; stroke: var(--blue); }
.feat-icon-box svg           { width: 20px; height: 20px; stroke: var(--blue); }
.output-card .oc-icon svg    { width: 26px; height: 26px; stroke: var(--blue); }
```

Note: `.ji-icon` lives inside `.journey-integration` which has `background: var(--ink)` (dark), so its SVG strokes white, not blue.

- [ ] **Step 2: Commit styles.css**

```bash
git add styles.css
git commit -m "Icons: add Lucide SVG sizing rules to icon containers"
```

---

## Task 2: Update index.html

**Files:**
- Modify: `index.html`

### Step 1 — Add Lucide CDN script to `<head>`

- [ ] **Add after line 10** (after the flash-prevention script, before `</head>`):

```html
  <script src="https://unpkg.com/lucide@latest/dist/umd/lucide.min.js"></script>
```

### Step 2 — Replace emoji nodes (Modes section, lines 71 + 79)

- [ ] Line 71 — Basic mode:
```html
<!-- before -->
      <div class="mode-emoji">⚡</div>
<!-- after -->
      <div class="mode-emoji"><i data-lucide="zap"></i></div>
```

- [ ] Line 79 — Pro mode:
```html
<!-- before -->
      <div class="mode-emoji">🏗️</div>
<!-- after -->
      <div class="mode-emoji"><i data-lucide="sliders-horizontal"></i></div>
```

### Step 3 — Replace emoji nodes (Journey chapters, lines 101–136)

- [ ] Line 101 — Strategic Asset Allocation:
```html
<!-- before -->
        <span class="jc-icon">📊</span>
<!-- after -->
        <span class="jc-icon"><i data-lucide="bar-chart-2"></i></span>
```

- [ ] Line 108 — Why ETFs:
```html
<!-- before -->
        <span class="jc-icon">🗂️</span>
<!-- after -->
        <span class="jc-icon"><i data-lucide="layers"></i></span>
```

- [ ] Line 115 — The Stock-Picking Trap:
```html
<!-- before -->
        <span class="jc-icon">🎯</span>
<!-- after -->
        <span class="jc-icon"><i data-lucide="target"></i></span>
```

- [ ] Line 122 — Market Timing:
```html
<!-- before -->
        <span class="jc-icon">📉</span>
<!-- after -->
        <span class="jc-icon"><i data-lucide="trending-down"></i></span>
```

- [ ] Line 129 — Power of Compounding:
```html
<!-- before -->
        <span class="jc-icon">📈</span>
<!-- after -->
        <span class="jc-icon"><i data-lucide="trending-up"></i></span>
```

- [ ] Line 136 — Your Investor Profile:
```html
<!-- before -->
        <span class="jc-icon">🧠</span>
<!-- after -->
        <span class="jc-icon"><i data-lucide="brain"></i></span>
```

### Step 4 — Replace emoji node (Journey integration box, line 144)

- [ ] Line 144 — Integration callout (dark background — white stroke applied via CSS):
```html
<!-- before -->
      <div class="ji-icon">⚡</div>
<!-- after -->
      <div class="ji-icon"><i data-lucide="zap"></i></div>
```

### Step 5 — Replace emoji nodes (Pain points, lines 173–187)

- [ ] Line 173 — Takes too long:
```html
<!-- before -->
            <div class="pain-icon">⏱</div>
<!-- after -->
            <div class="pain-icon"><i data-lucide="timer"></i></div>
```

- [ ] Line 180 — Inconsistent results:
```html
<!-- before -->
            <div class="pain-icon">🔁</div>
<!-- after -->
            <div class="pain-icon"><i data-lucide="refresh-cw"></i></div>
```

- [ ] Line 187 — Missing domain logic:
```html
<!-- before -->
            <div class="pain-icon">🧩</div>
<!-- after -->
            <div class="pain-icon"><i data-lucide="puzzle"></i></div>
```

### Step 6 — Replace emoji nodes (Steps, lines 230–255)

- [ ] Line 230 — Step 01:
```html
<!-- before -->
        <span class="step-icon">🚀</span>
<!-- after -->
        <span class="step-icon"><i data-lucide="zap"></i></span>
```

- [ ] Line 243 — Step 02:
```html
<!-- before -->
        <span class="step-icon">🧠</span>
<!-- after -->
        <span class="step-icon"><i data-lucide="brain"></i></span>
```

- [ ] Line 255 — Step 03:
```html
<!-- before -->
        <span class="step-icon">📋</span>
<!-- after -->
        <span class="step-icon"><i data-lucide="clipboard-check"></i></span>
```

### Step 7 — Replace emoji nodes (Features, lines 317–366)

- [ ] Line 317 — Home Bias Logic:
```html
<!-- before -->
        <div class="feat-icon-box">🏠</div>
<!-- after -->
        <div class="feat-icon-box"><i data-lucide="home"></i></div>
```

- [ ] Line 324 — Currency Hedging:
```html
<!-- before -->
        <div class="feat-icon-box">💱</div>
<!-- after -->
        <div class="feat-icon-box"><i data-lucide="arrow-left-right"></i></div>
```

- [ ] Line 331 — Asset Classes:
```html
<!-- before -->
        <div class="feat-icon-box">🗂️</div>
<!-- after -->
        <div class="feat-icon-box"><i data-lucide="layers"></i></div>
```

- [ ] Line 338 — Synthetic ETF Evaluation:
```html
<!-- before -->
        <div class="feat-icon-box">⚠️</div>
<!-- after -->
        <div class="feat-icon-box"><i data-lucide="alert-triangle"></i></div>
```

- [ ] Line 345 — Plausibility Validation:
```html
<!-- before -->
        <div class="feat-icon-box">✅</div>
<!-- after -->
        <div class="feat-icon-box"><i data-lucide="shield-check"></i></div>
```

- [ ] Line 352 — Bilingual Output:
```html
<!-- before -->
        <div class="feat-icon-box">🌐</div>
<!-- after -->
        <div class="feat-icon-box"><i data-lucide="globe"></i></div>
```

- [ ] Line 359 — ETF Look-Through Analysis:
```html
<!-- before -->
        <div class="feat-icon-box">🔬</div>
<!-- after -->
        <div class="feat-icon-box"><i data-lucide="microscope"></i></div>
```

- [ ] Line 366 — TER Estimation:
```html
<!-- before -->
        <div class="feat-icon-box">🏷️</div>
<!-- after -->
        <div class="feat-icon-box"><i data-lucide="tag"></i></div>
```

### Step 8 — Replace emoji nodes (Output modules, lines 384–409)

- [ ] Line 384 — Target Allocation:
```html
<!-- before -->
        <div class="oc-icon">🎯</div>
<!-- after -->
        <div class="oc-icon"><i data-lucide="target"></i></div>
```

- [ ] Line 389 — ETF Implementation:
```html
<!-- before -->
        <div class="oc-icon">📈</div>
<!-- after -->
        <div class="oc-icon"><i data-lucide="trending-up"></i></div>
```

- [ ] Line 394 — Currency Overview:
```html
<!-- before -->
        <div class="oc-icon">💵</div>
<!-- after -->
        <div class="oc-icon"><i data-lucide="banknote"></i></div>
```

- [ ] Line 399 — Rebalancing Guidance:
```html
<!-- before -->
        <div class="oc-icon">🔄</div>
<!-- after -->
        <div class="oc-icon"><i data-lucide="rotate-cw"></i></div>
```

- [ ] Line 404 — TER Estimation:
```html
<!-- before -->
        <div class="oc-icon">💰</div>
<!-- after -->
        <div class="oc-icon"><i data-lucide="coins"></i></div>
```

- [ ] Line 409 — ETF Look-Through:
```html
<!-- before -->
        <div class="oc-icon">🔬</div>
<!-- after -->
        <div class="oc-icon"><i data-lucide="microscope"></i></div>
```

### Step 9 — Replace emoji node (Customisation section, line 423)

- [ ] Line 423 — Customise strategies:
```html
<!-- before -->
      <div class="feat-icon-box">🛠️</div>
<!-- after -->
      <div class="feat-icon-box"><i data-lucide="wrench"></i></div>
```

### Step 10 — Add Lucide init call before `</body>`

- [ ] Add immediately before `</body>` (line 497):
```html
<script>lucide.createIcons();</script>
```

### Step 11 — Verify index.html in preview

- [ ] Open `http://localhost:8000/` (or use `preview_start` for `ppb-landing-page`)
- [ ] Scroll through the full page — every icon slot should show a blue Lucide SVG
- [ ] Check `.ji-icon` in the Journey integration band (dark background) — icon should be **white**
- [ ] Confirm no emoji fallbacks (blank squares, coloured glyphs)
- [ ] Resize viewport to 600 px width — icons should scale with containers

---

## Task 3: Update de.html

**Files:**
- Modify: `de.html`

Apply the identical structural changes. Content (text) is German but the HTML structure mirrors index.html exactly. Line numbers differ slightly but the emoji characters and container classes are identical.

- [ ] **Add Lucide CDN script to `<head>`** — same as index.html Step 1:
```html
  <script src="https://unpkg.com/lucide@latest/dist/umd/lucide.min.js"></script>
```
(insert after line 10, before `</head>`)

- [ ] **Replace all 30 emoji nodes** using this reference table (same replacements as index.html — find by emoji character, replace with `<i data-lucide="…"></i>`):

| Line (de.html) | Emoji | Lucide name |
|---|---|---|
| 62 | ⚡ | `zap` |
| 70 | 🏗️ | `sliders-horizontal` |
| 92 | 📊 | `bar-chart-2` |
| 99 | 🗂️ | `layers` |
| 106 | 🎯 | `target` |
| 113 | 📉 | `trending-down` |
| 120 | 📈 | `trending-up` |
| 127 | 🧠 | `brain` |
| 135 | ⚡ | `zap` |
| 163 | ⏱ | `timer` |
| 170 | 🔁 | `refresh-cw` |
| 177 | 🧩 | `puzzle` |
| 207 | 🚀 | `zap` |
| 215 | 🧠 | `brain` |
| 223 | 📋 | `clipboard-check` |
| 280 | 🏠 | `home` |
| 287 | 💱 | `arrow-left-right` |
| 294 | 🗂️ | `layers` |
| 301 | ⚠️ | `alert-triangle` |
| 308 | ✅ | `shield-check` |
| 315 | 🌐 | `globe` |
| 322 | 🔬 | `microscope` |
| 329 | 🏷️ | `tag` |
| 345 | 🎯 | `target` |
| 346 | 📈 | `trending-up` |
| 347 | 💵 | `banknote` |
| 348 | 🔄 | `rotate-cw` |
| 349 | 💰 | `coins` |
| 350 | 🔬 | `microscope` |
| 361 | 🛠️ | `wrench` |

- [ ] **Add Lucide init call before `</body>`**:
```html
<script>lucide.createIcons();</script>
```

- [ ] **Verify de.html in preview** — open `http://localhost:8000/de.html`, confirm all 30 icons render identically to the EN version.

---

## Task 4: Commit both HTML files

CLAUDE.md golden rule: EN + DE in the same commit.

- [ ] **Stage and commit**:
```bash
git add index.html de.html
git commit -m "Icons: replace emoji with Lucide SVG icons (EN + DE)"
```

---

## Post-Implementation

- [ ] Upload `index.html`, `de.html`, `styles.css` to `/httpdocs/prompt-builder/landingpage/` on the bicon.li server
- [ ] Verify live at `https://bicon.li/portfolio-prompt-builder/` (WordPress iframe embed)
- [ ] Verify German version at `https://bicon.li/portfolio-prompt-builder/` with path not containing `/en/`
