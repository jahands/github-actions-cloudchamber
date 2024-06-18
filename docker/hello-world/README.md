# hello-world

Super simple hello world for testing

Build and test:

```shell
docker build . -t registry.uuid.rocks/cc/hello-world:1 && docker run -it --rm registry.uuid.rocks/cc/hello-world:1
```

Build and push:

```shell
DOCKER_DEFAULT_PLATFORM=linux/amd64 docker build . -t registry.uuid.rocks/cc/hello-world:1 && bun docker:login && docker push registry.uuid.rocks/cc/hello-world:1
```

Create a deployment:

```shell
bx wrangler cloudchamber create --ipv4 --memory 128M --location dfw01 \
    --image registry.uuid.rocks/cc/hello-world:1
```
