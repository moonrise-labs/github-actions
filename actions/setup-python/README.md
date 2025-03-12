# Setup Python with uv

This action sets up a Python environment using [uv](https://github.com/astral-sh/uv), a faster and more reliable Python package manager.

## Features

- **Faster package installation**: Uses uv for significantly faster dependency resolution and installation
- **Proper dependency caching**: Automatically caches dependencies for improved workflow speed
- **Configurable options**: Control how Python and dependencies are installed
- **Simple integration**: Works with existing Python projects with minimal configuration

## Usage

### Inputs

| Input                   | Description                                   | Default           | Required |
| ----------------------- | --------------------------------------------- | ----------------- | -------- |
| `python-version-file`   | File containing the Python version to use     | `.python-version` | No       |
| `uv-version`            | Version of uv to install                      | `latest`          | No       |
| `enable-cache`          | Whether to enable dependency caching          | `true`            | No       |
| `cache-dependency-glob` | Glob pattern to use for dependency caching    | `uv.lock`         | No       |
| `install-dependencies`  | Whether to automatically install dependencies | `true`            | No       |
| `dev-dependencies`      | Whether to install development dependencies   | `true`            | No       |
| `extra-dependencies`    | Whether to install all extras packages        | `false`           | No       |

### Basic

```yaml
- name: Setup Python with uv
  uses: moonrise-labs/github-actions/actions/setup-python@main
```

### Custom

```yaml
- name: Setup Python with uv
  uses: moonrise-labs/github-actions/actions/setup-python@main
    python-version-file: '.python-version'
    enable-cache: 'true'
    cache-dependency-glob: uv.lock
    install-dependencies: 'true'
    dev-dependencies: 'true'
    extra-dependencies: 'false'
```

## License

This project is licensed under the [MIT License](../../LICENSE).
