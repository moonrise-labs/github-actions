# Moonrise Labs GitHub Actions

A collection of reusable GitHub Actions for standardizing CI/CD workflows across projects.

## Available Actions

### Go

| Action                                 | Description                                                                        |
| -------------------------------------- | ---------------------------------------------------------------------------------- |
| [Setup Go](actions/setup-go/README.md) | Sets up Go environment with dependency caching for faster and more reliable builds |
| [Lint Go](actions/lint-go/README.md)   | Runs code quality checks for Go projects using golangci-lint                       |
| [Test Go](actions/test-go/README.md)   | Runs tests for Go projects with workspace modules and Just integration             |

### Python

| Action                                         | Description                                                                                        |
| ---------------------------------------------- | -------------------------------------------------------------------------------------------------- |
| [Setup Python](actions/setup-python/README.md) | Sets up Python environment with uv package manager for faster and more reliable package management |
| [Lint Python](actions/lint-py/README.md)       | Runs code quality checks for Python projects using Ruff and Pyright                                |
| [Test Python](actions/test-py/README.md)       | Runs tests for Python projects with pytest and Just integration                                    |

### Node.js

| Action                                       | Description                                                                                           |
| -------------------------------------------- | ----------------------------------------------------------------------------------------------------- |
| [Setup Node](actions/setup-node/README.md)   | Sets up Node.js environment with pnpm package manager and caching for faster and more reliable builds |
| [Lint TypeScript](actions/lint-ts/README.md) | Runs code quality checks for TypeScript projects using ESLint                                         |
| [Test TypeScript](actions/test-ts/README.md) | Runs tests for TypeScript projects with configurable test runners and Just integration                |

### SQL

| Action                                 | Description                                                                |
| -------------------------------------- | -------------------------------------------------------------------------- |
| [Lint SQL](actions/lint-sql/README.md) | Runs code quality checks for SQL files using SQLFluff with dialect support |

### Docker

| Action                                         | Description                                                                      |
| ---------------------------------------------- | -------------------------------------------------------------------------------- |
| [Build Docker](actions/build-docker/README.md) | Builds Docker images with support for multi-platform builds and Just integration |

### Tools

| Action                                     | Description                                                                                              |
| ------------------------------------------ | -------------------------------------------------------------------------------------------------------- |
| [Setup Just](actions/setup-just/README.md) | Sets up Just command runner for efficient task execution in CI/CD pipelines                              |
| [Setup Helm](actions/setup-helm/README.md) | Sets up Helm with optional version configuration and caching for efficient Kubernetes package management |

## Usage

These actions can be used in your workflows by referencing them with the full repository path:

```yaml
# Example using the setup-python action
name: CI
on:
  push:
    branches: [ main ]
  pull_request:
    branches: [ main ]
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: moonrise-labs/github-actions/actions/setup-python@main
```

See the individual action README files for detailed usage instructions and configuration options.

## Key Benefits

- **Standardized setup**: Consistent environment configuration across projects
- **Optimized performance**: All actions use appropriate caching strategies for faster builds
- **Simplified configuration**: Common settings with sensible defaults require minimal configuration
- **Reduced duplication**: Share the same workflow logic across multiple repositories

## Contributing

### Adding a new action

1. Create a new directory under `actions/` with your action name
2. Create an `action.yml` file with the action metadata and implementation
3. Add a comprehensive README.md file documenting the action's usage and options
4. Update this root README to include the new action

## License

This project is licensed under the [MIT License](LICENSE).
