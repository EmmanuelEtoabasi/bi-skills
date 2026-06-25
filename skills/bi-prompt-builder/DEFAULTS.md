# Industry Lookup Templates — bi-prompt-builder

This file provides highly relevant, specific business and technical defaults for various industries. When a user provides their company's industry, the prompt builder references these templates to propose pre-filled defaults.

---

## 1. Renewable Energy & Contracting (e.g. Solar)

*   **Operating Model**: Engineering, procurement, and contracting (EPC) for solar/wind systems, wholesale equipment supply, and showroom retail.
*   **Revenue Mix**: 35% Showroom Sales, 30% wholesale/Procurement, 35% Custom Installation Projects.
*   **Scale**: 1 central depot, 3 showroom outlets, 5 active project sites, 50-100 employees.
*   **Path Choice**: Path A: Bottom-Up (Operational → Analytical → Strategic)
*   **Active Horizon Build**: Operational
*   **Data Sources**: POS database, Excel site supervisor checklists, QuickBooks ERP, logistics partner API.
*   **Target Analytics Stack**: DuckDB (Warehouse), dbt Core (Transformation), Flask (API/Backend), Power BI Desktop (Visualizations).
*   **Decision Makers**: Site Supervisors (operational), Supply Chain Analyst (analytical), Business Owner (strategic).
*   **Adoption Goals**: Eliminate manual site-expenditure checklists, reduce equipment stockouts, automate project variance alerts.

---

## 2. Retail & E-commerce

*   **Operating Model**: Multi-channel consumer goods sales (online Shopify store and brick-and-mortar storefronts).
*   **Revenue Mix**: 60% Online Web Sales, 40% Showroom/POS Sales.
*   **Scale**: 1 e-commerce store, 4 retail showrooms, 1 central fulfillment warehouse, 40 employees.
*   **Path Choice**: Path A: Bottom-Up (Operational → Analytical → Strategic)
*   **Active Horizon Build**: Operational
*   **Data Sources**: Shopify API, SQLite POS database, Google Analytics, inventory system logs.
*   **Target Analytics Stack**: MotherDuck/DuckDB (Warehouse), dbt Core (Transformation), Metabase (Visualizations).
*   **Decision Makers**: Store Managers (operational), Marketing Analyst (analytical), CEO/Owner (strategic).
*   **Adoption Goals**: Monitor daily checkout failures, automate warehouse low-stock alerts, track customer lifetime value (LTV).

---

## 3. Logistics & Warehousing

*   **Operating Model**: B2B third-party logistics (3PL), freight transportation, and multi-depot storage management.
*   **Revenue Mix**: 50% Long-haul Freight, 30% Warehouse Storage Fees, 20% Last-mile Delivery.
*   **Scale**: 3 central warehouses, 45 delivery trucks, 15 regional depots, 120 employees.
*   **Path Choice**: Path A: Bottom-Up (Operational → Analytical → Strategic)
*   **Active Horizon Build**: Operational
*   **Data Sources**: Fleet GPS tracking API, Warehouse Management System (WMS) database, driver spreadsheets.
*   **Target Analytics Stack**: DuckDB (Warehouse), dbt Core (Transformation), Apache Superset (Visualizations).
*   **Decision Makers**: Fleet Dispatchers (operational), Logistics Analyst (analytical), VP of Operations (strategic).
*   **Adoption Goals**: Track daily delivery SLA breaches, minimize fuel consumption variances, optimize truck load factors.

---

## 4. SaaS (Software as a Service)

*   **Operating Model**: B2B cloud software subscriptions with tiered plans, enterprise contracts, and professional services.
*   **Revenue Mix**: 70% Monthly Recurring Revenue (MRR), 20% Enterprise Custom Plans, 10% Professional Services.
*   **Scale**: 1 global cloud application, 15,000 active monthly users, 45 employees.
*   **Path Choice**: Path B: Top-Down (Strategic → Operational → Analytical)
*   **Active Horizon Build**: Strategic
*   **Data Sources**: Stripe billing API, Salesforce CRM, PostgreSQL production DB, Segment event streams.
*   **Target Analytics Stack**: Snowflake/DuckDB (Warehouse), dbt Core (Transformation), Lightdash (Visualizations).
*   **Decision Makers**: Customer Success Leads (operational), Product Analyst (analytical), CFO/VP of Product (strategic).
*   **Adoption Goals**: Monitor churn rates, track trial-to-paid conversion rates, measure customer acquisition cost (CAC) payback period.

---

## 5. Generic / Default Template (Fallback)

*   **Operating Model**: Traditional product wholesaling and client servicing.
*   **Revenue Mix**: 70% Product Sales, 30% Service Contracts.
*   **Scale**: 1 central office, 1 warehouse, 30 employees.
*   **Path Choice**: Path A: Bottom-Up (Operational → Analytical → Strategic)
*   **Active Horizon Build**: Operational
*   **Data Sources**: QuickBooks/Xero ledger, CRM database, Excel sales spreadsheets.
*   **Target Analytics Stack**: DuckDB (Warehouse), dbt Core (Transformation), Power BI Desktop (Visualizations).
*   **Decision Makers**: Department Managers (operational), Business Analyst (analytical), Owner/General Manager (strategic).
*   **Adoption Goals**: Automate manual weekly excel reporting, track daily gross profit margins.
