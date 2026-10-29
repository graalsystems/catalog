# Low-code pipeline catalog (deprecated)

> **This repository is no longer maintained and is kept for reference only.**
> Its templates move data between AWS S3 and Azure Blob Storage and take storage keys as
> plain parameters. The graal Data Platform now runs on your own infrastructure, reaches
> storage through its connectors and project secrets, and offers its templates from the
> console (and to agents through the MCP tools `list_templates` and `render_template`). See
> [Low-code pipelines](https://graal.systems/en/platform/pipelines).

The catalog held versioned, parameterised low-code pipelines:

```
templates/<name>/<version>/
    README.md          instructions
    metadata.yaml      name, version, description and parameters
    template.json.j2   Jinja template of the pipeline graph
```

| Template | Description |
|---|---|
| `el-aws-to-azure` | Copy a file from AWS S3 to Azure Blob Storage |
| `el-azure-to-aws` | Copy a file from Azure Blob Storage to AWS S3 |
| `aws-drop-azure` | Copy a file from AWS S3 to Azure Blob Storage, dropping columns |
