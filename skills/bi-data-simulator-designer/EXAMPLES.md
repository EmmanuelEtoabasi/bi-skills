# Worked Examples: Data Simulation Design

This document provides a worked example showing how to specify cyclical, random, and trend-based data for a business problem.

---

## Example Case: Renewable Energy Storage Capacity Degradation

### Business Problem
A solar farm operator uses battery storage to arbitrage energy in the spot market and fulfill PPA peak contracts. Battery degradation is causing unexpected capacity drops, resulting in peak-shaving shortfalls and Spot Arbitrage Penalties.

### 1. Context & Path Registry (`path-definition.md` mapping)
*   **Problem ID**: `UC-CAN-01` (Strategic: spot market optimization; Operational: charge cycles; Analytical: decay rate correlation).
*   **Simulated Data Markers**: `battery_capacity_ah`, `cell_temperature_c`, `charge_cycles_count`, `discharge_rate_c`.

---

### 2. Detailed Simulation Spec (`16-data-simulation-specification.md`)

*   **Story Narrative Link**: `NR-PRED-01` ("If cell degradation continues at the current rate of 1.2% per month, Battery Bank B will fail PPA peak commitments by October, incurring a £28,000 spot penalty.")
*   **Target Inflection Timestamp(s)**: 
    *   *Surge Anomaly*: `2024-08-15` (Lightning strike causing fuse blowouts and sudden 8% capacity drop).
    *   *Structural Break (Cell Swap)*: `2025-03-10` (Target cell replacement restoring capacity by 25%).
*   **Layer-by-Layer Spec**:
    *   **Operational**: Hourly temperature logs (`cell_temperature_c`) and state-of-charge (`soc_pct`). Generate daily out-of-bounds alerts when `soc_pct` drops below 15% during peak discharge windows (4:00 PM – 7:00 PM).
    *   **Analytical**: Regression modeling. Capacity decay rate correlates with charge cycles and ambient temperature:
        $$\text{Decay Rate } d_t = d_{\text{base}} \cdot \left(1 + \gamma \cdot \text{cell\_temp\_c}\right)$$
    *   **Strategic**: 3-year capacity degradation curve showing a $4.5\%$ annual output loss rolled up to monthly averages, with a step-function break on cell swap date.

*   **Mathematical Simulation Formula**:
    For $t \in [0, 1095]$ days (representing 3 years, starting `2023-06-01`):

    $$\text{Capacity}_t = C_0 \cdot \prod_{i=1}^t (1 - d_i) + \Delta C \cdot \mathbb{I}(t \ge T_{\text{swap}}) - \Delta C_{\text{strike}} \cdot \mathbb{I}(t \ge T_{\text{strike}}) + \epsilon_t$$

    *   Where:
        *   $C_0 = 1000.0$ Ah (initial capacity)
        *   $d_i = \text{Daily Degradation Rate} = 0.00012$ (approx 4.5% annually)
        *   $\Delta C = +250.0$ Ah (structural break cell restoration)
        *   $T_{\text{swap}} = 648$ (Day 648: `2025-03-10`)
        *   $\Delta C_{\text{strike}} = 80.0$ Ah (lightning strike damage)
        *   $T_{\text{strike}} = 441$ (Day 441: `2024-08-15`)
        *   $\epsilon_t \sim N(0, 1.5^2)$ (daily measurement noise)

*   **Generator Implementation Rules**:
    1.  **Seed Lock**: Ensure `numpy.random.seed(42)` is set at the start of the script to guarantee consistent daily noise across runs.
    2.  **Date Alignment**: Parse the timestamps using a relative delta from `2023-06-01` to map day index $t$ directly to calendar dates.
    3.  **Out-of-Bounds Trigger**: On Day 441 ( lightning strike), instantly force `discharge_rate_c` to spikes above `1.8` for a 4-hour window to trigger the operational exception logs.
