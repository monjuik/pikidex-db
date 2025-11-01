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

###  Pikmin Group Object

  - `icon` names a Material icon (or single glyph) and color holds one of `red`, `yellow`, `blue`, `white`, `purple`, `grey`, `pink`, `green`, `lightBlue` to tint the badge.
  - `name` is the default English title; `translations` is a locale→string map letting the app surface the right caption per user locale. `name` is used to form a key for storing progress on your device.
  - `pikmins` lists the group’s members in order; each item is a Pikmin entry described below.
  - `isSeasonal` toggles limited-time sets, with `seasonStart`/`seasonEnd` (ISO 8601 strings) framing the window; `availableFrom` captures the first known release date.
  - `isRegional` flags location-locked sets, while `osmTags` enumerates relevant OpenStreetMap tag selectors for real-world POIs.
  - Any omitted field simply falls back to sensible defaults in the UI (for example, booleans default to false).

###  Pikmin Entry

  - `id` is the numeric identifier the app uses for progress tracking and look-ups.
  - `color` repeats the Pikmin colour keyword so UI elements can render with the correct hue.


## 🧑‍💻 Contributing

You can help keep the dataset accurate and current:

1. Fork this repository
2. Update `pikidex.json` (add new items, fix names, etc.)
3. Submit a Pull Request with a short description of your changes

Before submitting, please validate the JSON format.


## ⚖️ License

© 2025 Pikidex Community
Licensed under the [Creative Commons Attribution–NonCommercial 4.0 International (CC BY-NC 4.0)](https://creativecommons.org/licenses/by-nc/4.0/).

> Commercial redistribution, resale, or integration of this dataset into paid or ad-monetized applications is strictly prohibited.
