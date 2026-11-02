# Global Earthquake Data Pipeline & Analytics

An end-to-end cloud ETL project that transforms raw USGS earthquake data into clean, analytics-ready datasets using **Keboola, Google BigQuery, and Power BI**.

## Project Overview

This project demonstrates a cloud-based data engineering workflow, from extracting public earthquake data to transforming, storing, and visualizing it for analytical insights.

**Project objectives:**
- Extract real-world earthquake data from the USGS public data feed.
- Clean and standardize raw data using SQL.
- Remove duplicate records and handle data type conversions.
- Create daily aggregated earthquake metrics.
- Build a Power BI dashboard to explore earthquake trends and magnitude distribution.

## Architecture

```text
USGS Earthquake Data (CSV)
          |
          v
   KEBOOLA - EXTRACT
      HTTP Source
          |
          v
   Raw Data Storage
          |
          v
   GOOGLE BIGQUERY
   SQL Transformations
          |
          +----------------------+
          |                      |
          v                      v
   CLEAN_EARTHQUAKES    DAILY_EARTHQUAKE_SUMMARY
          |                      |
          +-----------+----------+
                      |
                      v
               POWER BI
             Analytics Dashboard
```

## Technology Stack

| Technology | Purpose |
|---|---|
| USGS Earthquake Feed | Public data source |
| Keboola | Cloud ETL orchestration and data storage |
| Google BigQuery | SQL-based data transformation |
| Power BI Desktop | Data visualization and reporting |
| SQL | Data cleaning, deduplication, and aggregation |

## Data Pipeline

### 1. Extract
- Retrieved monthly earthquake records from the USGS public CSV feed using Keboola HTTP extraction.
- Loaded raw data into Keboola Storage.

### 2. Transform
Executed SQL transformations using Google BigQuery through Keboola.

**CLEAN_EARTHQUAKES**
- Standardized fields and converted data types.
- Removed duplicate earthquake records using `ROW_NUMBER()`.
- Created event dates and magnitude categories.
- Handled missing and invalid values.

**DAILY_EARTHQUAKE_SUMMARY**
- Aggregated earthquake activity by date.
- Calculated total events, average, minimum, and maximum magnitude.
- Counted magnitude 4+ and 5+ events.
- Calculated average depth and distinct locations.

### 3. Analyze
Built a Power BI dashboard featuring:
- Total earthquake count.
- Average and maximum magnitude KPIs.
- Earthquake magnitude category distribution.
- Daily earthquake activity trend.

## Pipeline Outputs

| Output Table | Purpose |
|---|---|
| `CLEAN_EARTHQUAKES` | Cleaned, deduplicated event-level dataset |
| `DAILY_EARTHQUAKE_SUMMARY` | Daily aggregated analytical dataset |

*Recorded output from the project run: 9,832 cleaned earthquake records and 31 daily summary records.*

## Repository Structure

```text
global-earthquake-etl-analytics/
│
├── keboola/
│   ├── earthquake_cleaning.sql
│   └── daily_earthquake_summary.sql
│
├── powerbi/
│   ├── earthquake_dashboard.pbix
│   └── earthquake_dashboard.pdf
│
├── screenshots/
│   ├── powerbi_dashboard.jpg
│   ├── keboola_transformation.jpg
│   ├── clean_earthquakes_output.jpg
│   └── daily_earthquake_summary_output.jpg
│
└── README.md
```

## Key Skills Demonstrated

- Cloud-based ETL development using Keboola.
- HTTP-based data ingestion from a public data source.
- SQL transformations using Google BigQuery.
- Data cleaning, type conversion, and deduplication.
- Data aggregation and preparation of analytics-ready datasets.
- Data visualization using Power BI.

## Future Improvements

- Schedule automated data ingestion and transformations.
- Implement incremental data processing.
- Introduce pipeline monitoring and data quality checks.

## Data Source

[USGS Earthquake Hazards Program – Earthquake Feeds](https://earthquake.usgs.gov/earthquakes/feed/v1.0/csv.php)

---

**Project Focus:** Demonstrating an end-to-end cloud data engineering pipeline, from raw data ingestion to analytics-ready outputs and business intelligence reporting.