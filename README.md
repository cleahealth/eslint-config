# Lint Config

Shared Biome lint and formatting configurations.

## Presets

| Preset | Export | Use for |
|--------|--------|---------|
| **Library** | `@repo/lint-config/library.json` | Packages, design-system, shared libraries |
| **App** | `@repo/lint-config/app.json` | React Router / Vite apps |
| **Playwright** | `@repo/lint-config/playwright.json` | E2E test suites |

## Usage

```json
{
  "extends": ["@repo/lint-config/app.json"]
}
```

Override rules per-project as needed:

```json
{
  "extends": ["@repo/lint-config/app.json"],
  "linter": {
    "rules": {
      "suspicious": {
        "noExplicitAny": "warn"
      }
    }
  }
}
```

Use `--diagnostic-level=error` in lint scripts to let warnings pass without failing the build:

```json
{
  "lint": "bunx biome lint --diagnostic-level=error --max-diagnostics 0 src/"
}
```
