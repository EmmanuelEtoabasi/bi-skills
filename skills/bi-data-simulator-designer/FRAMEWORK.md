# Data Simulation Design Framework

This document outlines the rules, mathematical models, and techniques required to simulate business data that captures operational, analytical, and strategic nuances.

---

## 1. Temporal Boundary & Date Range Rules

To represent the reality of a multi-tiered BI architecture, all simulated data tables must share a single uniform timeline. Staggered date ranges are prohibited because they break referential integrity (e.g., when trying to join historical transactional data with customer cohorts or financial records).

*Rule*: Always generate data using a single timeline spanning the maximum duration required in the deployment path (e.g., if a Strategic horizon is planned, all tables must span 3–5 years). The record frequency can vary (e.g., hourly for sales, daily for invoices, monthly for inventory audits), but the boundaries `start_date` and `end_date` must remain uniform across all assets.

---

## 2. Point of Inflection Rules

Points of inflection are deliberate anomalies, trends, or structural breaks injected into the data to represent the business "story" described in the narratives. 

Every problem registry must define at least two inflection points using absolute calendar dates rather than relative day indices. This ensures direct convertibility into SQL logic (e.g., DuckDB `CASE` statements).

1.  **Structural Breaks (Step Functions)**:
    *   *Concept*: A sudden, permanent shift in the baseline level of a variable.
    *   *Mathematical Spec*: $Y_{\text{Date}} = Y_{base} + \Delta Y \cdot \mathbb{I}(\text{Date} \ge \text{'YYYY-MM-DD'})$, where $\mathbb{I}$ is the indicator function.
    *   *Use Case*: Simulating tariff hikes, renegotiated PPA rates, or a new competitor entering a region.
2.  **Cyclical & Seasonal Factors**:
    *   *Concept*: Periodic fluctuations based on season, week, or hour.
    *   *Mathematical Spec*: $S_{\text{Date}} = A \sin\left(\frac{2\pi \cdot f(\text{Date})}{P} + \phi\right)$, where $f(\text{Date})$ extracts cyclical calendar metrics (e.g. month-of-year, hour-of-day), $P$ is the period (e.g. $P=12$ for monthly, $P=24$ for hourly), and $A$ is the amplitude.
    *   *Use Case*: Weather-based solar irradiance yields, or intraday lighting sales peaks.
3.  **Anomalies & Spikes (Outliers)**:
    *   *Concept*: A short-term, extreme deviation from the normal distribution.
    *   *Mathematical Spec*: $Y_{inflection} = Y_{base} + \text{Noise} \pm k \cdot \sigma$, at specific calendar dates/timestamps $\text{Date} \in \{\text{'YYYY-MM-DD'}\}$.
    *   *Use Case*: Grid shut-ins, equipment breakdowns, sudden project delays, or supplier defaults.
4.  **Gradual Drift (Trends & Degradation)**:
    *   *Concept*: A slow, long-term increase or decrease in a baseline variable.
    *   *Mathematical Spec*: $T_{\text{Date}} = T_0 - \beta \cdot \text{DaysBetween}(\text{start\_date}, \text{Date})$, where $\beta$ represents the degradation rate per day.
    *   *Use Case*: Solar panel output efficiency loss, battery capacity degradation, or customer satisfaction drift.

---

## 3. Layer-Specific Nuance Mapping

To demonstrate value across all three organizational layers, the simulated data must be generated so that the exact same problem registers visible patterns at each layer:

```
                  ┌───────────────────────────────────────────────┐
                  │                 STRATEGIC                     │
                  │   - 3-Year baseline drift (asset degradation) │
                  │   - Year-over-year capital planning impact    │
                  └───────────────────────▲───────────────────────┘
                                          │
                                          │ Rollups
                                          │
                  ┌───────────────────────┴───────────────────────┐
                  │                 ANALYTICAL                    │
                  │   - Correlation: weather vs degradation rate  │
                  │   - Weekly regression: input vs yield         │
                  └───────────────────────▲───────────────────────┘
                                          │
                                          │ Aggregations
                                          │
                  ┌───────────────────────┴───────────────────────┐
                  │                 OPERATIONAL                   │
                  │   - Hourly generation logs                    │
                  │   - Daily out-of-bounds exception alarms      │
                  └───────────────────────────────────────────────┘
```

### Operational Layer Specifications
*   **Noise Injection**: Generate high-frequency, noisy data using a normal distribution: $X_t \sim N(\mu, \sigma^2)$.
*   **Threshold Violations**: Ensure the variance $\sigma^2$ is calibrated so that normal noise rarely crosses thresholds, but injected anomalies guarantee an out-of-bounds trigger.
*   **Timestamps**: Timestamps must be generated at the transactional level (e.g., SCADA logs every 15 minutes, or individual sales receipts with millisecond timestamps).

### Analytical Layer Specifications
*   **Explanatory Variables**: Model relationships between tables (e.g., sales volume must correlate with temperature or local holidays).
*   **Correlation Specifications**: Define a target correlation coefficient $r \in [0.6, 0.9]$ for variables meant to be analyzed together (e.g., ambient temperature vs solar panel temperature).

### Strategic Layer Specifications
*   **Long-Term Rollups**: Ensure that when hourly/daily records are rolled up to monthly aggregates, the strategic trend (e.g., $1.5\%$ annual output loss) is mathematically detectable using basic linear regression.
*   **Macro Adjustments**: Apply calendar-effect corrections (e.g., accounting for different number of trading days in February vs March) to ensure forecasts do not flag false anomalies.
