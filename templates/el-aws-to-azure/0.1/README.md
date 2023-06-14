# AWS TO AZURE
> This template uploads a file from AWS S3 to Azure Blob Storage.

## Parameters

Here is the list of parameters to set.
- `data_structure`: The schema of the data to extract.
- `read_type`: The type of the file to read.
- `read_path`: The path of the file to read.
- `s3_bucket`: The name of the S3 Bucket where the data is located.
- `s3_access_key`: The S3 Bucket access key.
- `s3_secret_key`: The S3 Bucket secret key.
- `write_type`: The type to write the result in.
- `write_path`: The path of the result file.
- `storage_name`: The storage name of the Azure Blob storage.
- `sas_token`: The SAS Token to access the storage.
- `azure_container`: The container name of the Blob Storage.

