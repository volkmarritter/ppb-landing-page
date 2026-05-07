# ppb-landing-page — project context for Claude Code

Short and operational on purpose.

## What this repo is

A standalone marketing landing page for the **Portfolio Prompt Builder**
(`https://bicon.li/prompt-builder/`). Two single-file HTML deliverables share
one external stylesheet. No build step. Deployed to GitHub Pages.

Live: <https://volkmarritter.github.io/ppb-landing-page/>

## File map

```
index.html                              EN landing page, standalone
de.html                                 DE landing page, kept in lockstep with EN
styles.css                              Shared stylesheet for both HTML files
Screen.png                              Hero screenshot (served from GitHub Pages URL)
Reference Portfolio CHF April2026.html  Example AI-generated output — HTML format
Reference Portfolio EUR April2026.pdf   Example AI-generated output — PDF format
```

## Golden rule

**Every edit to EN (`index.html`) must be mirrored in DE (`de.html`) and vice versa.**
Same sections, same structure. Only the language and locale-specific wording differ.
Keep EN+DE changes in the same commit.

## Page section structure (both files)

```
Nav              Fixed bar — BICon logo + nav links + "Try the Builder" CTA
Hero             h1 + subhead + two CTAs + screenshot
Modes bar        Basic vs Pro mode cards
Journey          "Why Invest" edutainment section — links to why-invest-journey
Problem          3 pain-point items + solution stats box
How it works     3-step flow: Quick Start → Logic fires → Copy & use
Showcase         Reference portfolio example files (EUR PDF + CHF HTML)
Features         8 feature cards (home bias, hedging, asset classes, etc.)
Output modules   6 selectable output section cards
Customisation    Config.js callout + GitHub link
Use cases        3 persona cards: Private investor / Portfolio analyst / FinTech
CTA section      Dark gradient — main conversion block
Disclaimer       MiFID-style legal notice
Footer           Copyright + 4 footer links
```

## Design tokens (styles.css :root)

```
--blue:       #1e73be   primary brand blue
--blue-dark:  #155a99   hover state
--blue-light: #e8f2fb   tint / badge backgrounds
--blue-mid:   #3a90d4   gradient accent
--ink:        #0f1f2e   body text / dark section backgrounds
--muted:      #5a6a7a   secondary / caption text
--border:     #d8e4ef   borders and dividers
--bg:         #f5f8fc   alternate section backgrounds
--white:      #ffffff
--green:      #0f9a6b   success / "prompt ready" accent
--radius:     10px
--shadow:     0 4px 24px rgba(30,115,190,0.10)
--shadow-lg:  0 12px 48px rgba(30,115,190,0.16)

Font: system stack — -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, …
No external font imports (intentional — keeps the page fast and self-contained).
```

## Key external links

| Purpose | URL |
|---|---|
| Builder app | https://bicon.li/prompt-builder/ |
| Config file (allocation-prompt-engine) | https://github.com/volkmarritter/allocation-prompt-engine/blob/main/config.js |
| Why Invest Journey — EN | https://bicon.li/prompt-builder/bicon-why-invest-journey-en.html |
| Why Invest Journey — DE | https://bicon.li/prompt-builder/bicon-why-invest-journey-de.html |
| Reference portfolio EUR (PDF) | https://bicon.li/prompt-builder/Reference-Portfolio-EUR-April2026.pdf |
| Reference portfolio CHF (HTML) | https://bicon.li/prompt-builder/Reference-Portfolio-CHF-April2026.html |

## Dev / preview

No build step. From the repo root:

```bash
python3 -m http.server 8000   # or: npx serve
```

Open `http://localhost:8000/`.

## Commit conventions

- Imperative mood, sentence-case subject, < 72 chars.
- Scope in subject only when useful: `Hero: update subhead copy`.
- Keep EN+DE changes in the same commit when they are a pair.
- One commit per coherent change. No WIP commits on `main`.

## Deployment

Push to `main` triggers GitHub Pages deployment automatically.
Live site: <https://volkmarritter.github.io/ppb-landing-page/>
