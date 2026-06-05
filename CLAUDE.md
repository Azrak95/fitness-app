# CLAUDE.md — AzkFit Project Handover

## What is this project?

AzkFit is a personal fitness PWA (Progressive Web App) built as a single HTML file (`fitness.html`). It is designed for a specific user (Monir, 31 years old, 68.5kg, 171cm) and hosted on GitHub Pages at `azrak95.github.io/AzkNutrition/fitness.html`.

The app is installed on iPhone via Safari → "Add to Home Screen". It works offline. All data is stored in `localStorage`.

## Tech stack

- Single file: `fitness.html` (HTML + CSS + vanilla JS, no frameworks, no build step)
- Font: Bebas Neue (Google Fonts CDN) + Inter
- No external libraries
- Storage: `localStorage` (key-value, JSON serialized)
- Audio: Web Audio API (for cronometer beeps)
- Hosting: GitHub Pages (free)

## Design language

- Style reference: Nike Training Club app
- Background: `#eeeeee` (light gray, not pure white)
- Accent: `#16a34a` (green)
- Dark cards for hero sections (deficit card in Alimentación)
- Decorative SVG swoosh lines in blue (#93c5fd) across backgrounds
- Typography: Bebas Neue for titles/display, Inter for body
- Fully mobile-first, safe-area aware (iPhone notch/home bar)
- No nav bar — navigation via back buttons and home menu cards

## Architecture

The app is a single-page application with manual screen switching via `goScreen(id)`. Screens:

- `screen-inicio` — Dashboard/home
- `screen-ali` — Alimentación (nutrition tracking)
- `screen-entreno` — Entrenamiento (gym + crossfit)
- `screen-despensa` — Despensa (pantry stock) — PENDING
- `screen-compra` — Lista de compra — PENDING
- `screen-progreso` — Progreso (weight, calendar, achievements) — PENDING

## Key constraints — DO NOT BREAK

1. All JS is in a single `<script>` tag at the bottom of the file
2. All CSS is in a single `<style>` tag in the `<head>`
3. No external JS libraries (only Google Fonts CDN for typography)
4. `localStorage` is the only persistence layer
5. The file must remain a single `.html` file — no splitting into modules
6. Always run `node --check` on extracted JS before delivering
7. The cronometer drag uses `touch-action:none` — do not remove it
8. Safe area CSS variables (`--safe-top`, `--safe-bottom`) must be preserved for iPhone compatibility
9. The `goInicio()` function must always remove `#cf-input-fixed` before navigating away
10. Syntax-check JS before every delivery: extract script block, run `node --check`
