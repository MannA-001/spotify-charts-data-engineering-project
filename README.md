# 🎧 Spotify Data Engineering & Analytics Pipeline

##  Project Overview
This project demonstrates an **end-to-end data engineering pipeline** built on **Azure**, using Spotify streaming data.  
The goal is to ingest raw data, transform it through multiple layers using the **Medallion Architecture (Bronze → Silver → Gold)**, and expose **analytics-ready datasets** for reporting in **Power BI**.

The project closely follows **real-world data engineering practices**, where ingestion, transformation, and analytics are handled by different services.

---

## Architecture Overview

- Spotify Dataset (Kaggle)
- Azure Data Factory (ADF)
- Azure Data Lake Storage Gen2 (Bronze)
- Azure Databricks (Silver & Gold)
- Delta Tables (Managed)
- Power BI Dashboard


---

## 🧰 Tech Stack

- **Cloud Platform**: Microsoft Azure
- **Ingestion & Orchestration**: Azure Data Factory (ADF)
- **Storage**: Azure Data Lake Storage Gen2 (ADLS)
- **Processing Engine**: Azure Databricks
- **Storage Format**: Delta Lake
- **Querying & Transformations**: Spark SQL & PySpark
- **Visualization**: Power BI
- **Version Control**: GitHub

---

## 🥉 Bronze Layer — Raw Data Ingestion (ADF)

**Purpose:**
- Ingest raw Spotify chart data
- Preserve data in its original form
- Enable traceability and reprocessing

**Implementation:**
- Azure Data Factory pipeline is used for ingestion
- ADF Copy Activity moves raw CSV data into ADLS Gen2 (Bronze container)
- No transformations are applied at this stage
- Data is stored exactly as received

**Why ADF?**
- Designed for data movement and orchestration
- Decouples ingestion from transformation
- Common industry practice

---

## 🥈 Silver Layer — Cleaned & Standardized Data (Databricks)

**Purpose:**
- Prepare raw data for analytics
- Enforce schema consistency
- Improve data quality

**Key Transformations:**
- Column name standardization
- Data type corrections
- Null handling
- Deduplication
- Basic data validation

**Output:**
- Delta table: `spotify_silver`

All Silver transformations are implemented in **Azure Databricks** using PySpark.

---

## 🥇 Gold Layer — Analytics-Ready Data (Databricks)

**Purpose:**
- Create business-level aggregates
- Provide BI-ready datasets
- Optimize for reporting and performance

**Gold Tables Created:**
- `spotify_gold_daily_region`  
  → Daily total streams by region
- `spotify_gold_chart_trends`  
  → Chart movement trends over time
- `spotify_gold_top_tracks`  
  → Top streamed tracks
- `spotify_gold_top_artists`  
  → Top artists by total streams

**Design Choice:**
- Gold tables are created as **managed Delta tables**
- Optimized for consumption by BI tools
- Simplifies governance and access

---

## 📊 Power BI Dashboard

Power BI connects directly to **Databricks SQL Warehouse** and consumes **Gold-layer Delta tables**.

**Visuals Included:**
- Daily streaming trends by region (line chart)
- Top 10 tracks by total streams (bar chart)
- Interactive region slicer

**Why Gold Tables Only?**
- Gold tables represent stable, curated datasets
- Silver tables remain internal to data engineering workflows
- Aligns with BI best practices

---

## 🔐 Security & Access

- Azure AD–based authentication is used
- No secrets, keys, or credentials are stored in this repository
- Databricks handles secure access to data
- Power BI accesses data via Databricks SQL Warehouse

---

## 🚀 Key Learnings

- Implemented Medallion Architecture in Azure
- Used ADF for ingestion and Databricks for transformations
- Built Delta Lake–based Silver and Gold layers
- Designed BI-ready datasets
- Integrated Databricks with Power BI for analytics

---

 

