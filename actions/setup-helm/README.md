# Setup Helm

This action sets up [Helm](https://helm.sh/) with optional version configuration.

## Features

- **Version Management**: Install specific versions of Helm

## Usage

### Inputs

| Input          | Description                | Default   | Required |
| -------------- | -------------------------- | --------- | -------- |
| `helm-version` | Version of Helm to install | `v3.17.1` | No       |

### Basic

```yaml
- name: Setup Helm
  uses: moonrise-labs/github-actions/actions/setup-helm@main
```

### Specific Version

```yaml
- name: Setup Helm with specific version
  uses: moonrise-labs/github-actions/actions/setup-helm@main
  with:
    helm-version: v3.15.0
```

## Example Workflow

```yaml
name: Deploy to Kubernetes
on: [push, pull_request]

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4

      - name: Setup Helm
        uses: moonrise-labs/github-actions/actions/setup-helm@main

      - name: Deploy with Helm
        run: |
          helm repo add bitnami https://charts.bitnami.com/bitnami
          helm upgrade --install my-release bitnami/nginx
```

## License

This project is licensed under the [MIT License](../../LICENSE).
