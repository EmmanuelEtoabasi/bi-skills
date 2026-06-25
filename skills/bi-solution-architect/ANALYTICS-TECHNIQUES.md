# Business Analytics Techniques Taxonomy

This document is the standard reference list of business analytics techniques. When designing KPIs, Analytics Engines, and Intelligence Layers, the architect and design agents must select from this taxonomy to specify the requisite analytical techniques.

## Core Questions and Analytics Types

Business Analytics techniques can be broadly classified by the core question they answer:

| Analytics Type         | Core Question                                      |
| ---------------------- | -------------------------------------------------- |
| Descriptive Analytics  | What happened?                                     |
| Diagnostic Analytics   | Why did it happen?                                 |
| Predictive Analytics   | What is likely to happen?                          |
| Prescriptive Analytics | What should we do?                                 |
| Cognitive/AI Analytics | What can the system learn or decide automatically? |

---

# 1. Descriptive Analytics Techniques

**Purpose:** Summarize historical data.

## A. Basic Statistical Analysis
* Mean
* Median
* Mode
* Range
* Variance
* Standard Deviation
* Percentiles
* Quartiles
* Frequency Distribution

## B. KPI Analysis
* Revenue Analysis
* Profitability Analysis
* Customer Growth Analysis
* Churn Analysis
* Conversion Analysis
* Productivity Analysis
* Operational Efficiency Analysis

## C. Aggregation Techniques
* Summarization
* Group By Analysis
* Cross-tabulation
* Pivot Tables
* OLAP Cubes
* Drill Down Analysis
* Roll Up Analysis

## D. Trend Analysis
* Time Trend Analysis
* Growth Rate Analysis
* Moving Average Analysis
* Seasonal Trend Analysis
* Comparative Period Analysis

## E. Visualization Techniques
* Bar Charts
* Line Charts
* Pie Charts
* Area Charts
* Histograms
* Heat Maps
* Geographic Maps
* Dashboards
* Scorecards

---

# 2. Diagnostic Analytics Techniques

**Purpose:** Identify causes and relationships.

## A. Root Cause Analysis
* 5 Whys
* Fishbone Diagram
* Cause-and-Effect Analysis
* Fault Tree Analysis
* Pareto Analysis

## B. Correlation Analysis
* Pearson Correlation
* Spearman Correlation
* Kendall Correlation
* Cross-Correlation

## C. Variance Analysis
* Budget vs Actual Analysis
* Forecast vs Actual Analysis
* Performance Variance Analysis

## D. Comparative Analysis
* Benchmarking
* Cohort Analysis
* Segment Analysis
* Gap Analysis

## E. Statistical Testing
* T-Test
* Z-Test
* Chi-Square Test
* ANOVA
* MANOVA
* Hypothesis Testing

## F. Contribution Analysis
* Revenue Driver Analysis
* Cost Driver Analysis
* Margin Analysis
* Product Mix Analysis

---

# 3. Predictive Analytics Techniques

**Purpose:** Estimate future outcomes.

## A. Regression Models
* Linear Regression
* Multiple Regression
* Polynomial Regression
* Logistic Regression
* Ridge Regression
* Lasso Regression
* Elastic Net Regression

## B. Time Series Forecasting
* Moving Average
* Exponential Smoothing
* Holt-Winters
* ARIMA
* SARIMA
* Prophet
* VAR Models

## C. Classification Models
* Decision Trees
* Random Forest
* Gradient Boosting
* XGBoost
* LightGBM
* CatBoost
* Naive Bayes
* Support Vector Machines

## D. Survival Analysis
* Kaplan-Meier
* Cox Regression
* Hazard Models

## E. Demand Forecasting
* Sales Forecasting
* Inventory Forecasting
* Workforce Forecasting
* Cash Flow Forecasting

## F. Risk Prediction
* Credit Risk Models
* Fraud Prediction Models
* Default Prediction Models
* Churn Prediction Models

---

# 4. Prescriptive Analytics Techniques

**Purpose:** Recommend actions.

## A. Optimization
* Linear Programming
* Integer Programming
* Mixed Integer Programming
* Goal Programming
* Dynamic Programming

## B. Resource Allocation
* Workforce Scheduling
* Budget Optimization
* Capacity Planning
* Inventory Optimization

## C. Simulation
* Monte Carlo Simulation
* Discrete Event Simulation
* System Dynamics Simulation
* Agent-Based Modeling

## D. Decision Analysis
* Decision Trees
* Utility Theory
* Cost-Benefit Analysis
* Scenario Analysis
* What-If Analysis

## E. Recommendation Systems
* Collaborative Filtering
* Content-Based Filtering
* Hybrid Recommenders

