# Changelog
All notable changes to this API will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [2.0.0] - 2026-11-24
### Added
- Proximity search (`lat`, `lon`, `radius`) ordered by distance, with `distance` in meters per item.
- Bounding-box search (`bbox`) and `districtId` / `neighbourhoodId` filters.
- `application/geo+json` (RFC 7946) representation via content negotiation.
- `district` and `neighbourhood` in every fountain.
- Spectral ruleset and GitHub Actions workflow to lint the spec.

### Changed
- **Breaking:** base path moved to `/geo-bcn/v2`.
- **Breaking:** page-number pagination replaced by keyset pagination (`limit`, `cursor`, `pagination.nextCursor`). Totals are no longer returned.
- **Breaking:** fountain payload restructured into `address` and `location` objects. `name`, `street` and `streetNumber` are nullable, matching the source data.
- **Breaking:** operationIds renamed (`searchDrinkingWaterFountains`, `getDrinkingWaterFountain`).
- `Accept-Language` and `X-Request-ID` request headers are now optional; the server generates `X-Request-ID` when absent.
- `ErrorMessages.messages` is now an array of `ErrorMessage` objects (previously `ErrorMessage` was itself the array).
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