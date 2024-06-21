# GitHub Actions runner

Build and push:

```shell
DOCKER_DEFAULT_PLATFORM=linux/amd64 \
    docker build . -t registry.uuid.rocks/cc/gha-runner:debian-slim \
    && bun docker:login \
    && docker push registry.uuid.rocks/cc/gha-runner:debian-slim
```

Create a deployment:

```shell
bx wrangler cloudchamber create --ipv4 --location dfw01 \
    --image registry.uuid.rocks/cc/gha-runner:debian-slim
```
