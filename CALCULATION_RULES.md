# CALCULATION_RULES.md

## User profile

| Parameter | Value |
|-----------|-------|
| Name | Monir |
| Age | 31 years |
| Weight | 68.5 kg (reference) |
| Height | 171 cm |
| Goal | Fat loss + maintain/build muscle |
| Training | Gym (Mon/Wed/Fri) + CrossFit (Tue/Thu/Fri) |
| Weekends | Free eating, no tracking |

---

## TDEE by day type

Calculated using Mifflin-St Jeor BMR (~1,680 kcal) + activity multiplier:

| Training type | `state.train` value | TDEE | Approx deficit |
|--------------|-------------------|------|----------------|
| Rest day | `'descanso'` | ~2,270 kcal | ~770 kcal |
| Gym only | `'gym'` | ~2,600 kcal | ~950 kcal |
| CrossFit only | `'crossfit'` | ~2,600 kcal | ~950 kcal |
| Gym + CrossFit | `'doble'` | ~2,770 kcal | ~1,050 kcal |

Steps add: **+0.04 kcal per step** to TDEE (applied in `calcDay()`)

---

## Meal macros

### Desayuno — Tostada de pavo, café con leche y plátano
| Component | Quantity | kcal | Prot | Carbs | Fat |
|-----------|----------|------|------|-------|-----|
| Pan tostado | ~80g | ~210 | 7g | 40g | 2g |
| Pavo Hacendado | 2 lonchas (50g) | ~45 | 10g | 0g | 0.6g |
| Plátano | ~120g | ~107 | 1.3g | 27g | 0.3g |
| Bebida soja (café) | ~80ml total | ~26 | 2.5g | 1g | 1.4g |
| **TOTAL** | | **~369** | **~19g** | **~68g** | **~4g** |

---

### Comidas — Base común (todas las variedades)

Receta para **3 raciones**:
- 600g pechuga de pollo cruda (110 kcal/100g · 23g prot/100g)
- 3 cebollas (~300g) + 2 pimientos (~200g) + 3 tomates (~300g)
- 10g AOVE (aceite de oliva virgen extra)

Por ración:
- Pollo (200g crudo): 220 kcal · 46g prot
- Verduras (267g): 79 kcal · 3g prot
- AOVE (3.33g): 30 kcal · 0g prot
- **Base común: 329 kcal · 49g prot**

### Comida — Lentejas con pollo y verduras
- Base + 1 bote lentejas Hacendado 400g escurrido ÷ 3 = 133g (105 kcal/100g · 7.5g prot/100g)
- Lentejas 133g: 140 kcal · 10g prot
- **TOTAL: ~490 kcal · ~54g prot · ~48g carbs · ~9g fat** *(valor en uso, validado)*

### Comida — Garbanzos con pollo y verduras
- Base + 1 bote garbanzos Hacendado 400g escurrido ÷ 3 = 133g (120 kcal/100g · 7.5g prot/100g)
- Garbanzos 133g: 160 kcal · 10g prot
- **TOTAL: ~489 kcal · ~59g prot · ~42g carbs · ~8g fat**

### Comida — Arroz con pollo y verduras
- Base + 50g arroz crudo (350 kcal/100g · 7g prot/100g)
- Arroz 50g: 175 kcal · 3.5g prot
- **TOTAL: ~504 kcal · ~52g prot · ~54g carbs · ~5g fat**

### Comida — Patata cocida con pollo y verduras
- Base + 200g patata cocida (80 kcal/100g · 2g prot/100g)
- Patata 200g: 160 kcal · 4g prot
- **TOTAL: ~489 kcal · ~53g prot · ~49g carbs · ~5g fat**

---

### Merienda — Batido de proteínas con agua
- 30g proteína soja aislada + agua
- **117 kcal · 28g prot · 0.4g carbs · 0.5g fat**

---

### Cena — Wrap atún
1 tortilla avena (60g) + 1 lata atún natural (60g esc) + 1 huevo cocido + 1 loncha havarti light (25g) + verduras

| Component | kcal | Prot | Carbs | Fat |
|-----------|------|------|-------|-----|
| Tortilla avena 60g | 172 | 9g | 24g | 3.6g |
| Atún 60g esc (98 kcal/100g · 21g prot/100g) | 59 | 12.6g | 0g | 0.5g |
| Huevo cocido | 77 | 6.5g | 0.5g | 5.5g |
| Havarti Light 25g (267 kcal/100g · 27g prot/100g) | 67 | 6.75g | 0.1g | 4.3g |
| Verduras ~80g | 18 | 1g | 4g | 0g |
| **TOTAL sin salsa** | **~393** | **~36g** | **~29g** | **~15g** |

### Cena — Wrap pollo
1 tortilla avena (60g) + 90g pollo cocinado + 1 loncha havarti light (25g) + verduras

| Component | kcal | Prot | Carbs | Fat |
|-----------|------|------|-------|-----|
| Tortilla avena 60g | 172 | 9g | 24g | 3.6g |
| Pollo 90g cocinado (~165 kcal/100g · 31g prot/100g) | 149 | 28g | 0g | 4g |
| Havarti Light 25g | 67 | 6.75g | 0.1g | 4.3g |
| Verduras ~80g | 18 | 1g | 3g | 0g |
| **TOTAL sin salsa** | **~406** | **~45g** | **~28g** | **~12g** |

---

### Salsas
Base: 50g Queso Fresco Batido 0% Hacendado (46 kcal/100g · 8g prot/100g)

