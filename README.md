# fhir-bulk-data-to-bigquery

Load data from a FHIR Bulk Data API into a BigQuery DataSet

# Try it

## Preprequisites

* Docker
* Docker Compose
* gcloud, with credentials for a user account or service account configured

# Setup

```
git clone https://github.com/jmandel/fhir-bulk-data-to-bigquery
cd fhir-bulk-data-to-bigquery
docker-compose build
```

Edit `config/servers.json` to add details for any server(s) you want to connect to.


Run the loader, specifying a:

* `--source` matching the name of an entry in your `config/servers.json`
* `--bigquery-dataset` specifying the dataset in which you'll create tables
* `--gcs-bucket` specifying the bucket to which you'll write the data for storage (**Warning**: Existing `.ndjson` files will be deleted from your bucket!)

For example:

```
docker-compose run loader \
  --source smart-bulk-data \
  --bigquery-dataset fhir-org-starter-project:bulk_data_smart_100 \
  --gcs-bucket fhir-bulk-data 
```

