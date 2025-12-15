# U.S. Transportation & Macroeconomic Trends Analyzer

## Overview
The project analyzes 25 years of U.S. transportation data (2000–2025) to quantify how macroeconomic pressures, specifically fuel costs and unemployment, drive the tradeoff between Public Transit usage and Private Vehicle travel. It utilizes an automated ETL pipeline to measure the elasticity of transit demand relative to gas price fluctuations.

---

## Tech Stack
* **Language:** Python (Pandas)
* **Data Extraction:** FRED API (Federal Reserve Economic Data)
* **Automation/CI:** GitHub Actions
* **Visualization:** Microsoft Power BI

---

## Technical Architecture

### 1. Extraction (API Integration)
Python scripts utilize `fredapi` to fetch live historical time-series data. The pipeline targets specific economic indicators over a 25-year period.

### 2. Transformation (Data Engineering)
Raw data is processed to ensure time-series alignment:
* **Aggregation:** Resamples **Weekly** Gas Prices (`GASREGW`) into **Monthly** averages to match the granularity of Transit and Economic metrics.
* **Normalization:** Merges distinct datasets into a single, cohesive master time-series schema ready for analysis.

### 3. Automation (DevOps)
A **GitHub Actions** workflow is to execute the ETL script on a monthly schedule.
* **Benefit:** Enables a "set and forget" data refreshing cycle without manual intervention.
* **Output:** The pipeline automatically pushes updated datasets to the connected storage for Power BI ingestion.

---

## Dashboard & Visualizations
The processed data feeds into a Power BI dashboard featuring:
* **KPIs:** High-level performance metrics and change indicators.
* **Trend Analysis:** Time-series visualizations highlighting correlations between gas prices, economic health and transit ridership.
* **Exploration Controls:** Date slicers allowing for period-based analysis and drill-down capabilities.
