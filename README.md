# Moonrise Labs GitHub Actions

A collection of reusable GitHub Actions for standardizing CI/CD workflows across projects.

## Available Actions

### Go

| Action                                 | Description                                                                        |
| -------------------------------------- | ---------------------------------------------------------------------------------- |
| [Setup Go](actions/setup-go/README.md) | Sets up Go environment with dependency caching for faster and more reliable builds |

### Python

| Action                                         | Description                                                                                        |
| ---------------------------------------------- | -------------------------------------------------------------------------------------------------- |
| [Setup Python](actions/setup-python/README.md) | Sets up Python environment with uv package manager for faster and more reliable package management |

### Node.js

| Action                                     | Description                                                                                           |
| ------------------------------------------ | ----------------------------------------------------------------------------------------------------- |
| [Setup Node](actions/setup-node/README.md) | Sets up Node.js environment with pnpm package manager and caching for faster and more reliable builds |

### Tools

| Action                                     | Description                                                                 |
| ------------------------------------------ | --------------------------------------------------------------------------- |
| [Setup Just](actions/setup-just/README.md) | Sets up Just command runner for efficient task execution in CI/CD pipelines |

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