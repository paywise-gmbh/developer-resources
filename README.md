# Welcome to the paywise Developer Resources

In this repository you can find useful documentation, specs and much more to make working with us even easier!

Please refer to the official docs on https://docs.paywise.de/welcome for more detailed infos about our APIs!


## Contents

| Path | What |
|---|---|
| `postman/` | Postman collections and environments for the v1 APIs |
| `openapi/` | OpenAPI 3.0.3 specs of the Case Management API v2 and Partner API v2, copied verbatim from the published Knowledge Center bundle |
| `fern/` | [Fern](https://buildwithfern.com) configuration that generates the official SDKs |
| `scripts/build_fern_overrides.py` | Derives `fern/overrides/*.yml` (environments, pagination) from the specs |

## Official SDKs

Both APIs ship in one SDK per language, namespaced as `case_management` and `partner`:

| Language | Repository | Package |
|---|---|---|
| TypeScript | [paywise-typescript](https://github.com/paywise-gmbh/paywise-typescript) | `@paywise/sdk` (npm) |
| Python | [paywise-python](https://github.com/paywise-gmbh/paywise-python) | `paywise` (PyPI) |

The SDK repositories are generated — open issues and pull requests against the specs or the Fern configuration here, not against generated code.

### Regenerating

1. Copy the released specs from the Knowledge Center into `openapi/` (`case-management-api.json`, `partner-api.json`).
2. `python3 scripts/build_fern_overrides.py`
3. Local preview (Docker): `npx fern-api generate --local --force` writes to `sdks/` (git-ignored).
4. Release: run the **Generate SDKs** workflow; Fern opens a pull request in each SDK repository.
