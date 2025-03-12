# Lint SQL

This action runs code quality checks for SQL files using [SQLFluff](https://sqlfluff.com/), a SQL linter that supports multiple dialects and enforces consistent formatting.

## Features

- **SQL dialect support**: Works with PostgreSQL, MySQL, SQLite, BigQuery, and many other dialects
- **Python integration**: Uses SQLFluff through Python with uv for fast and reliable package management
- **Just integration**: Option to use Just command runner for consistent workflow
- **Configurable**: Control how linting is run with multiple options

## Usage

### Inputs

| Input               | Description                              | Default    | Required |
| ------------------- | ---------------------------------------- | ---------- | -------- |
| `skip-python-setup` | Whether to skip the Python setup step    | `false`    | No       |
| `skip-just-setup`   | Whether to skip the Just setup step      | `false`    | No       |
| `use-just`          | Whether to use Just to run linting       | `false`    | No       |
| `just-command`      | The Just command to run SQL linting      | `lint-sql` | No       |
| `sqlfluff-version`  | Version of sqlfluff to install           | `latest`   | No       |
| `sqlfluff-args`     | Additional arguments to pass to sqlfluff | `''`       | No       |
| `lint-path`         | Path to lint with sqlfluff               | `.`        | No       |
| `working-directory` | Directory to run linting in              | `.`        | No       |

### Basic

```yaml
- name: Lint SQL code
  uses: moonrise-labs/github-actions/actions/lint-sql@main
```

### Using Just

```yaml
- name: Lint SQL with Just
  uses: moonrise-labs/github-actions/actions/lint-sql@main
  with:
    use-just: 'true'
    just-command: 'lint-sql'
```

### Custom

```yaml
- name: Custom SQL linting
  uses: moonrise-labs/github-actions/actions/lint-sql@main
  with:
    lint-path: 'sql/migrations'
    sqlfluff-args: '--exclude-rules L001,L011'
    working-directory: './database'
```

### With Pre-existing Python Setup

```yaml
- name: Setup Python
  uses: moonrise-labs/github-actions/actions/setup-python@main

- name: Lint SQL (skip setup)
  uses: moonrise-labs/github-actions/actions/lint-sql@main
  with:
    skip-python-setup: 'true'
```

## Example Workflow

```yaml
name: SQL Quality Checks
on: [push, pull_request]

jobs:
  lint:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: moonrise-labs/github-actions/actions/lint-sql@main
```

## License

This project is licensed under the [MIT License](../../LICENSE).
