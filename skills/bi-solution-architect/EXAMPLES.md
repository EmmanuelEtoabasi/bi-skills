# Worked Examples — Serial Builds in Practice

This document provides a worked example of a company implementing **Path A: Bottom-Up (Operational → Analytical → Strategic)** sequentially, demonstrating how each build is focused but connects across horizons.

---

## 1. Operational Build (Saved to `/operational/`)

**Business Context (`BC-OP-001`)**: The company seeks to monitor and optimize daily inventory stockouts and delivery cycle times.

*   **KPIs Designed**:
    *   `KPI-OP-01` (Days of Inventory): `stock_on_hand / daily_sales_velocity`
    *   `KPI-OP-02` (SLA Breach Rate): `(Delayed Deliveries / Total Deliveries) * 100`
*   **Analytics Engines (`ENG-OP-01`)**: Threshold-based alert engine that triggers when `Days of Inventory` drops below 14 days or `SLA Breach Rate` exceeds 5%.
*   **Deliverables (`DEL-OP-01`)**: Real-time Operational Warehouse Dashboard and Exception Queue.

---

## 2. Analytical Build (Saved to `/analytical/`)

**Business Context (`BC-ANA-001`)**: Building on the completed Operational build, the company wants to diagnose *why* SLA breaches occur and predict which customers are likely to experience delivery failures.

*   **Cross-Horizon Connections**:
    *   This build references `KPI-OP-02` (SLA Breach Rate) from the Operational build directory as the primary target variable for diagnostic analysis.
    *   It references `DA-001` (POS receipt log) and `DA-004` (delivery logs) established during the operational data setup.
*   **KPIs Designed**:
    *   `KPI-ANA-01` (Delivery Delay Variance): `Actual transit duration - Scheduled transit duration`
    *   `KPI-ANA-02` (Customer Churn Risk Score): Probability index calculated from late delivery cohorts.
*   **Analytics Engines (`ENG-ANA-01`)**: Diagnostic Regression Engine that correlates `KPI-ANA-01` against route distance, traffic times, and driver experience to identify primary bottleneck factors.
*   **Deliverables (`DEL-ANA-01`)**: Route Optimization Analysis Report and Predictive Churn Alert Feed.

---

## 3. Strategic Build (Saved to `/strategic/`)

**Business Context (`BC-STR-001`)**: With operational monitoring and analytical diagnosis active, the executive team plans a 3-year warehousing and supply chain expansion to reduce overall transport costs and improve market share.

*   **Cross-Horizon Connections**:
    *   This build references the diagnostic findings from the Analytical build (`ENG-ANA-01`), which proved that distant regional deliveries drive 80% of SLA breaches.
    *   It uses `KPI-OP-01` (Days of Inventory) to estimate capital costs for proposed new warehouse regions.
*   **KPIs Designed**:
    *   `KPI-STR-01` (Net Present Value - NPV): Estimated capital return of proposed warehouse locations.
    *   `KPI-STR-02` (Market Share Index): Regional customer acquisition rates.
*   **Analytics Engines (`ENG-STR-01`)**: Scenario Simulation Engine that models transport cost reductions under different warehouse layout designs.
*   **Deliverables (`DEL-STR-01`)**: Executive Scorecard and Warehouse Siting Prioritization Model.

---

## 4. Master Path Register (`path-definition.md`)

Once all three builds are complete, the master register at the root of `architecture_docs/` records the full serial layout:

```markdown
# Path Definition Register

*   **Pathway**: Path A: Bottom-Up (Operational → Analytical → Strategic)
*   **Status**:
    *   `[x]` Operational Build: Complete (Saved to `./operational/`)
    *   `[x]` Analytical Build: Complete (Saved to `./analytical/`)
    *   `[x]` Strategic Build: Complete (Saved to `./strategic/`)

## Shared Data Assets
*   `DA-001`: POS Transactions (used by Operational & Analytical)
*   `DA-002`: QuickBooks Financials (used by Strategic & Operational)
*   `DA-004`: Site Delivery Logs (used by Analytical & Operational)
```
