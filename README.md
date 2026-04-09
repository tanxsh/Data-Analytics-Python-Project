# Behind the Wheel: A Data Story of Traffic Collisions in California

**Exploratory Data Analysis of California Traffic Collisions from 2020 to 2025**

Course: ISBA 2401 — Data Analytics with Python | Santa Clara University

---

## Overview

This project analyzes over 2 million traffic collision records from the California Highway Patrol (CHP) Traffic Records System to uncover patterns in crash frequency, severity, demographics, and environmental conditions across all 58 California counties from 2020 to 2025.

**Data Source:** [California Collision Records System (CCRS)](https://data.ca.gov/dataset/ccrs) — California Open Data Portal

**Unit of Analysis:** Individual traffic collision event

---

## Research Questions & Hypotheses

**Main Research Question:** What patterns and trends can be identified in California traffic collisions from 2020–2025, and how do demographic and environmental factors influence the frequency and severity of crashes?

| Hypothesis | Finding |
|---|---|
| H1: Urban areas have higher collision frequency than rural areas | Confirmed — LA County alone accounts for 25%+ of statewide volume |
| H2: Severe weather increases collision likelihood | Rejected — majority of crashes occur in clear weather |
| H3: Impaired driving and speeding lead to higher severity | Partially confirmed — speeding drives volume; wrong-side driving and DUI drive fatalities |

---

## Project Structure

```
├── Data_Merging.ipynb       # Load and merge annual Crashes + Parties CSVs (2020–2025)
├── Data_Analysis.ipynb      # Full EDA: geographic, demographic, and behavioral analysis
└── README.md
```

---

## Methodology

### Data Pipeline (`Data_Merging.ipynb`)
- Loaded 12 CSV files (Crashes + Parties for each year: 2020–2025)
- Concatenated into two master DataFrames and saved as merged CSVs for analysis

### Analysis (`Data_Analysis.ipynb`)

**Data Preparation**
- Standardized column names across years
- Built mapping rulebooks for county codes, collision factor violations, and severity descriptions
- Engineered **Severity Score** = `NumberInjured + (3 × NumberKilled)` — a weighted metric used in traffic safety analytics

**Three analytical dimensions:**

#### 1. Geographic Distribution
- Identified top 10 counties by collision volume (2020–2025)
- Isolated Los Angeles as a statistical outlier (100k+ annual collisions)
- Built county-level severity heatmap
- Forecasted 2026 statewide collisions using **Linear Regression** (~365,000 predicted)

#### 2. Demographic Analysis
- Segmented collision involvement by age group (0–17, 18–25, 26–35, 36–50, 51–65, 65+) and gender
- Computed average severity score by age group and gender

#### 3. Driver Behavior & Environmental Factors
- Mapped top 5 collision violation types by frequency and by average severity
- Analyzed crash distribution by lighting condition, weather condition, and hour of day

---

## Tools & Technologies

| Tool | Purpose |
|---|---|
| Python (pandas, numpy) | Data loading, cleaning, merging, feature engineering |
| matplotlib, seaborn | Data visualization |
| scikit-learn (LinearRegression) | 2026 collision volume forecasting |

---

## Key Findings

**Geographic**
- Los Angeles County records more collisions annually than the next 5 counties combined — driven by frequency of minor incidents, not high-severity crashes
- Linear regression forecasts ~365,000 statewide collisions in 2026

**Demographic**
- Highest collision volume: Males aged 26–50 (core workforce demographic)
- Highest average crash severity: Drivers aged 0–17, regardless of gender
- Male drivers are involved in nearly double the collisions of female drivers across all age groups

**Behavioral & Environmental**
- Speeding (~650k incidents) and Unsafe Turning (~475k) drive collision volume
- Wrong-side-of-road driving has an average severity score of 10.0 — the deadliest behavior
- Contrary to H2, ~2M collisions occurred in clear weather and ~1.5M in daylight — human error, not weather, is the dominant risk factor
- Crash peaks align with morning and evening commute hours, confirming traffic density as the primary driver

---

## Recommendations

1. **Automated enforcement** — speed cameras in high-density urban areas to tackle speeding at scale
2. **Physical infrastructure** — center median barriers and lane separators to prevent wrong-side collisions
3. **Youth-focused licensing** — stricter driving tests to reduce severity of crashes involving under-18 drivers
4. **Lighting & lane markings** — improve rural road visibility to reduce unsafe lane change incidents
5. **Long-term** — invest in public transportation alternatives to reduce overall vehicle dependency
