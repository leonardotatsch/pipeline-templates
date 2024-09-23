# pipeline-templates

This repository contains a collection of pipeline templates that can be used to create pipelines in GitHub Actions.

## Usage

To use a pipeline template, create a new file in your repository with the name `.github/workflows/<name>.yml` and add the following content:


### Terraform with Infracost example
```yaml
on: [push]

jobs:
  build:
    steps:
      - uses: leonardotatsch/pipeline-templates/<name>@main
        with:
          terraform_version: '1.0.0'
          infracost_enabled: true
          working_directory: '.'
```

