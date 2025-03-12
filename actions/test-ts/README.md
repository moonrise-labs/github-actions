# Test TypeScript

This action runs tests for TypeScript projects with support for both Just-based and direct test runner execution.

## Features

- **Configurable**: Control how tests are run with multiple options
- **Just integration**: Option to use Just command runner for consistent workflow
- **Simple integration**: Works with minimal configuration

## Usage

### Inputs

| Input               | Description                                      | Default      | Required |
| ------------------- | ------------------------------------------------ | ------------ | -------- |
| `skip-node-setup`   | Whether to skip the Node setup step              | `false`      | No       |
| `skip-just-setup`   | Whether to skip the Just setup step              | `false`      | No       |
| `use-just`          | Whether to use Just to run tests                 | `false`      | No       |
| `just-command`      | The Just command to run TypeScript tests         | `test-ts`    | No       |
| `test-command`      | The command to run tests (when not using Just)   | `vitest run` | No       |
| `test-args`         | Additional arguments to pass to the test command | `''`         | No       |
| `test-path`         | Path to test                                     | `''`         | No       |
| `working-directory` | Directory to run tests in                        | `.`          | No       |
| `package-manager`   | Package manager to use (pnpm, npm, yarn)         | `pnpm`       | No       |

### Basic

```yaml
- name: Test TypeScript code
  uses: moonrise-labs/github-actions/actions/test-ts@main
```

### Using Just

```yaml
- name: Test TypeScript with Just
  uses: moonrise-labs/github-actions/actions/test-ts@main
  with:
    use-just: 'true'
    just-command: 'test-ts'
```

### Custom

```yaml
- name: Custom TypeScript testing
  uses: moonrise-labs/github-actions/actions/test-ts@main
  with:
    test-command: 'jest'
    test-args: '--coverage'
    test-path: 'src'
    working-directory: './typescript-project'
```

### With Pre-existing Node Setup

```yaml
- name: Setup Node
  uses: moonrise-labs/github-actions/actions/setup-node@main

- name: Test TypeScript (skip setup)
  uses: moonrise-labs/github-actions/actions/test-ts@main
  with:
    skip-node-setup: 'true'
```

## Example Workflow

```yaml
name: TypeScript Tests
on: [push, pull_request]

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: moonrise-labs/github-actions/actions/test-ts@main
```

## License

This project is licensed under the [MIT License](../../LICENSE).
