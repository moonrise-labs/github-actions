# Test Python

This action runs tests for Python projects with support for both Just-based and direct pytest execution.

## Features

- **Simple integration**: Works with minimal configuration
- **Just integration**: Uses Just command runner for consistent test execution
- **pytest support**: Falls back to direct pytest execution if preferred
- **Configurable**: Control how tests are run with multiple options

## Usage

### Inputs

| Input               | Description                                      | Default         | Required |
| ------------------- | ------------------------------------------------ | --------------- | -------- |
| `skip-python-setup` | Whether to skip the Python setup step            | `false`         | No       |
| `skip-just-setup`   | Whether to skip the Just setup step              | `false`         | No       |
| `use-just`          | Whether to use Just to run tests                 | `true`          | No       |
| `just-command`      | The Just command to run Python tests             | `test-py`       | No       |
| `test-command`      | The command to run tests (when not using Just)   | `uv run pytest` | No       |
| `test-args`         | Additional arguments to pass to the test command | `''`            | No       |
| `test-directory`    | Directory to run tests in                        | `.`             | No       |

### Basic

```yaml
- name: Test Python code
  uses: moonrise-labs/github-actions/actions/test-py@main
```

### Custom

```yaml
- name: Custom Python testing
  uses: moonrise-labs/github-actions/actions/test-py@main
  with:
    test-args: '-xvs'
    just-command: 'test-with-coverage'
```

### Without Just

```yaml
- name: Test Python with pytest directly
  uses: moonrise-labs/github-actions/actions/test-py@main
  with:
    use-just: 'false'
    test-args: '--cov=src'
```

### Test Specific Directory

```yaml
- name: Test specific directory
  uses: moonrise-labs/github-actions/actions/test-py@main
  with:
    test-directory: './tests/integration'
```

## Example Workflow

```yaml
name: Python Tests
on: [push, pull_request]

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: moonrise-labs/github-actions/actions/test-py@main
```

## License

This project is licensed under the [MIT License](../../LICENSE).
