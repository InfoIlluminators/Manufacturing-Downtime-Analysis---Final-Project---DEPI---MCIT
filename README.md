# Manufacturing Downtime Analysis Project

**Organization:** Digital Egypt Pioneers Initiative (DEPI)

**Team:** InfoVerse Team

**Tools:** Microsoft Power BI, Figma, Excel

## Project Overview {#project-overview}

The **Manufacturing Downtime Analysis** project is a Business
Intelligence solution designed to analyze production line efficiency,
downtime patterns, and operator performance. Utilizing **Power BI**,
this system transforms raw manufacturing data into actionable insights
to improve operational effectiveness.

The primary goal was to identify the root causes of downtime---ranging
from mechanical failures to operator errors---and provide a data-driven
foundation for increasing production efficiency by an estimated
**5-10%**.

### Objectives {#objectives}

- **Increase Production Efficiency:** Minimize downtime and optimize
  > batch operations.

- **Root Cause Analysis:** Identify key factors contributing to machine
  > failure and delays using Fishbone/Ishikawa analysis.

- **Performance Evaluation:** Assess operator performance to guide
  > targeted training and resource planning.

- **Visualization:** Provide actionable dashboards for real-time
  > visibility across shifts, products, and time periods.

## The InfoVerse Team {#the-infoverse-team}

| **Team Member**        | **Role**         |
|------------------------|------------------|
| **AlHussein AlAttar**  | Project Lead     |
| **Mohammed AlMukadam** | Business Analyst |
| **Youssef Ezzat**      | Data Analyst     |
| **Youssif Ali**        | UI/UX Designer   |
| **Mina Ayad**          | Storyteller      |

## Technical Architecture {#technical-architecture}

### 1. Data Sources & ETL (Power Query) {#data-sources-etl-power-query}

The raw data was sourced from Manufacturing_Line_Productivity.xlsx and
processed using Power Query to ensure data integrity. Key transformation
steps included:

- **Data Cleaning:** Removing irrelevant columns, handling missing
  > values, and converting data types.

- **Unpivoting:** Transforming wide-format downtime factor columns into
  > a normalized format (factLineDowntime).

- **Standardization:** Cleaning product sizes (e.g., converting \"2 L\"
  > to 2000 ml) and standardizing operator names.

- **Time Dimension:** Generating a dynamic dimDate table and a granule
  > TimeTable (minute-by-minute) for shift analysis.

### 2. Data Modeling (Star Schema) {#data-modeling-star-schema}

The data model follows a Star Schema design optimized for performance
and analysis.

- **Fact Tables:**

  - factLineProductivity: Stores production event data (Batch, Duration,
    > Operator).

  - factLineDowntime: Captures specific downtime incidents and
    > durations.

- **Dimension Tables:**

  - dimProducts: Product attributes (Flavor, Size, Target Batch Time).

  - dimOperatorName: Operator details.

  - dimDowntimeFactors: Downtime reasons (Machine Failure, Inventory
    > Shortage, etc.) and Operator Error flags.

  - dimDate & TimeTable: For temporal analysis.

### 3. Key DAX Measures {#key-dax-measures}

Complex DAX calculations were implemented to derive critical KPIs,
including:

- **Overall Production Efficiency:** DIVIDE(\[Total Productive Time\],
  > \[Total Production Time\], 0)

- **% Batches Meeting Target:** Calculates adherence to target batch
  > times defined in dimProducts.

- **Total Downtime (Formatted):** Converts raw minutes into readable
  > \"Hours & Mins\" string formats.

- **Operator Specific Metrics:** Measures to isolate downtime
  > contribution by specific operators (e.g., Downtime for Charlie).

## Dashboard Insights {#dashboard-insights}

The Power BI report is divided into three analytical views:

### Page 1: Overview Analysis

- **Efficiency Baseline:** The production line operates at **64.02%
  > efficiency**.

- **Downtime Impact:** \~36% of total production time (approx. 23 hours)
  > is lost to downtime.

- **Top Offenders:**

  - **Top Product:** CO-600 contributes most to downtime.

  - **Top Factor:** Machine Adjustment is the primary cause of
    > stoppages.

- **Trends:** Monday sees the highest downtime usage, while Tuesday is
  > the most efficient day.

### Page 2: Batch Analysis

- **Target Adherence:** Only **7.89%** of batches meet their target
  > production times.

- **Correlation:** A strong linear relationship exists between batch
  > duration and downtime; longer batches are almost exclusively caused
  > by stoppages rather than slow running speeds.

- **Primary Bottlenecks:** Machine Adjustment (332 mins), Machine
  > Failure (254 mins), and Inventory Shortage (225 mins).

### Page 3: Operator Analysis

- **Operator Performance:**

  - **Least Efficient:** Charlie (Night Shift) and Dee (Day Shift).

  - **Most Efficient:** Dennis and Mac (Rotational Shifts).

- **Human Error:** **55.91%** of all downtime is linked to operator
  > error.

- **Shift Patterns:** Fixed-shift operators (Day-only or Night-only)
  > struggle more than rotational staff, specifically with machine
  > adjustments on the CO-600 line.

## Recommendations {#recommendations}

Based on the data analysis, the following actions were recommended to
the stakeholders:

1.  **Targeted Training:** Immediate retraining for operators Charlie
    > and Dee, focusing on \"Machine Adjustment\" procedures for product
    > CO-600.

2.  **SOP Optimization:** Create a standardized checklist for machine
    > adjustments to reduce the 332 minutes of lost time.

3.  **Supply Chain Investigation:** Address the \"Inventory Shortage\"
    > issue (3rd largest downtime cause) to ensure raw materials are
    > restocked efficiently to the line.

## Tools & Technologies {#tools-technologies}

- **Power BI Desktop:** Data ingestion, modeling, DAX, and
  > visualization.

- **Power Query (M):** ETL processes.

- **Figma:** UI/UX Wireframing.

- **Microsoft Excel:** Raw data source.

## How to Run {#how-to-run}

1.  Clone this repository.

2.  Ensure you have **Microsoft Power BI Desktop** installed.

3.  Open the .pbix file included in the repository.

4.  (Optional) If data sources are static, update the Data Source
    > Settings to point to the local Excel file
    > Manufacturing_Line_Productivity.xlsx.

*Copyright © 2025 InfoVerse Team - Digital Egypt Pioneers Initiative*
