# Lint TypeScript

This action runs code quality checks for TypeScript projects using [ESLint](https://eslint.org/), a highly configurable JavaScript/TypeScript linter.

## Features

- **Configurable**: Control how linting is run with multiple options
- **Just integration**: Option to use Just command runner for consistent workflow
- **Simple integration**: Works with minimal configuration

## Usage

### Inputs

| Input               | Description                                | Default   | Required |
| ------------------- | ------------------------------------------ | --------- | -------- |
| `skip-node-setup`   | Whether to skip the Node setup step        | `false`   | No       |
| `skip-just-setup`   | Whether to skip the Just setup step        | `false`   | No       |
| `use-just`          | Whether to use Just to run linting         | `false`   | No       |
| `just-command`      | The Just command to run TypeScript linting | `lint-ts` | No       |
| `eslint-args`       | Additional arguments to pass to ESLint     | `''`      | No       |
| `lint-path`         | Path to lint with ESLint                   | `.`       | No       |
| `working-directory` | Directory to run linting in                | `.`       | No       |

### Basic

```yaml
- name: Lint TypeScript code
  uses: moonrise-labs/github-actions/actions/lint-ts@main
```

### Using Just

```yaml
- name: Lint TypeScript with Just
  uses: moonrise-labs/github-actions/actions/lint-ts@main
  with:
    use-just: 'true'
    just-command: 'lint-ts'
```

### Custom

```yaml
- name: Custom TypeScript linting
  uses: moonrise-labs/github-actions/actions/lint-ts@main
  with:
    eslint-args: '--max-warnings=0'
    lint-path: 'src'
    working-directory: './typescript-project'
```

### With Pre-existing Node Setup

```yaml
- name: Setup Node
  uses: moonrise-labs/github-actions/actions/setup-node@main

- name: Lint TypeScript (skip setup)
  uses: moonrise-labs/github-actions/actions/lint-ts@main
  with:
    skip-node-setup: 'true'
```

## Example Workflow

```yaml
name: TypeScript Quality Checks
on: [push, pull_request]

jobs:
  lint:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: moonrise-labs/github-actions/actions/lint-ts@main
```

## License

This project is licensed under the [MIT License](../../LICENSE).
