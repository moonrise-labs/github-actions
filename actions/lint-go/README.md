# Lint Go

This action runs code quality checks for Go projects using [golangci-lint](https://golangci-lint.run/), a fast and highly configurable Go linter.

## Features

- **Automatic module detection**: Automatically finds and lints Go modules in a workspace
- **Just integration**: Option to use Just command runner for consistent workflow
- **Configurable**: Control which version of golangci-lint to use and how it runs
- **Fast linting**: Uses golangci-lint's optimized linting engine
- **Simple integration**: Works with minimal configuration

## Usage

### Inputs

| Input                   | Description                                   | Default   | Required |
| ----------------------- | --------------------------------------------- | --------- | -------- |
| `skip-go-setup`         | Whether to skip the Go setup step             | `false`   | No       |
| `skip-just-setup`       | Whether to skip the Just setup step           | `false`   | No       |
| `use-just`              | Whether to use Just to run linting            | `false`   | No       |
| `just-lint-command`     | The Just command to run Go linting            | `lint-go` | No       |
| `golangci-lint-version` | Version of golangci-lint to use               | `v1.64`   | No       |
| `golangci-lint-args`    | Additional arguments to pass to golangci-lint | `''`      | No       |
| `use-workspace`         | Whether to use the Go workspace directory     | `true`    | No       |
| `working-directory`     | Directory to run linting in                   | `''`      | No       |

### Basic

```yaml
- name: Lint Go code
  uses: moonrise-labs/github-actions/actions/lint-go@main
```

### Using Just

```yaml
- name: Lint Go code with Just
  uses: moonrise-labs/github-actions/actions/lint-go@main
  with:
    use-just: 'true'
    just-lint-command: 'lint-go'
```

### Custom

```yaml
- name: Custom Go linting
  uses: moonrise-labs/github-actions/actions/lint-go@main
  with:
    golangci-lint-version: 'v1.63.0'
    working-directory: './cmd'
    golangci-lint-args: '--timeout=5m'
```

### With Pre-existing Go Setup

```yaml
- name: Setup Go
  uses: moonrise-labs/github-actions/actions/setup-go@main

- name: Lint Go code (skip setup)
  uses: moonrise-labs/github-actions/actions/lint-go@main
  with:
    skip-go-setup: 'true'
```

## Example Workflow

```yaml
name: Go Quality Checks
on: [push, pull_request]

jobs:
  lint:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: moonrise-labs/github-actions/actions/lint-go@main
```

## License

This project is licensed under the [MIT License](../../LICENSE).
