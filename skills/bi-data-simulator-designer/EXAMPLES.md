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
        $$\text{Decay Rate}_{\text{Date}} = d_{\text{base}} \cdot \left(1 + \gamma \cdot \text{cell\_temp\_c}_{\text{Date}}\right)$$
    *   **Strategic**: 3-year capacity degradation curve showing a $4.5\%$ annual output loss rolled up to monthly averages, with a step-function break on cell swap date.

*   **Mathematical Simulation Formula**:
    For $\text{Date} \in [\text{'2023-06-01'}, \text{'2026-06-08'}]$:

    $$\text{Capacity}_{\text{Date}} = C_0 \cdot (1 - \text{Decay Rate})^{\text{DaysBetween}(\text{'2023-06-01'}, \text{Date})} + \Delta C \cdot \mathbb{I}(\text{Date} \ge \text{'2025-03-10'}) - \Delta C_{\text{strike}} \cdot \mathbb{I}(\text{Date} = \text{'2024-08-15'}) + \epsilon_{\text{Date}}$$

    *   Where:
        *   $C_0 = 1000.0$ Ah (initial capacity)
        *   $\text{Decay Rate} = 0.00012$ (approx 4.5% annually)
        *   $\Delta C = +250.0$ Ah (structural break cell restoration)
        *   $\Delta C_{\text{strike}} = 80.0$ Ah (lightning strike damage anomaly)
        *   $\epsilon_{\text{Date}} \sim N(0, 1.5^2)$ (daily measurement noise)

*   **Generator Implementation Rules**:
    1.  **Seed Lock**: Ensure `numpy.random.seed(42)` is set at the start of the script to guarantee consistent daily noise across runs.
    2.  **Uniform Date Filter**: Generate all tables (inventory, SCADA logs, PPA billing) to share the exact same start (`2023-06-01`) and end (`2026-06-08`) dates.
    3.  **Out-of-Bounds Trigger**: On `2024-08-15` (lightning strike), instantly force `discharge_rate_c` to spikes above `1.8` for a 4-hour window to trigger the operational exception logs.
