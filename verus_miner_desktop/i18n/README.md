# VerusMiner downloadable language packs

JSON packs for optional UI translation. English is also built into the app
(`lib/features/i18n/values/builtin_strings_en.dart`); other languages download
or can be copied into the CDN folder for testing.

## Catalog (manual)

| File | Purpose |
|------|---------|
| `i18n.json` | **Main catalog** of supported languages → pack files |

Edit `i18n.json` on the assets repo to add or remove languages **without** an app
release. Shape:

```json
{
  "version": 1,
  "fallback": "en",
  "languages": [
    {
      "code": "en",
      "englishName": "English",
      "nativeName": "English",
      "file": "en.json"
    },
    {
      "code": "es",
      "englishName": "Spanish",
      "nativeName": "Español",
      "file": "es.json"
    }
  ]
}
```

- `fallback`: language code used when a pack fails (English builtin is always last resort).
- `file`: pack filename under the same `i18n/` folder (can differ from `{code}.json`).
- If the catalog cannot be downloaded, the app uses its shipped builtin list.

## Pack files

| File     | Language |
|----------|----------|
| `en.json` | English (reference) |
| `es.json` | Spanish Español |
| `de.json` | German Deutsch |
| `fr.json` | French Français |
| `pl.json` | Polish Polski |
| `id.json` | Indonesian Bahasa Indonesia |
| `zh.json` | Chinese 中文 |
| `ja.json` | Japanese 日本語 |
| `ko.json` | Korean 한국어 |
| `hi.json` | Hindi हिन्दी |
| `ru.json` | Russian Русский |
| `ar.json` | Arabic العربية |

## App load URL

```
{AppSetting.ghAssetsBaseUrl}/i18n/i18n.json
{AppSetting.ghAssetsBaseUrl}/i18n/{file from catalog}
```

Example: `…/i18n/i18n.json` then `…/i18n/zh.json`

## Format (pack JSON)

Flat JSON object: `"key": "translated string"`.

- Placeholders must stay as `{name}`, `{pool}`, etc.
- Multi-line help text uses `\n`.
- Product names (VerusMiner, Verus, VRSC, …) stay untranslated.

## Local testing

1. Host these files under your assets base URL path `i18n/`, **or**
2. Temporarily point `ghAssetsBaseUrl` at a local/static server that serves this folder.
3. In the app: **General setting → Language** and pick a pack (online download).
4. Use **Refresh languages** under the language dropdown to re-download the catalog,
   the current pack, and `assets.json`.

First-run language screen uses the catalog when available, else `AppLocaleOption.builtin`.
