# Visualization Selection Guide

Select visuals based on **cognitive suitability** — what helps a decision-maker understand the insight fastest. Not aesthetics.

## Chart Selection Matrix

| Analytical Purpose              | Recommended Chart Type     | When to Use                                                  |
| ------------------------------- | -------------------------- | ------------------------------------------------------------ |
| Single metric status            | KPI Card                   | Current value, trend arrow, vs-target comparison              |
| Trend over time                 | Line Chart                 | Temporal patterns, seasonality, growth trajectories           |
| Category comparison             | Bar Chart (horizontal)     | Comparing discrete items (products, regions, departments)     |
| Period comparison               | Bar Chart (vertical)       | Comparing time periods (monthly revenue, quarterly costs)     |
| Contribution / waterfall        | Waterfall Chart            | How components add up to a total (profit bridges, cost decomposition) |
| Part-of-whole                   | Stacked Bar / Treemap      | Composition analysis (revenue mix, cost structure)            |
| Risk concentration              | Heatmap                    | Two-dimensional risk mapping (likelihood × impact)            |
| Anomaly detection               | Scatter Plot               | Outlier identification, pattern breaks                        |
| Relationship / correlation      | Bubble Chart               | Three-variable relationship analysis                          |
| Portfolio analysis              | Quadrant Matrix            | Classify items on two axes (BCG matrix, priority matrix)      |
| Root cause decomposition        | Decomposition Tree         | Drill-down from symptom to cause                              |
| Prediction / forecast           | Forecast Chart (line + CI) | Projected values with confidence intervals                    |
| Distribution                    | Histogram / Box Plot       | Data spread, skewness, outlier ranges                         |
| Flow / process                  | Sankey Diagram             | Volume flows between stages (customer journey, cost flow)     |
| Geographic patterns             | Choropleth / Bubble Map    | Location-based performance differences                        |
| Comparison across many metrics  | Radar / Spider Chart       | Multi-dimensional performance profiles                        |
| Exception / alert               | Alert Card (red/amber/green) | Threshold breaches requiring immediate attention            |

## Dashboard Layout Principles

1. **Top row**: KPI cards — 4-6 headline metrics with trend indicators and target comparison.
2. **Second row**: Primary analysis visuals — the charts that answer the dashboard's core management question.
3. **Third row**: Supporting detail — drill-down tables, decomposition views, secondary charts.
4. **Right sidebar** (if applicable): Filters, time range selector, segment selector.
5. **Bottom**: Exception alerts, action items, or links to related dashboards.

## Wireframe Convention

When describing dashboard wireframes in deliverable `12-visualization-architecture.md`, use this format:

```
┌─────────────────────────────────────────────────────────┐
│ Dashboard Title                              [Filters ▾]│
├────────┬────────┬────────┬────────┬────────┬────────────┤
│ KPI-01 │ KPI-02 │ KPI-03 │ KPI-04 │ KPI-05 │  KPI-06   │
├────────────────────────────┬────────────────────────────┤
│   Primary Chart A          │   Primary Chart B          │
│   (type: line chart)       │   (type: waterfall)        │
├────────────────────────────┼────────────────────────────┤
│   Detail Table / Tree      │   Supporting Chart C       │
│   (type: decomposition)    │   (type: heatmap)          │
├────────────────────────────┴────────────────────────────┤
│   Alerts / Exceptions / Action Items                    │
└─────────────────────────────────────────────────────────┘
```

Label each cell with: component ID (VIZ-), chart type, the KPI(s) or ENG- it renders, and the management question it answers.

## Anti-Patterns

- **Pie charts for more than 5 categories** — use horizontal bar instead.
- **3D charts** — never. They distort perception.
- **Dual-axis charts** — avoid unless the two metrics share a clear causal relationship and different scales. Prefer two separate charts.
- **Dashboards with more than 12 visual elements** — cognitive overload. Split into separate dashboards.
- **Decorative visuals** — every chart must answer a specific management question. If you cannot name the question, remove the chart.
- **Default color palettes** — use semantic colours (red = bad, green = good, amber = warning) consistently. Never use colour as the sole differentiator.
