# Do Left-handed People Really Die Young? — A Bayesian Investigation

A statistical analysis using Bayes' theorem to investigate the widely-circulated claim that left-handed people have shorter lifespans than right-handed people. Completed as a **Data Analytics Trainee at MedTourEasy** (Dec 2023, 4-week remote internship).

> This is a **guided project** originally authored by DataCamp. My work was to implement, reproduce, and interpret the analysis as part of structured internship training — the methodology and data sources follow the DataCamp template.

---

## The question

A 1991 study found that left-handed people were dying on average ~9 years earlier than right-handed people, and the result went viral. Was this a real biological effect, or a statistical artifact?

## The methodology

**Bayesian conditional probability:** compute $P(\text{LH} \mid A)$ — the probability that a person who died at age $A$ was left-handed — using:

$$P(LH \mid A) = \frac{P(A \mid LH) \cdot P(LH)}{P(A)}$$

The key insight: $P(LH)$ is **not a constant** — it depends on the person's birth year. Left-handedness was heavily suppressed in the early 20th century (forced right-hand writing in schools), so older cohorts appear "less left-handed" than younger ones. Simply comparing average ages at death ignores this cohort effect and fabricates a lifespan gap that isn't there biologically.

## Data

- **US death records**: CDC death counts by age
- **Historical left-handedness rates by birth year**: Gilbert & Wysocki 1992 — rates climb from ~3% for people born around 1900 to ~11% for those born in the 1950s, as cultural suppression eased

## Results

| Scenario | Mean age at death — left-handed | Mean age at death — right-handed | Gap |
|---|---|---|---|
| Original computation (1986–1995 death years, 1999 handedness rates) | **67.25 years** | **72.79 years** | **5.5 years** |
| Recalculation projected to 2018 (next-generation cohort) | — | — | **2.3 years** |

**Interpretation:** the 5.5-year gap is largely a **cohort effect**, not a biological disadvantage. Left-handers who died in 1986–1995 were predominantly born before 1950, when many left-handers were forced to write right-handed and thus got miscounted. As the cohort born after ~1950 ages into the death records, the apparent gap shrinks toward zero.

## Tech stack

Python · pandas · NumPy · Matplotlib · SciPy · statsmodels

## Repository contents

```
medtoureasy-handedness-analysis/
├── notebook.ipynb          # Analysis notebook (Bayesian computation + plots)
├── data/
│   ├── cdc_vs_death.csv    # CDC death counts by age (placeholder — see below)
│   └── handedness.csv      # Historical LH rates by birth year (placeholder)
├── report.pdf              # 34-page internship deliverable (optional to include)
└── README.md
```

> Note on data: the original CSVs were provided by DataCamp and are not redistributed here. Any equivalent CDC mortality table and published handedness-by-birth-year survey will reproduce the qualitative result.

## Key takeaway

Before concluding that a group has a shorter lifespan, check whether the group's **representation in the death records reflects their representation in the living population of the same birth cohort**. If it doesn't — because of historical suppression, changing diagnostic criteria, or demographic shifts — any "lifespan gap" you compute is measuring that demographic mismatch, not biology.

## Credentials earned

- **MedTourEasy — Data Analytics Trainee** (01 Dec 2023 – 29 Dec 2023, remote)
- Project report submitted 22 Dec 2023

## License

MIT — see [LICENSE](LICENSE). Analysis methodology credit: DataCamp guided project.
