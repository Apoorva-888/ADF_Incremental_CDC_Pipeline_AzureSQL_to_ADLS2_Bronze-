# Project Overview
**Project Name:** ADF Incremental CDC Pipeline AzureSQL → ADLS2 Bronze

**Description:**  
This project implements a metadata-driven, idempotent incremental ingestion pattern using Azure Data Factory (ADF). Data is ingested from Azure SQL Database into ADLS2 Bronze layer in **Parquet format**, using CDC (Change Data Capture) logic to ensure only updated or new rows are processed in each pipeline run.

**Key Features:**  
- Incremental load using CDC column (`updated_at`).  
- CDC tracking via `cdc.json` stored in ADLS2.  
- Parameterized pipeline: supports multiple tables and schemas.  
- Production-ready: idempotent, error-handling, logging-ready.  
- Bronze layer storage in **Parquet format** for analytics efficiency.

**Folder Structure:**  
- `pipelines/` – ADF pipeline JSONs  
- `datasets/` – Source, sink, and CDC datasets  
- `linked_services/` – Azure SQL & ADLS2 linked services  
- `cdc_tracking/` – CDC JSON tracking file  
- `templates/` – ARM templates for deployment  
- `scripts/` – Helper scripts (validation, testing)  
- `docs/` – Documentation and diagrams
