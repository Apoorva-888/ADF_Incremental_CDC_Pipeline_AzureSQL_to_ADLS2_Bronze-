# JSON Usage and Best Practices

**Why JSON?**  
- ADF stores pipeline, dataset, and linked service definitions as JSON.  
- Enables **export, version control, and GitHub integration**.  
- JSON format is portable and reusable across environments.

**Best Practices:**  
1. Parameterize pipeline and dataset JSONs for reusability.  
2. Never commit production secrets; use placeholders.  
3. Organize JSONs in clear folders: `pipelines/`, `datasets/`, `linked_services/`.  
4. Use `.gitignore` to exclude runtime files like `cdc.json`.  
5. Maintain ARM templates for automated deployment.
