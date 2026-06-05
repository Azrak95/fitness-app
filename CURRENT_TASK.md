# CURRENT_TASK.md

## Last completed task

**Entrenamiento screen — fully implemented and polished**

All features of the Entrenamiento module are complete:
- Progressive check buttons per serie
- Cronómetro with drag, beeps, red flash
- Rep delta and weight PR badges
- CrossFit logros with add/edit/delete
- Finalizar entrenamiento with multi-session support
- Auto-connection to Alimentación (TDEE selection)
- Auto-connection to Inicio dashboard (entreno card)
- Progress bar per rutina

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
- `node --check` must pass before every delivery
- The CF fixed input (`#cf-input-fixed`) is appended to `#app`, not inside the screen div — it must be cleaned up on any navigation away from CF tab
