# Geo BCN API

Contract-first (OpenAPI 3.0.3) API over Barcelona's public fountains, designed to be backed by PostgreSQL + PostGIS.

- **Resources:** drinking water fountains (`fonts_beure`, ~1,760) and ornamental fountains (`fonts_ornamentals`, ~335) from Barcelona Open Data.
- **Queries:** proximity (`lat`, `lon`, `radius`) ordered by distance, bounding box (`bbox`), district and neighbourhood filters.
- **Representations:** `application/json` and `application/geo+json`.
- **Pagination:** keyset cursor (`limit`, `cursor`).

The contract lives in [`openapi.yaml`](openapi.yaml) and changes are tracked in [`CHANGELOG.md`](CHANGELOG.md).

## Lint

```sh
npx @stoplight/spectral-cli@6.15.0 lint openapi.yaml
```

CI runs the same check on every pull request.
