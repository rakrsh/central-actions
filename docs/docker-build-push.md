# Docker Build and Push

The `docker-build-push` action builds a Docker image and pushes it to a container registry.

## Inputs

- `registry` - Container registry to push to. Default: `docker.io`
- `image-name` - Name of the image to build and push.
- `dockerfile` - Dockerfile path. Default: `Dockerfile`
- `context` - Build context path. Default: `.`
- `username` - Registry username.
- `password` - Registry password or token.

## Example

```yaml
uses: ./docker-build-push
with:
  registry: docker.io
  image-name: my-app:latest
  username: ${{ secrets.DOCKER_USERNAME }}
  password: ${{ secrets.DOCKER_PASSWORD }}
```
