# Emoji → Lucide Icons

**Date:** 2026-05-14  
**Scope:** `index.html`, `de.html`, `styles.css`

## Why

Emojis render inconsistently across OS and browser — color, size, and glyph vary. Replacing them with Lucide SVG icons gives consistent, brand-aligned visuals across all platforms.

## Approach

Lucide Icons via CDN. One `<script>` tag, icons declared as `<i data-lucide="name"></i>`, rendered at runtime by `lucide.createIcons()`. No build step, no local assets, no new dependencies beyond a single CDN call.

## Changes

### index.html + de.html (identical change in both)

1. Add to `<head>`:
   ```html
   <script src="https://unpkg.com/lucide@latest/dist/umd/lucide.min.js"></script>
   ```
2. Add before `</body>`:
   ```html
   <script>lucide.createIcons();</script>
   ```
3. Replace every emoji text node with `<i data-lucide="…"></i>` per the mapping below.

### styles.css

Add `svg` sizing inside each icon container class so Lucide's rendered SVGs scale correctly (current rules use `font-size`, which has no effect on SVGs):

| Class | Container size | SVG size | Stroke color |
|---|---|---|---|
| `.mode-emoji` | — | 28 × 28 px | `var(--blue)` |
| `.jc-icon` | — | 22 × 22 px | `var(--blue)` |
| `.pain-icon` | — | 22 × 22 px | `var(--blue)` |
| `.step-icon` | — | 28 × 28 px | `var(--blue)` |
| `.feat-icon-box` | 40 × 40 px (existing) | 20 × 20 px | `var(--blue)` |
| `.oc-icon` | — | 26 × 26 px | `var(--blue)` |

## Icon mapping

| Emoji | Location(s) | Lucide icon |
|---|---|---|
| ⚡ | Basic mode, step 01, integration box | `zap` |
| 🏗️ | Pro mode | `sliders-horizontal` |
| 📊 | Journey ch.1 | `bar-chart-2` |
| 🗂️ | Journey ch.2, feature card | `layers` |
| 🎯 | Journey ch.3, output module | `target` |
| 📉 | Journey ch.4 | `trending-down` |
| 📈 | Journey ch.5, output module | `trending-up` |
| 🧠 | Journey ch.6, step 02 | `brain` |
| ⏱ | Pain point 1 | `timer` |
| 🔁 | Pain point 2 | `refresh-cw` |
| 🧩 | Pain point 3 | `puzzle` |
| 📋 | Step 03 | `clipboard-check` |
| 🏠 | Feature: Home Bias | `home` |
| 💱 | Feature: Currency Hedging | `arrow-left-right` |
| ⚠️ | Feature: Synthetic ETF | `alert-triangle` |
| ✅ | Feature: Validation | `shield-check` |
| 🌐 | Feature: Bilingual Output | `globe` |
| 🔬 | Feature: ETF Look-Through (×2) | `microscope` |
| 🏷️ | Feature: TER Estimation | `tag` |
| 💵 | Output: Currency Overview | `banknote` |
| 🔄 | Output: Rebalancing | `rotate-cw` |
| 💰 | Output: TER Estimation | `coins` |
| 🛠️ | Customisation section | `wrench` |

## Constraints

- `de.html` must mirror every change made to `index.html` (CLAUDE.md golden rule).
- Both files go in the same commit.
- After commit: manually upload `index.html`, `de.html`, `styles.css` to `/httpdocs/prompt-builder/landingpage/` on the server.

## Verification

1. Open local preview (`python -m http.server 8000` from repo root).
2. Confirm all 30 icon slots render a Lucide SVG — no blank squares, no emoji fallbacks.
3. Check `de.html` at `http://localhost:8000/de.html` — identical icon rendering.
4. Resize to mobile (600 px) — icons should scale with their containers.
5. Check the live WordPress embed at `https://bicon.li/portfolio-prompt-builder/` after upload.
