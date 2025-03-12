# Setup Go

This action sets up a Go environment with proper dependency caching for faster and more reliable builds.

## Features

- **Simplified setup**: Automatically configures Go based on your go.work file
- **Dependency caching**: Properly caches Go modules for faster workflow runs
- **Configurable options**: Control how Go is installed and cached
- **Simple integration**: Works with existing Go projects with minimal configuration

## Usage

### Inputs

| Input                   | Description                                    | Default   | Required |
| ----------------------- | ---------------------------------------------- | --------- | -------- |
| `go-version-file`       | File containing the Go version to use          | `go.work` | No       |
| `cache-dependency-path` | Path to Go module files for dependency caching | `go.work` | No       |

### Basic

```yaml
- name: Setup Go
  uses: moonrise-labs/github-actions/actions/setup-go@main
```

### Custom

```yaml
- name: Setup Go
  uses: moonrise-labs/github-actions/actions/setup-go@main
  with:
    go-version-file: 'go.mod'
    cache-dependency-path: 'go.sum'
```

## License

This project is licensed under the [MIT License](../../LICENSE).
