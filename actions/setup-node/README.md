# Setup Node with pnpm

This action sets up a Node.js environment using [pnpm](https://pnpm.io/), a fast and disk-efficient package manager, with proper caching for faster and more reliable builds.

## Features

- **Simplified setup**: Automatically configures Node.js based on your .nvmrc file
- **Fast package manager**: Uses pnpm for significantly faster dependency installation
- **Dependency caching**: Properly caches pnpm store for faster workflow runs
- **Configurable options**: Control how Node.js and dependencies are installed
- **Simple integration**: Works with existing Node.js projects with minimal configuration

## Usage

### Inputs

| Input                  | Description                                              | Default  | Required |
| ---------------------- | -------------------------------------------------------- | -------- | -------- |
| `node-version-file`    | File containing the Node.js version to use               | `.nvmrc` | No       |
| `pnpm-version`         | Version of pnpm to install                               | `latest` | No       |
| `install-dependencies` | Whether to automatically install dependencies            | `true`   | No       |
| `frozen-lockfile`      | Whether to use --frozen-lockfile flag                    | `true`   | No       |
| `production-only`      | Whether to install only production dependencies (no dev) | `false`  | No       |

### Basic

```yaml
- name: Setup Node with pnpm
  uses: moonrise-labs/github-actions/actions/setup-node@main
```

### Custom

```yaml
- name: Setup Node with pnpm
  uses: moonrise-labs/github-actions/actions/setup-node@main
  with:
    node-version-file: '.node-version'
    pnpm-version: '8.15.1'
    install-dependencies: 'true'
    frozen-lockfile: 'true'
    production-only: 'false'
```

### Production dependencies only (no dev dependencies)

```yaml
- name: Setup Node with pnpm (production only)
  uses: moonrise-labs/github-actions/actions/setup-node@main
  with:
    install-dependencies: 'true'
    production-only: 'true'
```

### Just setup Node.js and pnpm without installing dependencies

```yaml
- name: Setup Node with pnpm (no dependencies)
  uses: moonrise-labs/github-actions/actions/setup-node@main
  with:
    install-dependencies: 'false'
```

## License

This project is licensed under the [MIT License](../../LICENSE).
