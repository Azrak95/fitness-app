# APP_STATE.md — Current Module Status

## ✅ SCREEN: Inicio (Dashboard)

**Status:** Complete

**Features:**
- Dynamic greeting (Buenos días / Buenas tardes / Buenas noches) based on current hour
- "Monir" in Bebas Neue large display font
- Current date (e.g. "Viernes, 5 de junio")
- Live clock updating every second (same size/style as date)
- Decorative SVG swoosh in blue crossing entire screen background (visible through gaps between cards)
- Quick stats cards:
  - Déficit hoy: shows kcal deficit + kcal ingested (from `week_log`)
  - Entreno: shows completed workout label + date (from `train_log`), with ⚡ emoji, green color
- Menu grid with 5 cards: Alimentación, Entreno, Despensa, Compra, Progreso
- Each card has color-coded accent bar (green, amber, blue, red, purple)
- Progreso card is wide (full width) with centered icon + text

**localStorage keys read:** `week_log`, `train_log`

---

## ✅ SCREEN: Alimentación

**Status:** Complete

**Features:**
- Date navigator (← Hoy →) to browse past days
- Hero deficit card (dark background) showing: déficit kcal (large, color-coded), TDEE, kcal ingeridas, progress bar
- Macro pills: Proteína / Carbos / Grasa
- Steps slider (0–20,000, steps of 500) — adds ~0.04 kcal per step to TDEE
- Entrenamiento selector (4 options): Descanso / Gimnasio / CrossFit / Doble sesión
  - **Auto-selected** when coming from Entreno screen after finalizing workout
- Meal selectors: Desayuno / Comida / Merienda / Cena
- Salsa selector (appears only when Cena is selected and not "Sin cena")
- Postre selector (appears with salsa section)
- "Guardar día" button saves to `week_log` and `day_YYYY-MM-DD`

**Auto-connection with Entreno:**
When `finalizarEntreno()` runs, it writes `state.train` and `dayState.train` so Alimentación auto-selects the correct entrenamiento option:
- Gym only → `'gym'` → selects "Gimnasio"
- CF only → `'crossfit'` → selects "CrossFit"
- Gym + CF → `'doble'` → selects "Doble sesión"

**localStorage keys read/written:** `day_YYYY-MM-DD`, `week_log`

---

## ✅ SCREEN: Entrenamiento

**Status:** Complete

**Features:**

### Rutina selector
- 3 tabs: Rutina 1 | Rutina 2 | CrossFit
- Shows hint: "Última sesión: Rutina 1 · Toca Rutina 2" based on `last_rutina`
- Progress bar below hint: fills as exercises are completed (per-exercise, equal weight)

### Exercise cards (Rutina 1 & 2)
- All exercises from both routines hardcoded (R1: 9 exercises, R2: 9 exercises)
- Each card is collapsible (tap header to open/close)
- Each serie shows: weight input (120px wide, fits "100kg×lado") + check button
- Last serie additionally shows: reps input
- Check buttons are progressive: S1 always visible; S2 appears only after S1 checked; S3 after S2, etc.
- Checked series are dimmed (opacity 0.45)
- When ALL series of an exercise are done: card background turns green (`rgba(22,163,74,0.10)`) with green border
- Reps delta badge (last serie only): ▲ +N green pill if improved, ▼ −N red pill if worse vs previous session
- Weight PR badge: 🏆 shows max weight ever recorded for that exercise (last serie)
- Previous session reps pre-filled in last serie input
- All data persists in localStorage

### Cronómetro flotante
- Appears automatically when any check button is pressed
- Draggable (mouse and touch) via handle area at top
- Default: 1:30, adjustable in 30s blocks with − and + buttons
- ✕ button to close
- Countdown: at 3, 2, 1 seconds → background turns dark red, display turns red, beep sound (Web Audio API)
- At 0: shows "¡Listo!" + final beep

### CrossFit tab
- Header with ⚡ CROSSFIT title
- Scrollable list of logros (achievements) at top
- Fixed input bar at bottom (above Finalizar button): text field + "+" button (also works with Enter)
- Each logro shows: text, date added, ✏️ edit button, 🗑️ delete button
- Edit mode: inline input replacing the text, OK/✕ buttons
- Logros persist in `cf_logros`

### Finalizar entrenamiento button
- Fixed at bottom of screen (above nav)
- On press: turns green, shows "✓ Entrenamiento registrado", toast "¡Entrenamiento registrado!" for 3s
- Writes to `train_log[today]` — accumulates up to 2 sessions (e.g. "Rutina 1 + CrossFit"), prevents duplicates and >2 sessions
- Writes `dayState.train` for Alimentación auto-selection
- Saves `last_rutina` for next-session hint
- Saves exercise history and PRs
- Calls `updateInicio()` to update dashboard immediately

**localStorage keys read/written:**
`gym_session_1`, `gym_session_2`, `gym_hist_1_N`, `gym_hist_2_N`, `gym_pr_w_1_N`, `gym_pr_w_2_N`, `gym_delta_1_N`, `gym_delta_2_N`, `last_rutina`, `train_log`, `day_YYYY-MM-DD`, `cf_logros`

---

## 🔲 SCREEN: Despensa — PENDING

**Planned features:**
- Fixed non-perishable product list with quantities (atún, huevos, proteína, tortillas avena, pavo, havarti, QFB, ketchup zero, mostaza, arroz, lentejas...)
- Free-text field to add custom items
- Red dot on menu card when any item is low (≤1 unit)
- Auto-decrease stock when meals are logged in Alimentación
- When stock = 1 → item auto-added to Lista de Compra

---

## 🔲 SCREEN: Compra — PENDING

**Planned features:**
- Auto-populated from Despensa when stock hits 1
- Each item has "Comprado" button
- On "Comprado": adds full pack quantity back to Despensa stock

---

## 🔲 SCREEN: Progreso — PENDING

**Planned features:**
- Period selector: semana / mes / año / total desde día 1
- Stats per period: déficit acumulado, días entrenados, proteína media, kcal media, peso perdido
- Weight tracking: add entries with date, graph of evolution, total lost
- Training calendar: marks days with completed workouts (from `train_log`)
- Photo gallery: add progress photos from camera roll (base64, compressed, localStorage)
- Logros/PRs section: view and manage all-time personal records
- Counter: days since training started
