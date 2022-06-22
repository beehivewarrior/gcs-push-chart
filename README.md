# Push Chart to GCS Bucket

Google Container Storage (GCS) is a service available on the Google Cloud Platform (GCP). GCS Buckets are one method
described by Helm to centrally store Helm Chart Packages. You can read more about this in
the [Helm documentation](https://helm.sh/docs/topics/chart_repository/#google-cloud-storage).

**This action has not been endorsed by Google, its Parent Alphabet, or any related entity.**

This action encapsulates the steps needed to push a Helm Chart to a GCS Storage Bucket.

## Features

- Minimal Configuration

## Usage

```yaml
...
steps:
  - uses: actions/checkout@v3

  - name: Package Chart
    shell: bash
    run: |
      helm package ./chart -d ./chart-packages

  - name: Push Chart To Repository
    uses: Bigelow-Systems/gcs-push-chart@v1
    with:
      GCP_CREDENTIALS: ${{ secrets.GCP_CREDENTIALS }}
      GCP_PROJECT_ID: my-project-id
      GCS_BUCKET_NAME: helm-chart-bucket
      PACKAGED_CHART_FOLDER: './chart-packages'
```

## Inputs

|         Input         |   Type   | Required |      Default       |                               Description                                |
|:---------------------:|:--------:|:--------:|:------------------:|:------------------------------------------------------------------------:|
|    GCP_CREDENTIALS    | `string` |   Yes    |                    | Service Account Credentials in JSON format that have been Base64 Encoded |
|    GCP_PROJECT_ID     | `string` |   Yes    |                    |          ID of Project that the GCS bucket is associated with.           |
|    GCP_BUCKET_NAME    | `string` |   Yes    |                    |                          Name of Bucket in GCS                           |
| PACKAGED_CHART_FOLDER | `string` |   Yes    | './chart-packages' |        Name of Folder Where Chart has been prepared and packaged         |

## Outputs

None right now. If you have a use case, you're welcome to contribute.

## License
[MIT License](LICENSE)