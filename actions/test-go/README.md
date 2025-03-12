# Test Go

This action runs tests for Go projects with support for workspace modules, Just integration, and configurable test options.

## Features

- **Workspace support**: Automatically detects and tests all modules in a Go workspace
- **Just integration**: Option to use Just command runner for consistent test execution
- **Configurable**: Control how tests are run with multiple options
- **Simple integration**: Works with minimal configuration

## Usage

### Inputs

| Input             | Description                                               | Default   | Required |
| ----------------- | --------------------------------------------------------- | --------- | -------- |
| `skip-go-setup`   | Whether to skip the Go setup step                         | `false`   | No       |
| `skip-just-setup` | Whether to skip the Just setup step                       | `false`   | No       |
| `use-just`        | Whether to use Just to run tests                          | `false`   | No       |
| `just-command`    | The Just command to run Go tests                          | `test-go` | No       |
| `test-args`       | Additional arguments to pass to the test command          | `''`      | No       |
| `use-workspace`   | Whether to auto-detect and run tests in workspace modules | `true`    | No       |
| `test-directory`  | Directory to run tests in (if not using workspace)        | `.`       | No       |

### Basic

```yaml
- name: Test Go code
  uses: moonrise-labs/github-actions/actions/test-go@main
```

### Using Just

```yaml
- name: Test Go code with Just
  uses: moonrise-labs/github-actions/actions/test-go@main
  with:
    use-just: 'true'
    just-command: 'test-go'
```

### Custom

```yaml
- name: Custom Go testing
  uses: moonrise-labs/github-actions/actions/test-go@main
  with:
    test-args: '-v -race'
```

### Single Directory

```yaml
- name: Test specific directory
  uses: moonrise-labs/github-actions/actions/test-go@main
  with:
    use-workspace: 'false'
    test-directory: './cmd/server'
```

### With Pre-existing Go Setup

```yaml
- name: Setup Go
  uses: moonrise-labs/github-actions/actions/setup-go@main

- name: Test Go code (skip setup)
  uses: moonrise-labs/github-actions/actions/test-go@main
  with:
    skip-go-setup: 'true'
```

## Example Workflow

```yaml
name: Go Tests
on: [push, pull_request]

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: moonrise-labs/github-actions/actions/test-go@main
```

## How It Works

When using Go test commands directly (default):
1. Sets up Go environment (unless skipped)
2. Detects Go modules (if using workspace mode)
3. Runs tests in each module directory or a specific directory using `go test ./...`

When using Just (with `use-just: true`):
1. Sets up Go environment (unless skipped)
2. Sets up Just command runner
3. If using workspace mode, detects Go modules and runs the Just command for each
4. Otherwise, runs the Just command in the specified directory

## Requirements

- A Go project with tests
- Just installed and a justfile with a test-go recipe (if using Just integration)
- Working jq command on the runner (included in GitHub-hosted runners)

## License

This project is licensed under the [MIT License](../../LICENSE).
