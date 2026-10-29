
# Suez Canal Disruption: Analyzing the Impact on Global Maritime Logistics

## Project Description

In March 2021, the *Ever Given* container ship blocked the Suez Canal for six days, disrupting a major global shipping route. This project investigates the impact of the disruption on maritime cargo movements and terminal efficiency during Q1 2021, examining changes in cargo volumes, regional differences, and the time required for operations to recover.

## Business Problem

The Suez Canal blockage disrupted global maritime transportation, potentially affecting cargo movements, port operations, and shipping schedules. Maritime logistics stakeholders need to understand the extent of the disruption, which regional hubs experienced the greatest impact, and how quickly operations recovered.

Using the available maritime dataset, this analysis aims to identify the disruption's footprint and assess its implications for cargo movement and operational efficiency.

## Project Objectives

1. **Identify the disruption:** Determine when the impact of the Suez Canal blockage becomes visible in the Q1 2021 data.
2. **Measure cargo movement changes:** Compare cargo volumes before, during, and after the disruption to identify unusual changes and possible recovery patterns.
3. **Compare regional impacts:** Evaluate differences in cargo movements and terminal efficiency across EMEA, APAC, and AMER.
4. **Assess operational recovery:** Estimate how long it took for cargo movements and terminal performance to return to their pre-disruption levels.

## Analytical Questions

1. When does the disruption become visible in the data, and does the timing align with the known incident?
2. Did cargo volumes decline or spike before, during, or after the incident?
3. Which regional hub (EMEA, APAC, or AMER) experienced the greatest change in cargo movements?
4. How did terminal efficiency change during the disruption?
5. How long did it take for cargo movements and terminal efficiency to return to normal?



## Tools and Methodology

### Tools

- **SQL Server:** Exploratory data analysis (EDA), trend analysis, regional comparisons, and calculation of key performance indicators.
- **Power BI:** Data visualization and interactive dashboards for investigating the disruption's impact on cargo movements and terminal efficiency.

### Methodology

1. **Exploratory Data Analysis:** Use SQL to examine cargo movements, terminal performance, date patterns, and regional distributions to understand the dataset and identify potential anomalies.

2. **Disruption Analysis:** Investigate changes in cargo movements and terminal efficiency before, during, and after the Suez Canal blockage in March 2021.

3. **Regional Comparison:** Compare the disruption's observed impact across EMEA, APAC, and AMER to identify differences in cargo movements and terminal performance.

4. **Recovery Analysis:** Establish pre-disruption performance baselines and measure how long cargo movements and terminal efficiency took to return to normal levels.

5. **Data Visualization:** Use Power BI to present trends, regional comparisons, performance indicators, and recovery patterns in an interactive dashboard.


## Dataset Documentation

For details about the dataset, table descriptions, key columns, and relationships, see the [Data Dictionary](docs/data_dictionary.md).

## SQL Exploratory Data Analysis (EDA)

## 1. Measuring the Immediate Impact

Following the Suez Canal disruption, stakeholders need to understand how the incident affected maritime operations, whether performance eventually recovered, and how long that recovery took.

The six-day blockage prevented vessels from passing through the canal, creating a backlog of ships waiting to transit. But how did this disruption translate into longer voyage durations?

To investigate this, I used SQL to calculate the average voyage duration (move duration) for each day of March 2021, to easily spot any unusual delay for in any of the month. 

```sql
SELECT
  r.date_id,
  ROUND(AVG(move_duration/24),2) AS avg_voyage_duration
FROM fact_cargo_movements AS l
INNER JOIN dim_time AS r
ON l.date_id = r.date_id
WHERE fiscal_year =  2021 AND month = 3
GROUP BY r.date_id
```
##Result![Average Movement Duration in March 2021](docs/Output1.JPG)
