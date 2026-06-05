# CHANGELOG.md

## Session history — AzkFit

---

### Phase 1 — Tracker básico (artefacto)

- Built initial inline tracker widget (artifact in Claude.ai chat)
- Features: meal selector, training type, steps slider, week summary
- Stored data using `window.storage` artifact API

---

### Phase 2 — PWA conversion

**Decision:** Convert to downloadable HTML file hosted on GitHub Pages
- Single `fitness.html` file, no build tools
- User created GitHub account (azrak95) and repository (AzkNutrition)
- Deployed to `azrak95.github.io/AzkNutrition/fitness.html`
- Installable on iPhone via Safari "Add to Home Screen"

---

### Phase 3 — Design overhaul (Nike style)

- **Background:** Changed from dark (#080808) to light gray (#eeeeee)
- **Font:** Added Bebas Neue (Google Fonts) for display titles — Nike-style bold typography
- **"Monir" name** rendered in Bebas Neue 72px on home screen
- **Greeting** color changed from green to gray (text3) — less aggressive
- **All text** adapted to light background (dark text on light bg)
- **Swoosh:** Added decorative SVG blue curves (#93c5fd) crossing entire Inicio background
- **Swoosh visible through gaps** between cards (cards have z-index:1, swoosh is absolute behind)
- **Centering:** Hero section (greeting, name, date, clock) centered; "Menú principal" label centered; Progreso card centered
- **Progreso card:** Made wide (grid-column: span 2) with centered icon + text
- **Clock:** Added live clock below date — same size/style as date text, updates every second
- **Alimentación deficit card:** Dark background (#0a0a0a) with green gradient overlay for contrast

---

### Phase 4 — Alimentación screen

- Date navigator (← → arrows) to browse past days
- Large deficit display in Bebas Neue on dark card
- Macro pills (Proteína / Carbos / Grasa)
- Steps slider with live kcal calculation (+0.04 kcal/step)
- Training selector (4 options) — also auto-selected from Entrenamiento
- All meal selectors with emoji cards (✓ checkmark on selected)
- Salsa + postre section appears conditionally on cena selection
- "Guardar día" saves to localStorage

---

### Phase 5 — Entrenamiento screen

#### 5.1 — Initial build
- 3 tabs: Rutina 1 / Rutina 2 / CrossFit
- All exercises hardcoded from user's actual routines
- Collapsible exercise cards
- Weight + reps inputs per serie
- Cronómetro flotante (1:30 default)

#### 5.2 — Progressive check buttons
- **Bug fixed:** `Cannot read properties of null (reading 'value')` — reps input doesn't exist on non-last series, code tried to read it
- **Fix:** Check if element exists before reading value
- **Bug fixed:** Click on check button propagated to exercise header (closing it)
- **Fix:** Added `event.stopPropagation()` to check button onclick
- **Progressive reveal:** S1 always visible; S2 visible only after S1 done; etc.
- **Decision:** Used `visibility:hidden` (not `display:none`) to preserve layout spacing

#### 5.3 — Rep delta + PR system
- Reps pre-filled from previous session
- Delta badge: ▲ +N green pill / ▼ −N red pill — persisted in `gym_delta_R_i`
- Weight PR badge: 🏆 shows all-time max weight, saved in `gym_pr_w_R_i`
- **Bug fixed:** HTML structure was broken using `</div><div style="display:none;">` trick to insert badge row — caused last serie check button to disappear
- **Fix:** Rewrote last serie as two clean separate divs (serie-row + badge-row)

#### 5.4 — Cronómetro improvements
- Draggable via handle area (mouse + touch)
- ✕ close button
- Red background + red text at ≤3 seconds remaining
- Beeps at 3, 2, 1 seconds (Web Audio API oscillator)
- Final beep at 0

#### 5.5 — Exercise completion visual
- When all series of an exercise are done: card turns green (rgba(22,163,74,0.10)) with green border

#### 5.6 — Progress bar
- Thin bar below hint text showing % of exercises completed
- Equal weight per exercise (1/9 each for both routines)
- Animates smoothly, turns green at 100%
- **Bug fixed:** `updateEntrenoProgress` inserted before `updateNextHint` without its `function` declaration, causing `Unexpected token '}'` syntax error
- **Fix:** Restored missing `function updateNextHint(){` declaration

#### 5.7 — CrossFit logros
- Scrollable list of achievements at top
- Fixed input bar at bottom (above Finalizar button)
- Add with Enter or + button
- Edit inline (✏️) and delete (🗑️)
- Each logro has date added
- **Bug fixed:** Last logro was hidden behind fixed input bar
- **Fix:** Increased bottom margin of list container to 280px

#### 5.8 — Finalizar + connections
- Button turns green with "✓ Entrenamiento registrado" on press
- Toast notification "¡Entrenamiento registrado!" for 3 seconds
- Writes to `train_log` — shown on Inicio dashboard as "Rutina 1 ⚡"
- Multi-session support: "Rutina 1 + CrossFit" if both done same day
- **Decision:** Max 2 sessions per day, no duplicates, no infinite stacking
- Writes `dayState.train` for Alimentación auto-selection
- **Decision:** `'gym'` → Gimnasio (~2600), `'crossfit'` → CrossFit (~2600), `'doble'` → Doble sesión (~2770)
- Calls `updateInicio()` immediately so dashboard updates without navigation

---

### Pending phases

- **Phase 6:** Despensa + Compra
- **Phase 7:** Progreso (weight graph, calendar, photos, logros)
- **Phase 8:** General polish, resumen semanal/mensual/anual
