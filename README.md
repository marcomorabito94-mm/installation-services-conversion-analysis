# Installation Services: Conversion Rate Analysis

**Domain:** Retail services / installation management  
**Methods:** Correlation analysis, lead time segmentation, artisan performance ranking (weighted score)  
**Stack:** Python · pandas · numpy · matplotlib · seaborn

> **Note on data:** This repository uses synthetic data generated to replicate the structure and statistical patterns of a real case study. Artisan identifiers, monetary figures, and store references are entirely fictional. The insights and patterns are representative of the real analysis.

---

## Business context

This analysis covers the post-sale installation funnel: from the sale of a site-visit voucher through the site visit, quotation discussion, and final conversion to an installation order.

**Scope:** 17,709 completed cases (site visit performed + quotation discussed), Jan–May 2024.  
**Overall conversion rate: 42.7%**

## Three areas investigated

### 1. Lead time
Does the time from voucher payment to quotation discussion affect conversion?

**Finding:** No. Pearson correlation = **−0.03**. The majority of cases fall in the 11–20 day window and show virtually identical conversion rates. Only extreme delays (30+ days, <4% of cases) show a meaningful drop.

**Implication:** Do not over-invest in reducing lead times. Resources are better directed elsewhere.

### 2. Service article incidence (articoli 49)
Does the share of service costs in the quotation predict conversion?

**Finding:** No. Incidence is **43.8% for converted** vs **43.7% for not converted** — essentially identical.

However, **total quotation value shows a strong inverse relationship:**

| Value band | Conversion rate |
|---|---|
| €0–5k | 48.2% |
| €5–10k | 44.1% |
| €10–15k | 36.6% |
| >€15k | 31.4% |

**Implication:** Price sensitivity — not the service cost mix — is the friction point. Pricing strategy and objection handling matter more than adjusting the 49/48 article mix.

### 3. Artisan performance
**Finding:** This is the dominant driver. Among artisans with ≥100 site visits, conversion ranges from **23% to 72%** — a ~49pp gap within the same operational context.

The pattern holds within specific departments (e.g. Falegnameria / Finestre–Persiane–Tapparelle: TX range 16%–67%). The gap is **not explained by service article incidence** — it reflects individual skills, relationship management, and quotation quality.

**Implications:**
- Prioritise site-visit assignment to high-performing artisans, especially in high-value quotation segments
- Investigate and replicate the practices of top performers
- Provide structured support to underperformers before reallocating volume

## Repo structure

```
├── data_servizi/
│   └── mondo_servizi_synth.csv      # synthetic dataset
├── outputs_servizi/
│   ├── 01_lead_time.png
│   ├── 02_cifra_vs_tx.png
│   ├── 03_artisan_top_flop.png
│   └── 04_artisan_falegnameria.png
├── installation_services_analysis.ipynb
└── README.md
```

## How to run

```bash
pip install pandas numpy matplotlib seaborn scipy
jupyter notebook installation_services_analysis.ipynb
```
