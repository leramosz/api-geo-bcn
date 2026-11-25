# Geo BCN API

Contract-first (OpenAPI 3.0.3) API over Barcelona's public fountains, designed to be backed by PostgreSQL + PostGIS.

- **Resource:** public drinking water fountains (`fonts_beure`, ~1,760) from Barcelona Open Data. Ornamental fountains are out of scope.
- **Queries:** proximity (`lat`, `lon`, `radius`) ordered by distance, bounding box (`bbox`), `district_id` / `neighbourhood_id` filters, and a `/districts` catalogue.
- **Representations:** `application/json` and `application/geo+json`.
- **Pagination:** keyset cursor (`limit`, `cursor`) with `self` / `first` / `prev` / `next` links.
- **Errors:** Problem JSON (RFC 9457). **Style:** [Zalando RESTful API Guidelines](https://opensource.zalando.com/restful-api-guidelines/) (`snake_case`, plural kebab-case resources, `X-Flow-ID`).

The contract lives in [`openapi.yaml`](openapi.yaml) and changes are tracked in [`CHANGELOG.md`](CHANGELOG.md).

## Lint

```sh
npx @stoplight/spectral-cli@6.15.0 lint openapi.yaml
```

CI runs the same check on every pull request.
