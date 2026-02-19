# Datasets and Linked Services

**Datasets:**
- `dataset_azuresql` – Parameterized dataset for Azure SQL source tables.  
- `parquet_dynamic_adls2` – Bronze layer sink in Parquet format.  
- `dataset_json_dynamic_adls2` – CDC tracking JSON dataset.

**Linked Services:**
- `ls_azuresql` – Azure SQL Database connection (parameterized).  
- `ls_adls2` – ADLS2 storage connection (URL and credential placeholder).  

**Best Practices:**  
- All sensitive info (credentials, production URLs) are replaced with placeholders in GitHub repo.  
- Datasets are parameterized for schema, table, and CDC column.
