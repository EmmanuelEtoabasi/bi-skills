# Data Simulation Design Framework

This document outlines the rules, mathematical models, and techniques required to simulate business data that captures operational, analytical, and strategic nuances.

---

## 1. Decision Horizon & Date Range Rules

To represent the reality of a multi-tiered BI architecture, simulated datasets must span different time ranges and frequencies depending on the target decision horizon:

| Horizon | Date Range | Frequency | Primary Purpose |
| :--- | :--- | :--- | :--- |
| **Strategic** | 3 to 5 Years | Monthly/Quarterly | Trend forecasting, seasonal adjustments, and long-term capacity/capital planning. |
| **Analytical** | 1 to 2 Years | Daily/Weekly | Root-cause analysis, regression modeling, and customer/product correlation discovery. |
| **Operational** | 3 Months | Transactional/Hourly | Real-time monitoring, threshold exception triggers, and daily SLA monitors. |

*Rule*: All generated data must share a consistent final timestamp (e.g. matching the current date of the simulation) so that dashboards do not appear stale.

---

## 2. Point of Inflection Rules

Points of inflection are deliberate anomalies, trends, or structural breaks injected into the data to represent the business "story" described in the narratives. 

Every problem registry must define at least two inflection points:

1.  **Structural Breaks (Step Functions)**:
    *   *Concept*: A sudden, permanent shift in the baseline level of a variable.
    *   *Mathematical Spec*: $Y_t = Y_{base} + \Delta Y \cdot \mathbb{I}(t \ge T_{break})$, where $\mathbb{I}$ is the indicator function.
    *   *Use Case*: Simulating tariff hikes, renegotiated PPA rates, or a new competitor entering a region.
2.  **Cyclical & Seasonal Factors**:
    *   *Concept*: Periodic fluctuations based on season, week, or hour.
    *   *Mathematical Spec*: $S_t = A \sin\left(\frac{2\pi t}{P} + \phi\right)$, where $P$ is the period (e.g. $P=12$ for monthly, $P=24$ for hourly) and $A$ is the amplitude.
    *   *Use Case*: Weather-based solar irradiance yields (low in wet season, high in dry season), or intraday lighting sales peaks.
3.  **Anomalies & Spikes (Outliers)**:
    *   *Concept*: A short-term, extreme deviation from the normal distribution.
    *   *Mathematical Spec*: $Y_{inflection} = Y_base + \text{Noise} \pm k \cdot \sigma$, at specific timestamps $t \in \{T_{anomaly}\}$.
    *   *Use Case*: Grid shut-ins, equipment breakdowns, sudden project delays, or supplier defaults.
4.  **Gradual Drift (Trends & Degradation)**:
    *   *Concept*: A slow, long-term increase or decrease in a baseline variable.
    *   *Mathematical Spec*: $T_t = T_0 - \beta \cdot t$, where $\beta$ represents the degradation rate per time unit.
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
