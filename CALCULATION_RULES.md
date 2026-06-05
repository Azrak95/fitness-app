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

### Desayuno completo
| Component | Quantity | kcal | Prot | Carbs | Fat |
|-----------|----------|------|------|-------|-----|
| Pan tostado | ~80g | ~210 | 7g | 40g | 2g |
| Pavo Hacendado | 2 lonchas (50g) | ~45 | 10g | 0g | 0.6g |
| Plátano | ~120g | ~107 | 1.3g | 27g | 0.3g |
| Bebida soja (café) | ~80ml total | ~26 | 2.5g | 1g | 1.4g |
| **TOTAL** | | **~369** | **~19g** | **~68g** | **~4g** |

### Comida — Táper (sin arroz)
Per ración (3 raciones de: 600g pollo crudo, 1 pimiento verde, 1 pimiento rojo, 3 cebollas, 3 tomates, 1 bote lentejas Hacendado 400g escurrido, 10g AOVE). Postre: manzana.

| Component | kcal | Prot | Carbs | Fat |
|-----------|------|------|-------|-----|
| Táper base | ~400 | ~51.5g | ~26g | ~8.8g |
| Manzana ~150g | ~80 | ~0.5g | ~20g | 0g |
| **TOTAL** | **~490** | **~53.5g** | **~48g** | **~8.8g** |

### Comida — Táper + arroz 50g seco
- Base táper: 490 kcal
- Arroz 50g seco: +~175 kcal, +38g carbs
- **TOTAL: ~665 kcal · 61g prot · 86g carbs · 9g fat**

### Comida — Táper + arroz 70g seco
- Base táper: 490 kcal
- Arroz 70g seco: +~245 kcal, +53g carbs
- **TOTAL: ~735 kcal · 64g prot · 101g carbs · 9g fat**

### Comida — Alternativa rápida
- Jarred vegetables (Mercadona) + atún + huevo cocido
- **~350 kcal · 40g prot · 20g carbs · 8g fat**

### Merienda — Batido proteína
- 30g proteína soja aislada + agua
- **117 kcal · 28g prot · 0.4g carbs · 0.5g fat**

### Cena — Wrap atún
1 tortilla avena (60g) + 1 lata atún natural (60g esc) + 1 huevo cocido + 1 loncha havarti light (25g) + verduras + sin salsa

| Component | kcal | Prot | Carbs | Fat |
|-----------|------|------|-------|-----|
| Tortilla avena 60g | 172 | 9.1g | 24g | 3.6g |
| Atún 60g esc | 50 | 12g | 0g | 0.5g |
| Huevo cocido | 77 | 6.5g | 0.5g | 5.5g |
| Havarti Light 25g | 52 | 4.4g | 0.1g | 3.8g |
| Verduras ~100g | 25 | 1.5g | 4g | 0g |
| **TOTAL sin salsa** | **~366** | **~33g** | **~29g** | **~13g** |

### Cena — Wrap pollo
1 tortilla avena + 90g pollo cocinado + 1 loncha havarti + verduras + sin salsa

| Component | kcal | Prot | Carbs | Fat |
|-----------|------|------|-------|-----|
| Tortilla avena 60g | 172 | 9.1g | 24g | 3.6g |
| Pollo 90g cocinado | 148 | 28g | 0g | 4g |
| Havarti Light 25g | 52 | 4.4g | 0.1g | 3g |
| Verduras ~80g | 20 | 1g | 3g | 0g |
| **TOTAL sin salsa** | **~382** | **~42g** | **~27g** | **~11g** |

### Salsas
| Salsa | Ingredients | kcal | Prot |
|-------|------------|------|------|
| Rosa | 50g QFB 0% + 5g mostaza Dijon + 20g ketchup zero | ~60 | ~5g |
| Normal | 50g QFB 0% + especias | ~40 | ~4g |
| Piparras | Normal + 10g piparras | ~45 | ~4g |
| Pepinillos | Normal + 15g pepinillos | ~43 | ~4g |
| Sin salsa | — | 0 | 0 |

### Postres cena
| Postre | kcal | Prot |
|--------|------|------|
| Sandía ~300g | ~90 | ~1.5g |
| Pera ~170g | ~85 | ~0.5g |

---

## Product reference (Hacendado / Mercadona)

| Product | Serving | kcal | Prot | Carbs | Fat |
|---------|---------|------|------|-------|-----|
| Pechuga pavo Hacendado | 25g (1 loncha) | ~22 | ~4.9g | <0.25g | ~0.3g |
| Bebida soja Hacendado | 100ml | 32 | 3.1g | 0.9g | 1.7g |
| Proteína soja aislada | 30g (1 scoop) | 117 | 28g | 0.4g | 0.5g |
| Tortilla avena 51% Hacendado | 60g (1 ud) | 172 | 9.1g | 24g | 3.6g |
| Atún al natural | 60g escurrido | ~50 | 12g | 0g | 0.5g |
| Havarti Light Hacendado | 25g (1 loncha) | 52 | 4.4g | 0.1g | 3.8g |
| Queso fresco batido 0% Hacendado | 100g | 46 | 8g | 3.5g | <0.5g |
| Mostaza Dijon | 100g | 149 | 7.2g | 13g | 11g |
| Ketchup zero | 100g | 83 | 1.7g | 17.8g | 0g |

---

## Rice rules (arroz aparte del táper)

| Day type | Rice amount (dry) | Added kcal |
|----------|------------------|------------|
| Rest day | 0g | 0 |
| Single session (gym or CF) | ~50g | ~175 kcal |
| Double session (Fri: gym + CF) | ~70g | ~245 kcal |

Rice is NOT included in the táper. It is added separately based on the day.

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
| `day_YYYY-MM-DD` | Object | Full day state (train, meals, steps) |
| `week_log` | Object | Per-day summary {kcal, prot, tdee, def, train} |
| `train_log` | Object | Per-day workout label for dashboard |
| `last_rutina` | Number | 1 or 2 — last gym rutina done |
| `gym_session_1` | Object | Current weights/reps for Rutina 1 |
| `gym_session_2` | Object | Current weights/reps for Rutina 2 |
| `gym_hist_R_i` | Array | History of sessions for rutina R, exercise i |
| `gym_pr_w_R_i` | String | All-time PR weight for rutina R, exercise i |
| `gym_delta_R_i` | Object | {dir, text} — rep delta badge for today |
| `cf_logros` | Array | CrossFit logros [{id, text, date}] |
