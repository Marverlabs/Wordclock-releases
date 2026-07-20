# Wordclock releases

Compiled firmware releases for the [Marver Labs](https://github.com/Marverlabs) Wordclock. Every clock checks `manifest.json` in this repo once a day and offers to install a new version when one is published here.

This repo intentionally contains **only compiled binaries** — no source code. The firmware source is closed.

- `manifest.json` — current version + download URLs, read by the clocks
- `firmware.bin` — compiled firmware image
- `littlefs.bin` — compiled web UI (settings page) image
