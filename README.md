# Azure Healthcare RCM Pipeline
This project implements an end-to-end data pipeline for processing healthcare Revenue Cycle Management (RCM) data. It ingests, cleans, transforms, and aggregates patient and claims data to produce analytics-ready datasets.
The pipeline follows the Medallion architecture (Bronze → Silver → Gold) and is built entirely on Azure services with Python and PySpark for transformations. 

# What the Pipeline Does
- Pulls data from MySQL, Azure SQL, flat files, and REST APIs.
- Stores all raw data in Azure Data Lake (Bronze).
- Cleans, validates, and enriches it with PySpark in Databricks (Silver).
- Builds business-ready aggregates and KPIs (Gold).
- Publishes the curated layer to Synapse and Power BI for reporting.

# Core Features
- Multi-source ingestion orchestrated with Azure Data Factory.
- Delta Lake for ACID-compliant storage across all layers.
- Secure design using Key Vault, Entra ID, and ADLS ACLs.
- Modular, scalable structure aligned with real RCM workflows.

# Tech Stack
Azure Data Factory, Azure Databricks, ADLS Gen2, Delta Lake, Synapse Analytics, Power BI, Key Vault, Entra ID.  
Python libraries: pyspark, delta, pandas, azure-storage-blob, requests.

# How It Works
1. **Ingestion**: ADF loads raw EMR, claims, and API data into Bronze in ADLS.
2. **Transformation**: Databricks cleans and structures the data into Silver.
3. **Aggregation**: Gold layer computes RCM metrics like claim approvals, reimbursements, and visit trends.
4. **Analytics**: Synapse queries Gold datasets; Power BI visualizes operational and financial insights.

# Outputs
1. **Bronze**: Raw EMR, claims, CPT, ICD, and NPI data.
2. **Silver**: Cleaned patient, provider, encounter, transaction, CPT, ICD, and NPI tables.
3. **Gold**: Dimensional models and fact tables for RCM analytics.
4. **Power BI Dashboards** for claims and revenue performance.

# Security
- Secrets in Azure Key Vault
- Authentication via Entra ID
- Layer-based access control in ADLS
