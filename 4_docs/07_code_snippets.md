

### 1. SQL Query for Incremental Load


```sql
SELECT *
FROM dbo.DimUser
WHERE updated_at > '2025-10-07T19:49:55'
```

### 2. Dynamic SQL Expression in Copy Activity
```json

"sqlReaderQuery": {
    "value": "@concat(
        'SELECT * FROM ', pipeline().parameters.schema, '.', pipeline().parameters.table,
        ' WHERE ', pipeline().parameters.cdc_column,
        ' > ''', activity('lookup_cdc_json').output.value[0].cdc, ''''
    )",
    "type": "Expression"
}

```
