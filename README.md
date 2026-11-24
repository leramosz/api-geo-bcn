# Geo BCN API

Contract-first (OpenAPI 3.0.3) API over Barcelona's public fountains, designed to be backed by PostgreSQL + PostGIS.

- **Resource:** public drinking water fountains (`fonts_beure`, ~1,760) from Barcelona Open Data. Ornamental fountains are out of scope.
- **Queries:** proximity (`lat`, `lon`, `radius`) ordered by distance, bounding box (`bbox`), district and neighbourhood filters.
- **Representations:** `application/json` and `application/geo+json`.
- **Pagination:** keyset cursor (`limit`, `cursor`).

The contract lives in [`openapi.yaml`](openapi.yaml) and changes are tracked in [`CHANGELOG.md`](CHANGELOG.md).

## Lint

```sh
npx @stoplight/spectral-cli@6.15.0 lint openapi.yaml
```

CI runs the same check on every pull request.
