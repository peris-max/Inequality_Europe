# Inequality_Europe
# Geography of Inequality: Europe's North–South Divide

Panel analysis of income inequality across 20 European countries from 2010 to 2022.

## What this project does

Uses Gini coefficients, welfare spending, unemployment, and union density data to answer one question: **why is Southern Europe more unequal than the North?**

The short answer: it's not labour markets. It's redistribution.

## Key findings

- The **pre-transfer (market) Gini** is nearly identical across North and South — 0.453 vs 0.459
- The **post-transfer gap** is 0.038 — 84% of which is explained by weaker Southern redistribution
- **Welfare spending** is the single strongest predictor of redistribution (R² = 0.825, p < 0.001)
- **Unemployment** is the only robust within-country driver of inequality (β = 0.0018, p < 0.001, panel FE)
- The **South dummy** is insignificant in every model once spending and unemployment are controlled
- At current convergence rates, the South will reach Northern redistribution levels in ~16 years

## Data sources

| Variable | Source | Dataset |
|---|---|---|
| Post-transfer Gini | Eurostat | [ilc_di12] |
| Pre-transfer Gini | Eurostat | [ilc_di11] |
| Welfare spending % GDP | Eurostat | [spr_exp_sum] |
| Unemployment rate | Eurostat | [une_rt_a] |
| At-risk-of-poverty rate | Eurostat | [ilc_li02] |
| S80/S20 ratio | Eurostat | [ilc_di01] |
| Union density | OECD | Trade Union Dataset |
| GDP per capita | World Bank | WDI NY.GDP.PCAP.CD |

20 countries · 5 time periods (2010, 2013, 2016, 2019, 2022) · 100 panel observations

## How to run

```bash
pip install matplotlib numpy python-pptx
python inequality_charts.py       # generates 16 PNG charts + PDF
python build_presentation.py      # builds the PowerPoint deck
```

## Files

| File | Description |
|---|---|
| `inequality_charts.py` | Generates all 16 charts as PNGs using matplotlib |
| `build_presentation.py` | Builds a 17-slide PowerPoint from the charts |
| `inequality_presentation.pptx` | Ready-made presentation |

## Methods

- Cross-sectional OLS with HC3 robust standard errors (N=20, 2022)
- Two-way panel fixed effects with cluster-robust SE (N=100)
- Hausman test confirming FE over RE (p = 0.0005)
- Reynolds-Smolensky pre/post-transfer decomposition
- Difference-in-differences (pooled + staggered Callaway-Sant'Anna)
- Robustness checks: outlier exclusion, alternative DV (S80/S20), alternative group classifications, IV (lagged welfare — weak instrument, disclosed)

## Limitations

- Data manually entered from Eurostat/OECD/World Bank — not API-pulled
- Welfare spending figures are 2021 (most recent complete year); other variables are 2022
- IV attempt invalid due to weak first stage (F = 3.11); welfare endogeneity unresolved
- Only one pre-period available for parallel trends testing

## Countries

**North (9):** Iceland, Norway, Denmark, Finland, Sweden, Belgium, Netherlands, Austria, Germany

**South (11):** France, Malta, Croatia, Cyprus, Slovenia, Portugal, Spain, Italy, Greece, Romania, Bulgaria