| Salsa | Ingredientes | kcal | Prot |
|-------|-------------|------|------|
| Normal | 50g QFB 0% + especias | **~23** | **~4g** |
| Rosa | QFB + 5g mostaza Dijon (148 kcal/100g) + 20g ketchup zero (82 kcal/100g) | **~47** | **~5g** |
| Piparras | Normal + 10g piparras | **~25** | **~4g** |
| Pepinillos | Normal + 15g pepinillos | **~25** | **~4g** |
| Sin salsa | — | 0 | 0 |

---

### Fruta / Postre
| Postre | kcal | Prot |
|--------|------|------|
| Manzana ~150g | ~78 | ~0g |
| Pera ~170g | ~85 | ~1g |
| Sandía ~300g | ~90 | ~2g |
| Plátano ~120g | ~107 | ~1g |
| Sin postre | 0 | 0 |

---

## Product reference (Hacendado / Mercadona)

| Product | Serving | kcal | Prot | Carbs | Fat |
|---------|---------|------|------|-------|-----|
| Pechuga pavo Hacendado | 25g (1 loncha) | ~22 | ~4.9g | <0.25g | ~0.3g |
| Bebida soja Hacendado | 100ml | 32 | 3.1g | 0.9g | 1.7g |
| Proteína soja aislada | 30g (1 scoop) | 117 | 28g | 0.4g | 0.5g |
| Tortilla avena 51% Hacendado | 60g (1 ud) | 172 | 9.1g | 24g | 3.6g |
| Atún al natural | 60g escurrido | ~59 | ~12.6g | 0g | ~0.5g |
| Havarti Light Hacendado | 25g (1 loncha) | 67 | 6.75g | 0.1g | 4.3g |
| Queso fresco batido 0% Hacendado | 100g | 46 | 8g | 3.5g | <0.5g |
| Mostaza Dijon | 100g | 148 | 7.2g | 13g | 11g |
| Ketchup zero | 100g | 82 | 1.7g | 17.8g | 0g |
| AOVE | 100g | 884 | 0g | 0g | 100g |

---

## Gym routines

### Rutina 1 (Full body)
1. Press piernas — 3s × 10–12 reps — 65/80/90 kg×lado
2. Femoral tumbado — 3s × 12–14 reps — 30/35/40 kg
3. Extensión cuádriceps — 3s × 12–14 reps — 30/35/40 kg
4. Remo polea — 3s × 10–12 reps — 55/60/65 kg
5. Pulldown agarre plano — 3s × 10–12 reps — 66/73/80 kg
6. Press pecho máquina — 3s × 8–10 reps — 73/77/82 kg
7. Tríceps polea — 3s × 8–10 reps — 50/55/60 kg
8. Curl bíceps barra — 3s × 8–10 reps — 30kg / 12.5kg×lado / 13.75kg×lado
9. Press hombro máquina — 3s × 10–12 reps — 36/41/45 kg

### Rutina 2 (Full body alternada)
1. Pendulum squat — 3s × 8–10 reps — 2.5/5/7.5 kg×lado
2. Cajón a una pierna — 3s × 8 reps por pierna
3. Press inclinado mancuerna — 4s × 8–10 reps — 17.5/20/22.5/25 kg
4. Remo banco inclinado — 4s × 8–10 reps — 25/27.5/30/32.5 kg
5. Tríceps banco mancuerna — 4s × 12–14 reps — 8/8/9/10 kg
6. Curl bíceps 45º — 4s × 12–14 reps — 10/12.5/12.5/15 kg
7. Elevaciones laterales máquina — 4s × 12–14 reps — 3.75/3.75/5/6.25 kg×lado
8. Loaded back extension — 3s × 15 reps — 20/25/30 kg
9. Deltoides posterior máquina — 3s × 10–12 reps — 32/36/41 kg

**Friday rule:** No leg exercises on either routine (double session day — gym + CrossFit)

### CrossFit
- Tuesday, Thursday, Friday
- 1 hour sessions
- No structured exercise tracking — only logros (free text achievements)

---

## localStorage key reference

| Key | Type | Description |
|-----|------|-------------|
| `day_YYYY-MM-DD` | Object | Full day state (train, meals, steps, extraX arrays) |
| `week_log` | Object | Per-day summary {kcal, prot, tdee, def, train} |
| `train_log` | Object | Per-day workout label for dashboard |
| `last_rutina` | Number | 1 or 2 — last gym rutina done |
| `gym_session_1` | Object | Current weights/reps for Rutina 1 |
| `gym_session_2` | Object | Current weights/reps for Rutina 2 |
| `gym_hist_R_i` | Array | History of sessions for rutina R, exercise i |
| `gym_pr_w_R_i` | String | All-time PR weight for rutina R, exercise i |
| `gym_delta_R_i` | Object | {dir, text} — rep delta badge for today |
| `cf_logros` | Array | CrossFit logros [{id, text, date}] |

## State shape (in-memory)

```js
state = {
  train: 'descanso' | 'gym' | 'crossfit' | 'doble',
  desayuno: 'completo' | 'nada',
  comida: 'taper' | 'garbanzos' | 'arroz' | 'patata' | 'nada',
  merienda: 'batido' | 'nada',
  cena: 'atun' | 'pollo' | 'nada' | null,
  salsa: 'rosa' | 'normal' | 'piparras' | 'pepinillos' | 'sin' | null,
  postre: 'manzana' | 'pera' | 'sandia' | 'platano' | 'sin' | null,
  steps: Number,
  extraDesayuno: [{name, k, p}],
  extraComida:   [{name, k, p}],
  extraMerienda: [{name, k, p}],
  extraCena:     [{name, k, p}]
}
```
