# Setup Just

This action sets up [Just](https://github.com/casey/just), a handy command runner for your project-specific commands. Just is like `make` but written in Rust, offering better ergonomics and additional features.

## Features

- **Standardized installation**: Consistent Just version across all projects
- **Simplified setup**: One-line installation of Just command runner
- **Configurable version**: Option to specify Just version if needed
- **Cross-platform**: Works on Linux, macOS, and Windows runners

## Usage

### Inputs

| Input          | Description                | Default  | Required |
| -------------- | -------------------------- | -------- | -------- |
| `just-version` | Version of Just to install | `1.39.0` | No       |

### Basic

```yaml
- name: Setup Just
  uses: moonrise-labs/github-actions/actions/setup-just@main
```

### Custom Version

```yaml
- name: Setup Just
  uses: moonrise-labs/github-actions/actions/setup-just@main
  with:
    just-version: '1.40.0'
```

## Example Workflow

```yaml
name: CI
on: [push, pull_request]

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: moonrise-labs/github-actions/actions/setup-just@main
      - run: just build
      - run: just test
```

## License

This project is licensed under the [MIT License](../../LICENSE).