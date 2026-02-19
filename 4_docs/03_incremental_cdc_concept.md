# Incremental CDC Concept

**Purpose:**  
- To avoid full table reloads every run.  
- To ensure **idempotent and efficient incremental ingestion**.

**Concept Flow:**  
1. Read the last processed CDC timestamp from `cdc.json`.  
2. Filter SQL source using CDC column > last processed timestamp.  
3. Copy new/updated data into ADLS2 Bronze layer.  
4. Calculate maximum CDC value post-load.  
5. Update `cdc.json` for the next pipeline execution.

**Benefits:**  
- Reduces data transfer and compute cost.  
- Ensures no duplicate or missed records.  
- Production-ready for high-volume tables.
