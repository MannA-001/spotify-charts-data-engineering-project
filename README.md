# Spotify Data Engineering Pipeline

## Overview
This project demonstrates an end-to-end data engineering pipeline built on Azure using Spotify streaming data. The goal is to ingest raw data, transform it through multiple layers, and make analytics-ready datasets available for Power BI reporting.

The project follows the Medallion Architecture:
Bronze → Silver → Gold.

---

## Architecture

Data Source (Kaggle CSV)
→ Azure Data Lake Storage Gen2
→ Azure Databricks (Bronze, Silver, Gold layers)
→ Delta Tables
→ Power BI Dashboard

---

## Technologies Used

- Azure Data Lake Storage Gen2
- Azure Databricks
- Delta Lake
- Spark SQL
- Power BI
- GitHub

---

## Bronze Layer (Raw Data)

Purpose:
- Store raw Spotify chart data
- Minimal transformation

Steps:
- Read CSV files from ADLS
- Infer schema
- Store data in Delta format

---

## Silver Layer (Cleaned Data)

Purpose:
- Clean and standardize data for analytics

Transformations:
- Standardized column names
- Data type corrections
- Null handling
- Deduplication

Output:
- Delta table: spotify_silver

---

## Gold Layer (Analytics Ready)

Purpose:
- Create business-level aggregates for reporting

Gold Tables:
- spotify_gold_daily_region
- spotify_gold_chart_trends
- spotify_gold_top_tracks
- spotify_gold_top_artists

These tables are used directly in Power BI.

---

## Power BI Dashboard

The Power BI dashboard connects directly to Databricks and visualizes:
- Daily streaming trends by region
- Top tracks by total streams
- Interactive region-based filtering

---

## Key Learnings

- Implemented Medallion Architecture
- Built BI-ready Delta tables
- Integrated Databricks with Power BI
- Designed analytics-focused data models

---

## Author

Sayan Manna
