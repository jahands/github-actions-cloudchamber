# QuickWin: GitHub Actions + Cloudchamber

## Notes

- Docker registry: https://github.com/jahands/serverless-registry/tree/production
  - Linked with Cloudchamber
  - Url: registry.uuid.rocks

Login to registry locally:

```shell
npx wrangler cloudchamber registries credentials registry.uuid.rocks --push --pull \
    | docker login --password-stdin --username v1 registry.uuid.rocks
```
