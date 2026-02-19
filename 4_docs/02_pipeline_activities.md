# Pipeline Activities

**Pipeline Name:** p1_incremental_ingestion_bronze

**Activities Overview:**

1. **lookup_cdc_json**  
   - Type: Lookup  
   - Reads last processed CDC value (`cdc.json`) from ADLS2.  
   - Ensures incremental load picks only new/updated rows.

2. **current_value**  
   - Type: SetVariable  
   - Stores the current timestamp for tracking and file naming.

3. **copy_azureSQL_to_adls2**  
   - Type: Copy  
   - Source: Azure SQL Database (dynamic table & schema).  
   - Sink: ADLS2 Bronze layer in Parquet format.  
   - Uses CDC column to incrementally copy only new/updated rows.  

4. **If_IncrementalData**  
   - Type: IfCondition  
   - Checks if `dataRead > 0`.  
   - If **false** → deletes empty Parquet file.  
   - If **true** → proceeds to `max_cdc` and `update_last_cdc_value`.

5. **max_cdc**  
   - Type: Script  
   - Finds the maximum CDC column value after the current load.

6. **update_last_cdc_value**  
   - Type: Copy  
   - Updates `cdc.json` in ADLS2 with the latest CDC value for next incremental run.
