# Brice Turang: Hitter Development Plan

A player development plan built only from 2024 data, then tested against what actually happened in 2025 and 2026.

![Turang's bat speed, attack angle and xwOBA, 2023–2026](outputs/charts/step10_hero_swing_change.png)

## TL;DR

| | |
|---|---|
| **Question** | After the 2024 season, what was the #1 thing Brice Turang needed to fix in his swing, and how would we know it worked? |
| **Answer** | Bat speed. Across 215 qualified MLB hitters, it had the strongest link to damage of any swing metric (0.73 with barrel rate). Turang swung 66.1 mph, near the bottom of the league. |
| **Result** | His bat speed rose to 70.6 mph in 2025 and held in 2026. His barrel rate more than tripled (2.4% → 7.9%), and his xwOBA went from the league's bottom quarter to its top quarter (.302 → .344). 3 of 4 goals were met in both seasons. |

## Why this project

In 2024, Turang was one of the best contact hitters in MLB: he missed on only 13.8% of his swings. But his swing was among the slowest and flattest in the league, so that contact turned into ground balls instead of damage.

I wanted to answer the question a player development (PD) department asks every off-season: where does this player stand, and what is the one thing that will make him better next year? I built the plan using only the data available after 2024, the way an analyst would have that winter, and then checked it against the next two seasons.

What surprised me most was how much one change, bat speed, could change the whole picture in a single season.

The same idea works outside baseball: when you find what really needs to change and target it, the results are mostly positive.

## Approach

The full analysis is in [`notebooks/turang_idp.ipynb`](notebooks/turang_idp.ipynb), in 10 steps.

| Step | Question | What I did |
|---|---|---|
| 1–2 | Can I trust the data? | Loaded 9,962 pitches and 20 league leaderboards (2023–2026). Removed bunts and non-competitive swings, and matched Savant's bat speed numbers within 0.2 mph. |
| 3–5 | Where does he rank? | Built league benchmarks (median and percentiles) and ranked Turang on 12 metrics. He was last of 215 on attack angle and in the 3rd percentile on bat speed, but in the 93rd on contact. |
| 6 | What is the #1 fix? | Compared each swing metric with damage across the league. Bat speed had the strongest link: 0.73 with barrels and 0.49 with xwOBA, vs. 0.36 and −0.01 for attack angle. |
| 7–8 | What's the plan? | Set four measurable goals from the benchmarks and wrote a three-phase drill plan (off-season, spring, in-season). |
| 9–10 | Did it work? | Built a season table, rolling 100-swing charts and a goal scorecard for 2025–2026. |

![Turang's 2024 percentile profile](outputs/charts/step05_percentile_profile_2024.png)

## Findings

### Goal scorecard

| Goal | 2024 | Target | 2025 | 2026 | Result |
|---|---|---|---|---|---|
| Bat speed (mph) | 66.1 | 70+ | 70.6 | 70.1 | Met both years |
| Attack angle (°) | 1.0 | 9–12 | 6.9 | 8.6 | Missed, but rising every year |
| Barrel rate (%) | 2.4 | 5+ | 7.9 | 7.7 | Met both years |
| Whiff rate (guardrail) | 13.8% | under 23% | 18.9% | 21.4% | Held, but close to the line |

### What the data shows

- **The change happened all at once.** His bat speed jumped right at the start of 2025, which points to off-season work rather than a slow build during the season.
- **Speed came first, then the path.** His attack angle climbed gradually through 2025 and only reached the 9–12° range late in 2026.
- **He paid for it in contact.** His whiff rate rose from 13.8% to 21.4%, the trade-off the guardrail was there to watch.
- **The trade was worth it.** His xwOBA went from the league's 25th percentile (.302) to above the 75th (.344).
- **He didn't need an average swing to become an above-average hitter.** In 2026 his bat speed and attack angle were still below the league median, but his xwOBA was well above it. A good-enough swing on top of elite contact was enough.

![Rolling bat speed, 2024–2026](outputs/charts/step09_rolling_bat_speed.png)

## Limitations

- **I don't know what the Brewers actually did.** The data shows that his swing changed, not which drills caused it. My plan pointed in the right direction; that doesn't mean my drills are what worked.
- **Written in hindsight.** Every decision used only 2024 data, but I knew 2025 and 2026 had already happened. A plan written in real time is the true test.
- **2024 was his low point.** In the second half of 2023 he already swung 68.4 mph, so part of the jump was a return to his earlier level.
- **Correlation isn't causation.** Faster bats go with more barrels across hitters, but that doesn't prove adding speed causes barrels for every hitter.
- **Some results were luck.** His actual wOBA ran ahead of his expected wOBA in both seasons, so I judge results on xwOBA.

## Skills shown

- Data cleaning and validation against a trusted source (within 0.2 mph of Baseball Savant)
- Merging five leaderboards across four seasons, including mismatched ID columns
- Benchmarking with league medians and percentiles
- Percentile ranks, correlation, sample size, standard error and rolling averages
- Data visualization in Matplotlib: percentile profiles, scatter plots, rolling trends, a multi-panel summary chart
- Turning analysis into one priority, measurable goals, a guardrail and a drill plan
- Writing the same findings for a player, a hitting coach and a PD director, in English and Spanish

**Tools:** Python, pandas, NumPy, Matplotlib, Jupyter, Baseball Savant (Statcast)

## How to run it

1. Install Python 3.10+ and the packages:

   ```bash
   pip install pandas numpy matplotlib jupyter
   ```

2. Clone the repository:

   ```bash
   git clone https://github.com/OmarMorillo/turang-hitter-development-plan.git
   cd turang-hitter-development-plan
   ```

3. Open `notebooks/turang_idp.ipynb` and run all cells. The raw data is in `data/raw/` (sources in [`data/raw/SOURCES.md`](data/raw/SOURCES.md)). The notebook writes clean files to `data/clean/` and charts to `outputs/charts/`.

## Repository structure

```text
turang-hitter-development-plan/
├── README.md
├── data_dictionary.md        # every column used: meaning, units, source
├── data/
│   ├── raw/                  # Baseball Savant downloads, unchanged
│   └── clean/                # written by the notebook
├── notebooks/
│   └── turang_idp.ipynb      # the full analysis, Steps 1–10
└── outputs/
    └── charts/               # every chart in the notebook
```

**Data:** Baseball Savant, MLB Advanced Media (baseballsavant.mlb.com). Regular season, 2023–2026. Bat tracking began July 14, 2023, so 2023 swing metrics cover the second half only.

## About me

**Omar Morillo Aldana.** Former college player formed in Venezuelan baseball, Driveline-certified hitting coach, and M.S. Information Systems student at Point Park University. I'm learning to combine what the numbers say with how the swing actually works.

[GitHub](https://github.com/OmarMorillo) · [LinkedIn](https://www.linkedin.com/in/omar-morillo-203a9124a/) · Morilloaldanaomar@gmail.com

---

## Resumen en español

**Brice Turang: plan de desarrollo de un bateador**

**La pregunta:** después de la temporada 2024, ¿qué era lo más importante que Brice Turang tenía que mejorar en su swing, y cómo sabríamos si funcionó?

**La respuesta:** la velocidad del bate. Entre los 215 bateadores calificados de MLB, fue la métrica del swing más relacionada con el daño (0.73 con el porcentaje de barrels). Turang bateaba a 66.1 mph, casi en el último lugar de la liga.

**El resultado:** su velocidad del bate subió a 70.6 mph en 2025 y se mantuvo en 2026. Su porcentaje de barrels se triplicó (2.4% → 7.9%), y su xwOBA pasó del cuarto más bajo de la liga al cuarto más alto (.302 → .344). Cumplió 3 de 4 metas en ambas temporadas.

Armé el plan usando solo los datos disponibles después de 2024, como lo haría un analista ese invierno, y después lo comparé con lo que pasó en 2025 y 2026. Lo que más me sorprendió fue cómo un solo cambio, la velocidad del bate, pudo cambiar todo el panorama en una temporada.

**Lo que muestran los datos:**

- El cambio llegó de golpe: su velocidad del bate subió justo al empezar 2025, señal de trabajo en la pretemporada.
- Primero la velocidad, después el ángulo: su ángulo de ataque subió poco a poco y llegó al rango de 9–12° a finales de 2026.
- Pagó un precio en contacto: su porcentaje de swings fallados subió de 13.8% a 21.4%, pero se quedó debajo del límite de 23%.
- Valió la pena: pasó del cuarto más bajo de la liga al cuarto más alto en valor ofensivo esperado.

**Sobre mí:** exjugador universitario formado en el béisbol venezolano, entrenador de bateo certificado por Driveline y estudiante de la maestría en Sistemas de Información en Point Park University. Estoy aprendiendo a combinar lo que dicen los números con cómo funciona el swing de verdad.
