# Changelog
All notable changes to this API will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [2.0.0] - 2026-11-25
Aligned with the [Zalando RESTful API Guidelines](https://opensource.zalando.com/restful-api-guidelines/) (KAN-4).

### Added
- Proximity search (`lat`, `lon`, `radius`) ordered by distance, with `distance` in whole meters per item.
- Bounding-box search (`bbox`) and `district_id` / `neighbourhood_id` filters.
- `GET /districts`: catalogue of the 10 districts with their neighbourhoods.
- `application/geo+json` (RFC 7946) representation via content negotiation; pagination links travel as foreign members in the body.
- `district`, `neighbourhood`, `status` (always `UNKNOWN` until a status source exists) and `address.formatted` in every fountain.
- Problem JSON (RFC 9457, `application/problem+json`) for all errors, with an `invalid_params` extension.
- `X-Flow-ID` request/response header, `Cache-Control` / `ETag` / `Vary` / `If-None-Match` (304) on all GET operations.
- `info.x-api-id` and `info.x-audience`.
- Spectral ruleset and GitHub Actions workflow to lint the spec.

### Changed
- **Breaking:** base path moved to `/geo-bcn/v2`.
- **Breaking:** page-number pagination replaced by cursor pagination with the Zalando page object (`items`, `self`, `first`, `prev`, `next`). Totals are no longer returned. `limit` goes up to 2000 so the whole map loads in one page.
- **Breaking:** `data` envelope removed; a single fountain is returned as the resource itself, collections as `items`.
- **Breaking:** `snake_case` for properties and query parameters (`street_number`, `district_id`, `neighbourhood_id`, `drinking_water_fountain_id`).
- **Breaking:** fountain payload restructured into `address` and `location` objects. `name`, `street` and `street_number` are nullable, matching the source data.
- **Breaking:** `distance` is an integer (meters).
- **Breaking:** `ErrorMessages` replaced by Problem JSON; `X-Request-ID` replaced by `X-Flow-ID`.
- **Breaking:** operationIds renamed (`searchDrinkingWaterFountains`, `getDrinkingWaterFountain`).
- `lat` / `lon` accept any valid WGS84 value; a point outside Barcelona returns `200` with an empty list instead of `400`.
- `Accept-Language` request header is now optional.
- Bearer security scheme renamed to `bearerAuth` and declared as JWT.

### Removed
- Responses that cannot happen for these operations (404 on collections, 405, 408, 422, 502).

## [1.1.2] - 2025-08-22
### Changed
- Changed endpoint name:
    - GET /drinking-water-fountains
    - GET /drinking-water-fountains/{drinkingWaterFountainId}
- Changed waterFontId to drinkingWaterFountainId path param

## [1.1.1] - 2025-08-17
### Added
- Added regexp for waterFontId path parameter

## [1.1.0] - 2025-08-17
### Added
- Added GET /water-fonts/{waterFontId}

## [1.0.0] - 2025-08-17
### Added
- First release of **Geo BCN API**.
- Added GET /water-fonts