---

# 5. Machine Learning Analytics

**Purpose:** Discover patterns automatically.

## A. Supervised Learning
* Regression Models
* Classification Models
* Ensemble Models

## B. Unsupervised Learning
* K-Means Clustering
* Hierarchical Clustering
* DBSCAN
* Gaussian Mixture Models

## C. Semi-Supervised Learning
* Label Propagation
* Self-Training

## D. Reinforcement Learning
* Q-Learning
* Deep Q Networks
* Policy Optimization

---

# 6. Data Mining Techniques

## A. Association Analysis
* Market Basket Analysis
* Apriori Algorithm
* FP-Growth

## B. Clustering
* Customer Segmentation
* Product Segmentation
* Geographic Segmentation

## C. Pattern Discovery
* Sequential Pattern Mining
* Frequent Pattern Mining

## D. Anomaly Detection
* Outlier Detection
* Fraud Detection
* Network Intrusion Detection

---

# 7. Customer Analytics Techniques

## Customer Segmentation
* Demographic Segmentation
* Geographic Segmentation
* Behavioral Segmentation
* Psychographic Segmentation

## Customer Value Analysis
* RFM Analysis
* Customer Lifetime Value (CLV)
* Loyalty Analysis

## Customer Behavior Analysis
* Journey Analytics
* Funnel Analytics
* Retention Analysis
* Churn Analysis

## Voice of Customer Analytics
* Sentiment Analysis
* Survey Analysis
* Text Mining

---

# 8. Financial Analytics Techniques

## Profitability Analytics
* Gross Margin Analysis
* Net Margin Analysis
* EBITDA Analysis

## Investment Analytics
* ROI Analysis
* NPV Analysis
* IRR Analysis
* Payback Period Analysis

## Risk Analytics
* Value at Risk (VaR)
* Stress Testing
* Scenario Testing

## Working Capital Analytics
* Cash Conversion Cycle
* Liquidity Analysis
* Solvency Analysis

---

# 9. Operations Analytics Techniques

## Process Analytics
* Process Mining
* Bottleneck Analysis
* Throughput Analysis

## Quality Analytics
* Six Sigma
* Statistical Process Control
* Control Charts
* Capability Analysis

## Supply Chain Analytics
* Inventory Analysis
* Logistics Optimization
* Route Optimization
* Procurement Analytics

---

# 10. Marketing Analytics Techniques

## Acquisition Analytics
* Lead Scoring
* Campaign Attribution
* CAC Analysis

## Conversion Analytics
* Funnel Analysis
* Conversion Rate Optimization

## Campaign Analytics
* A/B Testing
* Multivariate Testing
* Uplift Modeling

## Brand Analytics
* Share of Voice Analysis
* Brand Sentiment Analysis
* Competitive Intelligence

---

# 11. Human Resource Analytics

## Workforce Analytics
* Headcount Analysis
* Turnover Analysis
* Retention Analysis

## Performance Analytics
* Productivity Analysis
* Performance Scoring
* Skills Gap Analysis

## Talent Analytics
* Recruitment Funnel Analytics
* Candidate Scoring
* Succession Planning

---

# 12. Strategic Analytics Techniques

## Portfolio Analytics
* BCG Matrix
* GE-McKinsey Matrix

## Competitive Analytics
* SWOT Analysis
* PESTLE Analysis
* Porter's Five Forces

## Growth Analytics
* Market Share Analysis
* Market Penetration Analysis
* Product Expansion Analysis

---

# 13. AI-Powered Analytics

## Natural Language Analytics
* Sentiment Analysis
* Topic Modeling
* Entity Extraction
* Document Classification

## Generative Analytics
* Scenario Generation
* Forecast Narrative Generation
* Automated Insight Generation

## Knowledge Analytics
* Knowledge Graph Analysis
* Semantic Search Analytics

---

# Enterprise Analytics Pillars

At an enterprise BI level, almost every analytics technique maps into one of seven major pillars. These pillars are critical for categorizing dashboard features, reporting engines, and alert configurations:

1. **Reporting Analytics** (Dashboards, KPIs, Scorecards)
2. **Exploratory Analytics** (Drill-down, Slice-and-Dice, Segmentation)
3. **Diagnostic Analytics** (Root Cause, Correlation, Variance)
4. **Predictive Analytics** (Forecasting, Machine Learning)
5. **Prescriptive Analytics** (Optimization, Simulation)
6. **Monitoring Analytics** (Alerts, Exception Detection, Real-Time Analytics)
7. **Decision Intelligence** (AI, Recommendations, Automated Decisions)
