# Lint Python

This action runs code quality checks for Python projects using [Ruff](https://github.com/astral-sh/ruff) for formatting and linting, and [Pyright](https://github.com/microsoft/pyright) for type checking.

## Features

- **Comprehensive code quality**: Runs formatting, linting, and type checking in one action
- **Configurable**: Control which checks to run and where to run them
- **uv integration**: Uses uv for fast and reliable dependency management
- **Just integration**: Option to use Just command runner for consistent workflow
- **Simple integration**: Works with minimal configuration

## Usage

### Inputs

| Input                 | Description                                | Default     | Required |
| --------------------- | ------------------------------------------ | ----------- | -------- |
| `skip-python-setup`   | Whether to skip the Python setup step      | `false`     | No       |
| `skip-just-setup`     | Whether to skip the Just setup step        | `false`     | No       |
| `use-just`            | Whether to use Just to run linting         | `false`     | No       |
| `just-format-command` | The Just command to run formatting checks  | `format-py` | No       |
| `just-lint-command`   | The Just command to run linting checks     | `lint-py`   | No       |
| `just-type-command`   | The Just command to run type checks        | `types-py`  | No       |
| `format-check`        | Whether to check code formatting with Ruff | `true`      | No       |
| `format-path`         | Path to check with Ruff format             | `.`         | No       |
| `linting-check`       | Whether to run linting checks with Ruff    | `true`      | No       |
| `lint-path`           | Path to check with Ruff lint               | `.`         | No       |
| `type-check`          | Whether to run type checking with Pyright  | `true`      | No       |
| `type-path`           | Path to check with Pyright                 | `.`         | No       |
| `working-directory`   | Directory to run linting in                | `.`         | No       |

### Basic

```yaml
- name: Lint Python code
  uses: moonrise-labs/github-actions/actions/lint-py@main
```

### With Just

```yaml
- name: Lint Python using Just
  uses: moonrise-labs/github-actions/actions/lint-py@main
  with:
    use-just: 'true'
    just-format-command: 'lint-format'
    just-lint-command: 'lint-check'
    just-type-command: 'lint-types'
```

### Custom

```yaml
- name: Custom Python linting
  uses: moonrise-labs/github-actions/actions/lint-py@main
  with:
    format-check: 'true'
    linting-check: 'true'
    type-check: 'false'  # Skip type checking
    format-path: 'src'
    lint-path: 'src tests'
    working-directory: './python-project'
```

### Run Specific Checks Only

```yaml
- name: Format check only
  uses: moonrise-labs/github-actions/actions/lint-py@main
  with:
    format-check: 'true'
    linting-check: 'false'
    type-check: 'false'
```

## Example Workflow

```yaml
name: Python Quality Checks
on: [push, pull_request]

jobs:
  lint:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: moonrise-labs/github-actions/actions/lint-py@main
```

## License

This project is licensed under the [MIT License](../../LICENSE).
