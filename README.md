# RETEX · Quality Management System — Textile Recycling Operations

> **Stack:** Excel · Power BI · DAX · Statistical Process Control  
> **Domain:** Quality Engineering · Industrial Statistics · Cost Analysis  
> **Deliverables:** Relational data model · Interactive dashboard · Technical report  

---

## Overview

End-to-end quality management system designed for a textile recycling operation, built on **Juran's Quality Trilogy** as the methodological framework. The project covers the full quality lifecycle: from customer needs translation and process characterization, through statistical monitoring with SPC charts and capability indices, to financial justification of a process innovation via ROI analysis.

The system was developed entirely from scratch — data modeling, statistical calculations, DAX measures, and dashboard design — with no pre-built templates.

---

## Problem statement

The core operational issue: **inconsistent fiber purity in classified bales**, causing downstream rejections from spinning mills and driving up reclassification costs. Quantifying this gap and proposing a data-backed improvement path is the central thread of the project.

---

## What's in this repository

### `Retex.xlsx` — Relational Data Model & Statistical Engine

Six normalized tables structured as a relational model with `ID_Lote` as the primary key across tables:

| Table | Content | Rows |
|---|---|---|
| `Lotes` | 52-week lot catalog with fiber type, shift, and operator | 52 |
| `Mediciones_Pureza` | 5 purity readings per lot with running Cp/Cpk | 260 |
| `Peso_Pacas` | 20 subgroups of 5 bales for X̄-R control charts | 100 |
| `KPIs_Diarios` | Weekly tracking of 6 KPIs with automatic alert flags | 312 |
| `Costos_CONC` | Monthly cost of poor quality by category with NIR savings projection | 48 |
| `Operadores` | 6-operator catalog with individual purity averages and performance rating | 6 |

**Key Excel techniques applied:**

- `DISTR.NORM.INV` for generating normally distributed simulation data
- `DESVEST.P` for population sigma calculation across lots
- `PROMEDIO.SI.CONJUNTO` for cross-table conditional analysis
- `INDICE + COINCIDIR` for relational lookups between sheets
- Structured tables with explicit relationships by `ID_Lote`
- Conditional formatting with automatic traffic-light alerts per KPI threshold

---

### `Retex.pbix` — Power BI Dashboard (3-page interactive report)

Fully relational data model inside Power BI with custom DAX measures. No auto-generated visuals — every chart was configured with explicit data roles, formatting, and interaction logic.

**Page 1 — Executive Summary**
<img width="1380" height="774" alt="image" src="https://github.com/user-attachments/assets/86a2edac-765f-41aa-861a-29397d24cb2a" />

6 KPI cards, weekly purity trend line with minimum specification boundary, alert frequency chart, month slicer.

**Page 2 — Process Control**
<img width="1382" height="780" alt="image" src="https://github.com/user-attachments/assets/a9f75873-8194-4c67-a41d-2123d860d326" />

X̄ and R control charts with dynamically calculated control limits, process capability cards (Cp, Cpk, process sigma), out-of-control signal table, filters by shift and operator.

**Page 3 — Cost of Poor Quality & ROI**
<img width="1380" height="774" alt="image" src="https://github.com/user-attachments/assets/0921a47b-a41c-4475-9c39-968b316079b5" />

Stacked CONC chart by category and month, cumulative annual trend, savings and projected ROI cards, and an interactive **what-if simulator** with a numeric range parameter to model different error-reduction scenarios under NIR implementation.

**DAX measures written from scratch:**

```dax
-- Process capability index (real-time, context-aware)
Cpk = 
VAR mu = AVERAGE(Mediciones_Pureza[Pureza])
VAR sigma = STDEVX.P(Mediciones_Pureza, Mediciones_Pureza[Pureza])
VAR cpu = DIVIDE(100 - mu, 3 * sigma)
VAR cpl = DIVIDE(mu - 96, 3 * sigma)
RETURN MIN(cpu, cpl)

-- Dynamic process state classification
Estado_Proceso = 
SWITCH(
    TRUE(),
    [Cpk] >= 1.33, "CAPAZ",
    [Cpk] >= 1.0,  "ACEPTABLE",
    [Cpk] < 1.0,   "NO CAPAZ"
)

-- What-if ROI simulation
ROI_Simulado = 
VAR reduccion = SELECTEDVALUE('Parametro NIR'[Parametro NIR Value]) / 100
VAR ahorro_fallas_int = 15000 * reduccion
VAR ahorro_fallas_ext = 10000 * (reduccion * 0.9)
VAR inversion = 15000
RETURN DIVIDE(ahorro_fallas_int + ahorro_fallas_ext + 5000 - inversion, inversion)
```

---

### `Retex.pdf` — Technical Report

Structured analytical document covering:

- **Quality Planning:** customer segmentation (external/internal), explicit and latent needs matrix, translation of needs to measurable quality characteristics with metrics and frequencies
- **SPC Analysis:** p-chart for defective fraction (fiber purity), X̄-R chart for bale weight — with control limit calculations, stability interpretation, and signal identification
- **Process Capability:** Cp = 1.33, Cpk = 1.20 — process is capable and slightly off-center toward the upper spec (higher purity), interpreted with operational implications
- **KPI Framework:** 6 indicators with alert thresholds, responsible roles, measurement frequency, and technical justification per threshold
- **Cost of Poor Quality (COPQ):** $40,000 USD annual baseline broken down by failure category; NIR implementation projected to deliver **73.3% ROI in year 1**

---

## Statistical methods applied

| Method | Application |
|---|---|
| p-chart (attribute SPC) | Weekly defective fraction monitoring for fiber purity |
| X̄-R chart (variable SPC) | Bale weight stability across subgroups of n=5 |
| Cp / Cpk indices | Process capability against bilateral specification (96%–100%) |
| Normal distribution simulation | Synthetic dataset generation with realistic process variation |
| Ishikawa (cause-effect) | Root cause structure for classification error |
| COPQ model | Four-category cost breakdown: internal failures, external failures, appraisal, prevention |
| ROI analysis | First-year return on NIR sensor investment with what-if sensitivity |

---

## Key results

| Metric | Value | Interpretation |
|---|---|---|
| Process stability (p-chart) | ✅ Stable | All points within 3σ limits, no special causes detected |
| Process stability (X̄-R) | ✅ Stable | Mean and range under control across 20 subgroups |
| Cp (purity) | 1.33 | Adequate potential capacity |
| Cpk (purity) | 1.20 | Capable; slight positive shift — process runs at higher purity than nominal |
| Annual COPQ | $40,000 USD | Dominated by internal failures (reclassification) and lost clients |
| NIR investment | $15,000 USD | — |
| Projected annual savings | $26,000 USD | 80% reduction in internal failures + 90% in returns |
| First-year ROI | **73.3%** | Payback within 7 months |

---

## Repository structure

```
retex-quality-system/
├── Retex.xlsx          # Relational data model, SPC engine, KPI tracker
├── Retex.pbix          # Power BI dashboard (3 pages, DAX measures, what-if)
├── Retex.pdf           # Full technical report
└── README.md
```

---

## Author

**Sergio Montes Cruz**  
Quality & Process Engineer — Manufacturing / Railway sector  
Industrial Engineering · MOVAPE / UNICEP  

Field experience: dimensional inspection, NDT (RT, MT, PT, BT — Level 2), ISO 9001 / IRIS quality systems, 8D problem solving, process documentation.
