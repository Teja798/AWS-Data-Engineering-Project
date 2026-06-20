# End-to-End Azure Databricks Data Pipeline: Medallion Architecture & Dashboarding

This repository contains an end-to-end data engineering pipeline built on AWS Databricks. The pipeline processes both historical full-load data and monthly incremental updates stored in AWS S3. Using the Medallion Architecture, raw data is cleaned, transformed, and denormalised into a single unified analytical table to power a business intelligence dashboard.



## Overview

- Ingest full load and monthly incremental data from S3 into Databricks using an external location configured with a token. [web:6][web:16]
- Process data through Bronze (raw), Silver (cleaned), and Gold (business‑ready) tables. [web:1][web:5][web:13][web:15]
- Denormalize the model into a single wide Gold table for fast dashboard queries. [web:14][web:10][web:15]
- Build a Databricks SQL dashboard on top of the Gold table.

## Data Flow

1. Upload full load and incremental CSV/Parquet files to an S3 bucket.
2. Create a storage credential and external location in Databricks that points to the S3 path. [web:16][web:6]
3. Load data into Bronze tables (full + incremental) with minimal transformations. [web:1][web:13]
4. Clean and standardize data in Silver tables.
5. Join and denormalize data into a single Gold table for reporting. [web:14][web:10][web:15]
6. Create SQL queries and a dashboard directly on the Gold table.


## Key Features

- Handles both initial full load and monthly incremental loads.
- Removes processed incremental files from the source path to avoid double processing.
- Provides a single denormalized table that is easy to use for BI tools and dashboards. [web:14][web:10]

## Requirements

- Databricks Free Edition
- AWS S3 bucket and permissions to read/write from Databricks
- Personal access token or storage credential configured in Databricks to access S3.

## How to Run

1. Configure S3 bucket and external location in Databricks.
2. Import the notebooks into your Databricks workspace.
3. Update database names, schemas, and S3 paths in the notebooks.
4. Run notebooks in order from Bronze → Silver → Gold.
5. Use the Gold table to build or refresh the dashboard.
