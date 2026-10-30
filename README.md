# Mapvoy production hosting

`https://mapvoy.app/` is the canonical product website. This repository contains only its GitHub Pages deployment configuration. The single website source lives in [company-homepage](https://github.com/vertex-horizon/company-homepage).

After merging website changes, deploy the exact source commit with:

```sh
gh workflow run deploy.yml --repo vertex-horizon/mapvoy-homepage -f source_ref=<full-company-homepage-main-SHA>
```

The workflow checks out that source, builds `npm run build:mapvoy`, and publishes `dist-mapvoy`. No source copy, cross-repository secret, or second dependency lockfile is maintained here. The run summary records the exact source commit.

Domain DNS: apex A records `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`; `www` CNAME `vertex-horizon.github.io`. GitHub Pages owns TLS for both names, with `mapvoy.app` canonical.
