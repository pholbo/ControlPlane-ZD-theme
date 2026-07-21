# ControlPlane-ZD-theme

Zendesk theme source for the External and Internal help centres. These are two separate Zendesk Guide installs, each getting its own theme package, sharing a common base stylesheet with per-centre overrides.

## Structure

- `shared/base.css` — Copenhagen-based styles common to both help centres, using Zendesk's `$variable` theme-settings syntax (resolved via each centre's `manifest.json`, not plain CSS — expect editor warnings here)
- `external/overrides.css` — External help centre specific styles, imports `shared/base.css`
- `external/manifest.json` — theme settings/variables for the External package
- `internal/overrides.css` — Internal help centre specific styles, imports `shared/base.css`
- `internal/manifest.json` — theme settings/variables for the Internal package

## Deploying

Each help centre needs a fully self-contained theme package (manifest + templates + style.css + assets) — Zendesk doesn't resolve the `@import "../shared/base.css"` across separately installed themes. Before packaging for `zcli themes:import`/upload, merge `shared/base.css` + the centre's `overrides.css` into one `style.css` per package.

`templates/`, `script.js`, and `assets/` from the original Copenhagen export aren't in this repo yet — add per-centre once branding/content decisions are locked in.
