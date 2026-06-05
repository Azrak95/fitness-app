# CURRENT_TASK.md

## Last completed task

**Alimentación screen — overhaul completo (Phase 6)**

Todo implementado y con macros calculados de ingredientes reales:
- Header centrado
- Grid entrenamiento reordenado (Gym · CrossFit · Doble · Descanso)
- Desayuno renombrado con nombre descriptivo
- Comida: 4 opciones nuevas con macros reales (lentejas, garbanzos, arroz, patata)
- Merienda renombrada
- Cena: wraps recalculados con valores exactos de producto (Havarti, atún)
- Salsas recalculadas (QFB 0% real = 23 kcal base)
- Postre expandido: Manzana · Pera · Sandía · Plátano · Sin postre
- Bloque "✏️ Otro" en cada comida: multi-item con nombre, kcal y prot por item
- Bug timezone dkey() corregido (local vs UTC)
- Bug Entrenamiento→Alimentación sync corregido

---

## Next task: DESPENSA

Build the Despensa screen. This is the next priority.

### Requirements

1. **Fixed product list** with stock quantities (editable):
   - Atún al natural (unit: lata, pack size: 6)
   - Huevos (unit: huevo, pack size: 12)
   - Proteína de soja (unit: scoop/toma, pack size: ~30 scoops per bag)
   - Tortillas de avena Hacendado (unit: tortilla, pack size: 6)
   - Pechuga pavo Hacendado (unit: loncha, pack size: 8)
   - Havarti Light Hacendado (unit: loncha, pack size: 12)
   - Queso fresco batido 0% (unit: bote, pack size: 1)
   - Ketchup zero (unit: bote, pack size: 1)
   - Mostaza Dijon (unit: bote, pack size: 1)
   - Arroz (unit: g, pack size: 1000g)
   - Lentejas Hacendado bote (unit: bote, pack size: 1)

2. **Custom items** — free text + quantity field to add anything not in the fixed list

3. **Auto-decrease** — when a meal is saved in Alimentación, relevant items decrease:
   - Wrap atún → atún -1 lata
   - Wrap pollo → no pantry item (chicken is fresh)
   - Táper → lentejas -1 bote (if using legumes)
   - Batido → proteína -1 scoop
   - Desayuno completo → pavo -2 lonchas, tortilla avena -0 (bread is fresh)
   - Cena con havarti → havarti -1 loncha
   - Salsa rosa/normal → QFB -50g (track by weight)

4. **Low stock alert** — when quantity ≤ 1 unit:
   - Red dot appears on Despensa card in Inicio menu
   - Item is automatically added to Lista de Compra

5. **Design** — same style as rest of app, list of product cards with +/− quantity buttons

### After Despensa: COMPRA

Then: PROGRESO

---

## Things that must NOT be broken

- `goInicio()` must call `document.getElementById('cf-input-fixed')?.remove()` before navigating
- `finalizarEntreno()` must keep its dual-session logic (`train_log` accumulation + `dayState.train` TDEE mapping)
- `syncUI()` in Alimentación reads `state.train` — the 4 valid values are: `'descanso'`, `'gym'`, `'crossfit'`, `'doble'`
- The cronómetro drag uses `position:fixed` with `top/left` after first drag — do not reset to `bottom/right` on re-render
- The CF fixed input (`#cf-input-fixed`) is appended to `#app`, not inside the screen div — it must be cleaned up on any navigation away from CF tab
- `extraDesayuno/Comida/Merienda/Cena` in state are **arrays** `[{name,k,p}]`, NOT objects `{k,p}` — backward compat handled in `getExtra(g)`
