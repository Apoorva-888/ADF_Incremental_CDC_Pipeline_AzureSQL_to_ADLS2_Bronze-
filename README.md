# ADF Incremental CDC Pipeline – Azure SQL to ADLS2 (Bronze Layer)
Implements a metadata-driven, idempotent incremental data ingestion pattern using Azure Data Factory (ADF) to copy updated/new records from Azure SQL Database into ADLS2.
## Overview
This project implements a metadata-driven and idempotent incremental data ingestion pattern using Azure Data Factory (ADF).
The pipeline extracts only new and updated records from Azure SQL Database using a watermark-based CDC strategy and loads them into Azure Data Lake Storage Gen2 (ADLS2) Bronze layer .

### Architecture
- Source: Azure SQL Database  
- Orchestration: Azure Data Factory  
- Target: ADLS Gen2 (Bronze Layer)  
- Format: Parquet  
- Load Strategy: Incremental (Watermark-based CDC)
### Key Features
- Metadata-driven configuration
- Dynamic query generation
- Parameterized datasets
- Idempotent execution (safe re-runs)
- Optimized Parquet storage for analytics workloads
### Incremental Load Flow
  1. Read last processed watermark value.
  2. Extract only records greater than the watermark.
  3. Write data to ADLS2 in Parquet format.
  4. Update watermark after successful load.
This ensures efficient processing and prevents duplicate ingestion.

### Project Structure
```
ADF_Incremental_CDC_Pipeline_AzureSQL_to_ADLS2_Bronze/
├── 1_pipelines/
│   └── p1_incremental_ingestion_bronze.json
│
├── 2_datasets/
│   ├── dataset_azuresql.json
│   ├── dataset_json_dynamic_adls2.json
│   └── parquet_dynamic_adls2.json
│
├── 3_linked_services/
│   ├── ls_adls2.json
│   └── ls_sqldatabase.json
│
├── 4_docs/
│   ├── 01_project_overview.md
│   ├── 02_pipeline_activities.md
│   ├── 03_incremental_cdc_concept.md
│   ├── 04_dataset_and_linkedservices.md
│   ├── 05_json_usage_and_best_practices.md
│   ├── 06_production_readiness.md
│   ├── 07_code_snippets.md
│   └── architecture_diagram.png
│
└── 5_activity_visuals/
    ├── copy_azureSQL_to_adls2_output.png
    ├── p1_incremental_ingestion_bronze.png
    └── p1_incremental_ingestion_bronze_without_if_condition.png
```

### Why This Approach?
- Avoids full table reloads
- Reduces compute and storage cost
- Scales across multiple tables
- Forms the foundation for Silver and Gold transformations

## Outcome
A production-ready incremental ingestion framework aligned with enterprise Azure data platform standards.
