# Azure Healthcare RCM Pipeline
This project implements an end-to-end data pipeline for processing healthcare Revenue Cycle Management (RCM) data. It ingests, cleans, transforms, and aggregates patient and claims data to produce analytics-ready datasets.
The pipeline follows the Medallion architecture (Bronze → Silver → Gold) and is built entirely on Azure services with Python and PySpark for transformations.

# Project Overview
The Azure Healthcare RCM Pipeline simulates a real-world healthcare data engineering workflow. It ingests patient, billing, and claims data from multiple hospital databases, APIs, and flat files into Azure Data Lake Storage. The data then flows through Databricks transformations and is curated for analytics in Synapse and Power BI. This project highlights key Azure components for secure, scalable data engineering, from ingestion to reporting and aligned with HIPAA-compliant design practices.   

# Features
1. **Multi-Source Ingestion**: Pulls healthcare data from MySQL, Azure SQL, flat files, and REST APIs (ICD codes).
2. **Layered Data Processing**: Implements Bronze (raw), Silver (cleaned), and Gold (aggregated) data layers using Delta Lake.
3. **ETL Orchestration**: Uses Azure Data Factory pipelines for ingestion and transformation scheduling.
4. **Secure Storage**: Stores all data in Azure Data Lake Storage Gen2 with managed access through Azure Key Vault and Entra ID.
5. **Data Transformation**: Performs cleaning, joins, and aggregations in Databricks notebooks using PySpark.
6. **Data Warehouse & Reporting**: Publishes curated data to Synapse Analytics and Power BI for business reporting.
7. **Scalable & Governed**: Designed with modularity, role-based access, and future scalability in mind.

# Tech Stack
- **Azure Data Factory** – Orchestration and data movement
- **Azure Data Lake Storage Gen2 (ADLS)** – Centralized storage
- **Azure Databricks** – Data cleaning, transformation, and aggregation using PySpark
- **Delta Lake** – Reliable data management and ACID transactions
- **Azure Synapse Analytics** – Data warehouse and query layer
- **Power BI** – Visualization and reporting
- **Azure Key Vault** – Secure secret and credential management
- **Azure Entra ID (AD)** – Authentication and access control  

# How It Works
1. **Ingestion**:
   - Azure Data Factory connects to hospital EMR databases (MySQL, Azure SQL), flat files, and REST APIs.
   - Raw data is ingested into the Bronze Layer in ADLS.
2. **Transformation**:
   - Databricks reads Bronze data and applies cleaning, validation, and enrichment steps.
   - The processed data is written to the Silver Layer (structured and cleaned).
3. **Aggregation**:
   - Databricks computes business-level KPIs like claim approval rates, reimbursement totals, and patient visit metrics.
   - These outputs are stored in the Gold Layer (aggregated tables).
4. **Analytics & Reporting**:
   - Synapse Analytics queries the Gold data layer.
   - Power BI dashboards visualize claim trends, revenue leakage, and operational insights.
   
# Required Libraries (Databricks)
- pyspark
- delta
- pandas
- azure-storage-blob
- requests

# Execution Flow
1. Trigger ADF pipeline to load data from source systems to ADLS (Bronze).
2. Run Databricks notebooks for data cleansing and enrichment (Silver).
3. Generate business aggregates and KPIs (Gold).
4. Load curated data into Synapse for analytical queries.
5. Build Power BI reports for end-user visualization.

# Key Outputs
1. **Bronze Laye**r: Raw patient, claim, and ICD data.
2. **Silver Layer**: Cleaned and standardized data ready for analytics.
3. **Gold Layer**: Business metrics for RCM performance and financial insights.
4. **Power BI Dashboards**: Claim turnaround time, denied claims, top revenue departments.

# Security & Governance
1. **Azure Key Vault**: Stores credentials and connection strings securely.
2. **Azure Entra ID**: Manages role-based access and authentication.
3. **ADLS Gen2 ACLs**: Fine-grained access control for data layers.
