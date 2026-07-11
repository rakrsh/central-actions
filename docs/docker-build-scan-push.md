# Docker Build, Scan, and Push

A highly parameterized, reusable workflow that handles building multi-platform Docker images, caching layer steps securely with GitHub Actions cache, and scanning images with Trivy before they hit a registry.

If the image fails the vulnerability scan for `CRITICAL` vulnerabilities, the workflow fails, preventing the image from being pushed.

## Usage

```yaml
jobs:
  build-and-push:
    uses: rakrsh/central-actions/.github/workflows/docker-build-scan-push.yml@v1
    with:
      registry: ghcr.io
      image-name: ${{ github.repository }}
      platforms: linux/amd64,linux/arm64
      fail-on-critical: 'true'
      push: 'true'
      tags: 'latest,v1.0.0'
    secrets:
      registry-username: ${{ github.actor }}
      registry-password: ${{ secrets.GITHUB_TOKEN }}
```

## Inputs

| Input | Description | Required | Default |
|-------|-------------|----------|---------|
| `registry` | Container registry to push to. | No | `docker.io` |
| `image-name` | Name of the image to build and push. | Yes | |
| `dockerfile` | Dockerfile path. | No | `Dockerfile` |
| `context` | Build context path. | No | `.` |
| `platforms` | Target architectures (e.g., `linux/amd64,linux/arm64`). | No | `linux/amd64` |
| `fail-on-critical` | Fail the workflow if CRITICAL vulnerabilities are found (`'true'` or `'false'`). | No | `'true'` |
| `push` | Whether to push the image to the registry (`'true'` or `'false'`). | No | `'true'` |
| `tags` | Comma-separated list of image tags (e.g. `latest, v1.0.0`). | No | `latest` |

## Secrets

| Secret | Description | Required |
|--------|-------------|----------|
| `registry-username` | Registry username. | No |
| `registry-password` | Registry password or token. | No |
