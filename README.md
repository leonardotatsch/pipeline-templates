# pipeline-templates

This repository contains a collection of pipeline templates that can be used to create pipelines in GitHub Actions.

## Usage

To use a pipeline template, create a new file in your repository with the name `.github/workflows/<name>.yml` and add the following content:


### Terraform with Infracost example
```yaml
name: IaC test

on:
  workflow_dispatch:

jobs:
  build:
    uses: leonardotatsch/pipeline-templates/.github/workflows/terraform-plan.yml@main
    with:
      working-directory: <path-to-your-terraform-code>
      terraform-version: <version-of-terraform>
      storage_account_name: <storage-account-name>
      container_name: <container-name>
      tf_file_name: <tf-file-name>
      resource_group_name: <resource-group-name>
      environment: <environment>
      tf_apply: <true|false>
      tf_destroy: <true|false>
      infracost_enabled: <true|false> #Needs to set INFRACOST_API_KEY secret when true
    secrets: #How to create secrets: https://docs.github.com/en/actions/reference/encrypted-secrets
      AZURE_SUBSCRIPTION_ID: "${{ secrets.AZURE_SUBSCRIPTION_ID }}"
      AZURE_TENANT_ID: "${{ secrets.AZURE_TENANT_ID }}"
      AZURE_CLIENT_ID: "${{ secrets.AZURE_CLIENT_ID }}"
      AZURE_CLIENT_SECRET: "${{ secrets.AZURE_CLIENT_SECRET }}"
      INFRACOST_API_KEY: null
```

