# Wordclock releases

Compiled firmware releases for the [MarverLabs](https://github.com/Marverlabs) Wordclock. Every clock checks `manifest.json` in this repo once a day and offers to install a new version when one is published here.

This repo intentionally contains **only compiled binaries** — no source code. The firmware source is closed.

- `manifest.json` — current version + download URLs, read by the clocks
- `firmware.bin` — compiled firmware image
- `littlefs.bin` — compiled web UI (settings page) image
- `beta/` — build under test, served only to the clocks whose device ID is
  listed in the manifest's `beta.devices`

## Beta channel

A clock listed in `beta.devices` reads the nested `beta` block instead of the
top-level fields; every other clock ignores `beta` entirely and sees only the
stable release. Firmware older than 3.8.1 doesn't know the key at all, which
is what makes it safe to leave in place.

To test a build: put it in `beta/`, set `beta.version` to the version string
the binary was built with, and wait for the test clock to offer it.

To promote: build the release **once more** with the suffix dropped, and put
that build in **both** the root and `beta/`, with the release version in
**both** `version` fields. Never move the beta binaries across — an image
that calls itself `3.9.5-b3` under a manifest offering `3.9.5` is reinstalled
on every check, forever. And never leave `beta` pointing at the old test
build — a listed clock reads only that block, and would be stranded on it.

The full step-by-step lives in the firmware repo's README.
