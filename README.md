# Low-code DAG catalogue

This repository contains a catalogue of pipeline resources designed to be highly reusable.

# Catalogue structure

1. Each template is provided in a separate directory containing a pipeline and may have multiple versions. Each resource follows the following structure.

```
./templates

    /el-aws-to-azure            
       /0.1                     👈 version number
         /README.md             👈 instructions on how to use the pipeline template 
         /metadata.yaml         👈 metadata to be replaced in the template
         /template.json.j2      👈 template of the pipeline
       /0.2/...

    /el-azure-to-aws
       /0.1
         /README.md
         /metadata.yaml
         /template.json.j2
```

2. The `metadata.yaml` file is structured as follows.

````yaml
name: el-azure-to-aws           👈 pipeline folder must have same name
version: 0.1                    👈 version folder must have same name
description: Extract data from Azure Blob Storage and load them in AWS S3.
parameters:
  - name: read_path
    type: str
    description: The path of the file to read.
    example: path/to/file
  - name: storage_name
    type: str
    description: The storage name of the Azure Blob storage.
    example: my_storage 
````

The `name`, `description` and `version` fields are mandatory. Each parameter has a name, a type, a description and an example. 

3. Ultimately, the template file is a JSON file. All parameters are replaced with those specified in the `metadata.yaml` file. Below is an example for the `el-azure-to-aws` template.

```json
{
  "id": "dag1",
  "tasks": [
    {
      "id": "task1",
      "type": "read",
      "params": {
        "type": "file",
        "object": {
          "header": true,
          "type": "{{ read_type }}",
          "path": "{{ read_path }}"
        },
        "connector": {
          "type": "azure",
          "options": {
            "storage_name": "{{ storage_name }}",
            "sas_token": "{{ sas_token }}",
            "container": "{{ azure_container }}"
          }
        },
        "structure": {{ data_structure }}
      }
    },
    {
      "id": "task2",
      "type": "write",
      "dependency": ["task1"],
      "params": {
        "type": "file",
        "object": {
          "header": true,
          "type": "{{ write_type }}",
          "path": "{{ write_path }}"
        },
        "connector": {
          "type": "s3",
          "options": {

            "bucket": " {{s3_bucket }}",
            "access_key": "{{ s3_access_key }}",
            "secret_key": "{{ s3_secret_key }}",
          }
        } 
      }
    }
  ]
}
```

<!--
Users can also contribute to the creation of new pipelines if they follow the template.
-->

## Contributors :woman_technologist: :man_technologist:

<a href="https://github.com/graalsystems/catalog/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=graalsystems/catalog" />
</a>