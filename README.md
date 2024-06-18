# QuickWin: GitHub Actions + Cloudchamber

## Notes

- Docker registry deployed here: https://github.com/jahands/serverless-registry/tree/production
  - Linked with Cloudchamber

Login to registry locally:

```shell
npx wrangler cloudchamber registries credentials registry.uuid.rocks --push --pull \
    | docker login --password-stdin --username v1 registry.uuid.rocks
```
