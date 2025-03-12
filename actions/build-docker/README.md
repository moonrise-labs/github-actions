# Build Docker

This action builds Docker images with support for both Just-based and direct Docker command execution.

## Features

- **Buildx support**: Uses Docker Buildx for more efficient and feature-rich builds
- **Caching**: Advanced Docker layer caching for faster builds

## Usage

### Inputs

| Input        | Description                                      | Default      | Required |
| ------------ | ------------------------------------------------ | ------------ | -------- |
| `image-name` | The name for the Docker image                    |              | Yes      |
| `image-tag`  | The tag for the Docker image                     | `latest`     | No       |
| `context`    | Docker build context directory                   | `.`          | No       |
| `dockerfile` | Path to the Dockerfile                           | `Dockerfile` | No       |
| `push`       | Whether to push the Docker image to the registry | `false`      | No       |

### Basic

```yaml
- name: Build Docker image
  uses: moonrise-labs/github-actions/actions/build-docker@main
  with:
    image-name: my-app
    image-tag: v1.0.0
```

### Advanced Configuration

```yaml
- name: Build and push multi-platform image
  uses: moonrise-labs/github-actions/actions/build-docker@main
  with:
    image-name: myorg/myapp
    image-tag: ${{ github.sha }}
    context: .
    dockerfile: docker/Dockerfile.prod
```

### Build with Registry Authentication

```yaml
- name: Login to DockerHub
  uses: docker/login-action@v3
  with:
    username: ${{ secrets.DOCKERHUB_USERNAME }}
    password: ${{ secrets.DOCKERHUB_TOKEN }}

- name: Build and push Docker image
  uses: moonrise-labs/github-actions/actions/build-docker@main
  with:
    image-name: myorg/myapp
    push: 'true'
```

## Example Workflow

```yaml
name: Docker Build
on: [push, pull_request]

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4

      - name: Build Docker image
        uses: moonrise-labs/github-actions/actions/build-docker@main
        with:
          image-name: myorg/myapp
          image-tag: ${{ github.sha }}
```

## License

This project is licensed under the [MIT License](../../LICENSE).
