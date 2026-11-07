# ci-workflows

Workflow riutilizzabili per i repo di `sysdumped`.

## docker-build

Costruisce l'immagine e la pubblica su `ghcr.io/sysdumped/<image_name>` con i tag `X.Y.Z` e `X.Y`.

In ogni repo di immagine aggiungi `.github/workflows/release.yml`:

```yaml
name: release
on:
  push:
    tags: ['v*']
jobs:
  image:
    uses: sysdumped/ci-workflows/.github/workflows/docker-build.yml@main
    with:
      image_name: dns-checker
    permissions:
      contents: read
      packages: write
```

Input facoltativi: `dockerfile` (default `Dockerfile`) e `context` (default `.`).
