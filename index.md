---
layout: default
title: Pikidex Decor Collection Data
published: true
last_modified_at: 2025-11-01
---


Community-maintained dataset for the Pikidex app — a companion for *Pikmin Bloom* that helps track and organize your Pikmin decor collection.


## 📦 About

This repository hosts the public JSON file with up-to-date Pikmin decor data, curated and verified by the Pikidex community.

- Source file: [`pikidex.json`](./pikidex.json)
- Format: standard JSON, compatible with the Pikidex mobile app
- Updates: community contributions are welcome via pull requests
- Website: [https://monjuik.github.io/pikidex-db](https://monjuik.github.io/pikidex-db)

## Pikidex.json format

### Main Collection Structure

  - Root JSON exposes `collection`, which the app loads into its "Decor Collector".
  - `collection` is an ordered array; each element maps directly to a PikminGroup.
  - Entries are read as-is, so their order and optional fields are preserved for display logic.

### Example

``` json
{
  "icon": "restaurant",
  "name": "Restaurant",
  "translations": {
    "en": "Restaurant — Chef Hat",
    "es": "Restaurante — Gorro de Chef",
    "de": "Restaurant – Seltene Kochmütze",
    "ja": "レストラン — シェフハット"
    },
  "osmTags": ["amenity=restaurant"],
  "pikmins": [
    {
      "id": 1,
      "color": "red"
    },
    {
      "id": 2,
      "color": "yellow"
    },
    {
      "id": 3,
      "color": "blue"
    },
    {
      "id": 4,
      "color": "white"
    },
    {
      "id": 5,
      "color": "purple"
    },
    {
      "id": 6,
      "color": "grey"
    },
    {
      "id": 7,
      "color": "pink"
    },
    {
      "id": 8,
      "color": "lightBlue"
    }
  ]
}
```

###  Pikmin Group Object

  - `icon` names a Material icon (or single glyph) and `color` holds one of `red`, `yellow`, `blue`, `white`, `purple`, `grey`, `pink`, `green`, `lightBlue` to tint the badge. NB, not all icons are available in the app.
  - `name` is the default English title. `name` is used to form a key for storing progress on your device, that's why we should think of backward compatability and change it only in really needed cases.
  - `translations` is a locale→string map letting the app surface the right caption per user locale. Locale uses  [IANA Language Subtag
Registry](https://www.iana.org/assignments/language-subtag-registry/language-subtag-registry), supported by Pikidex:
    - `en`
    - `fr`
    - `es`
    - `de`
    - `it`
    - `pt`
    - `ja`
    - `ko`
  - `pikmins` lists the group’s members in order; each item is a Pikmin entry described below.
  - `availableFrom` captures the first known release date.
  - `isSeasonal` toggles limited-time sets, with `seasonStart`/`seasonEnd` (ISO 8601 strings) framing the window.
  - `isRegional` flags location-locked sets, while `osmTags` enumerates relevant OpenStreetMap tag selectors for real-world POIs.
  - Unsupported JSON-fields are ignored.
  - Unsupported values (for color, icon) are converted to default values.

###  Pikmin Entry

  - `id` is the numeric identifier the app uses for progress tracking and look-ups.
  - `color` repeats the Pikmin colour keyword so UI elements can render with the correct hue.


## 🧑‍💻 Contributing

Report issues or suggest improvements at [GitHub](https://github.com/monjuik/pikidex-db/issues).

You can help keep the dataset accurate and current:

1. Fork this repository
2. Update `pikidex.json` (add new items, fix names, etc.)
3. Submit a Pull Request with a short description of your changes

Before submitting, please validate the JSON format.


## ⚖️ License

© 2025 Pikidex Community
Licensed under the [Creative Commons Attribution–NonCommercial 4.0 International (CC BY-NC 4.0)](https://creativecommons.org/licenses/by-nc/4.0/).

> Commercial redistribution, resale, or integration of this dataset into paid or ad-monetized applications is strictly prohibited.
