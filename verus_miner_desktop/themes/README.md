# Downloadable theme packs

Published to GitHub app-assets as:

```
{ghAssetsBaseUrl}/themes/themes.json   ← catalog (edit this to reorder / retarget)
{ghAssetsBaseUrl}/themes/{file}        ← pack from catalog entry
```

Same pattern as `i18n/i18n.json` + `i18n/{lang}.json`.

## Catalog (`themes.json`)

```json
{
  "version": 1,
  "fallback": "verus",
  "themes": [
    {
      "id": "verus",
      "englishName": "Verus",
      "nativeName": "Verus (default)",
      "file": "verus.json"
    },
    {
      "id": "dark",
      "englishName": "Dark",
      "nativeName": "Dark",
      "file": "dark.json"
    }
  ]
}
```

- `fallback`: theme id if the saved choice is missing.
- `file`: pack filename under `themes/` (can differ from `{id}.json`).
- Only **known** app theme ids are shown (`verus`, `dark`, `pangz`, `oink`, `dudezmobi`).
  Unknown ids are skipped so the app never breaks offline.
- If the catalog cannot be downloaded, the app uses its built-in list.

## Pack files

| File | Theme |
|------|--------|
| `verus.json` | Verus (default) |
| `dark.json` | Dark |
| `pangz.json` | Pangz |
| `oink.json` | 𝙊𝙞𝙣𝙠 |
| `dudezmobi.json` | Dudezmobi |

Built-in themes always work offline. Remote packs **override** colors for a known theme id.

Hex colors: `#RRGGBB` or `#AARRGGBB`.

## Local testing

1. Copy this folder to `app-assets/verus_miner/themes/` (including `themes.json`).
2. Push app-assets, or host locally and point `ghAssetsBaseUrl` there.
3. In the app: **General settings → Appearance → Refresh themes**.
