

### 1. SQL Query for Incremental Load


```sql
SELECT *
FROM dbo.DimUser
WHERE updated_at > '2025-10-07T19:49:55'
```

### 2. CDC JSON Structure
```json

[
  { "cdc": "2025-10-07T19:49:55Z" }
]

```
