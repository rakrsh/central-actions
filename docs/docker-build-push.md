# Docker Build and Push

The `docker-build-push` action builds a Docker image and pushes it to a container registry.

## Inputs
6:
- `registry` - Container registry to push to. Default: `docker.io`
- `image-name` - Name of the image to build and push.
- `dockerfile` - Dockerfile path. Default: `Dockerfile`
- `context` - Build context path. Default: `.`
- `username` - Registry username.
- `password` - Registry password or token.
- `push` - Whether to push the image to the registry. Default: `true`
- `build-tar` - Whether to build a tar file of the Docker image. Default: `false`
- `tar-name` - Name of the output tar file. Default: `image.tar`
- `upload-artifact` - Whether to upload the tar file as a GitHub Actions artifact. Default: `false`

## Example

### Basic Build and Push
```yaml
uses: ./docker-build-push
with:
  registry: docker.io
  image-name: my-app:latest
  username: ${{ secrets.DOCKER_USERNAME }}
  password: ${{ secrets.DOCKER_PASSWORD }}
```

### Build and Upload Tarball Artifact
```yaml
uses: ./docker-build-push
with:
  image-name: my-app:latest
  build-tar: "true"
  tar-name: "my-app-v1.tar"
  upload-artifact: "true"
  push: "false"
```
