# HârnWorld Location Module: Getha Keep
[![Version (latest)](https://img.shields.io/github/v/release/toastygm/hm-loc-getha)](https://github.com/toastygm/hm-loc-getha/releases/latest)
[![Forge Installs](https://img.shields.io/badge/dynamic/json?label=Forge%20Installs&query=package.installs&suffix=%25&url=https%3A%2F%2Fforge-vtt.com%2Fapi%2Fbazaar%2Fpackage%2Fhm-loc-getha&colorB=4aa94a)](https://forge-vtt.com/bazaar#package=hm-loc-getha)
[![GitHub downloads (latest)](https://img.shields.io/badge/dynamic/json?label=Downloads@latest&query=assets[?(@.name.includes('zip'))].download_count&url=https://api.github.com/repos/toastygm/hm-loc-getha/releases/latest&color=green)](https://github.com/toastygm/hm-loc-getha/releases/latest)

Getha Keep is a "Location Module" for the Foundry VTT system. This location module
is designed to depict the Getha Keep in the far northeast of the Kingdom of Kaldor, on
the island of Hârn in the [HârnWorld](https://columbiagames.com/harnworld/) fantasy
setting; however, this manor could be adapted to exist anywhere in any fantasy setting.

Although designed for use with the [HârnMaster](https://foundryvtt.com/packages/hm3)
system, this module is mostly system-agnostic.  Detailed descriptions of the actors
has been provided in journal entries to facilitate conversion to other game systems.

Getha is the largest village in Fethael Hundred. The seat and ancestral home of the
Indama clan, this village also provides goods and services to Silver Way caravans
and travelers.

# Maps

The original maps from this work have been used as inspiration, and new maps have been
designed specifically to meet the requirements of the VTT environment.  The following
maps are part of this module.

## Getha Village

Map of Getha Village, including the keep.

<img src="assets/scenes/getha-area-player.png" alt="Getha Village" width="600"/>

## Gatehouse Inn

Cellar.

<img src="assets/scenes/gatehouse-inn-cellar.webp" alt="Gatehouse Inn Cellar" width="600"/>

Ground floor.

<img src="assets/scenes/gatehouse-inn-ground.webp" alt="Gatehouse Inn Ground" width="600"/>

Upper floor.

<img src="assets/scenes/gatehouse-inn-2nd.webp" alt="Gatehouse Inn Upper" width="600"/>

## Leaky Bucket Inn

Cellar.

<img src="assets/scenes/leaky-bucket-cellar.webp" alt="Leaky Bucket Cellar" width="600"/>

Ground floor.

<img src="assets/scenes/leaky-bucket-ground.webp" alt="Leaky Bucket Ground" width="600"/>

Upper floor.

<img src="assets/scenes/leaky-bucket-2nd.webp" alt="Leaky Bucket Upper" width="600"/>

## Temple of Halea

Ground floor.

<img src="assets/scenes/temple-of-halea-ground.webp" alt="Temple of Halea Ground" width="600"/>

Second floor.

<img src="assets/scenes/temple-of-halea-2nd.webp" alt="Temple of Halea Second Floor" width="600"/>

Third floor.

<img src="assets/scenes/temple-of-halea-3rd.webp" alt="Temple of Halea Third Floor" width="600"/>

## Getha Keep

Cellar (Ground Level).

<img src="assets/scenes/getha-keep-0.webp" alt="Getha Keep Cellar" width="600"/>

Entry floor.

<img src="assets/scenes/getha-keep-1.webp" alt="Getha Keep First Floor" width="600"/>


Main hall floor.

<img src="assets/scenes/getha-keep-2.webp" alt="Getha Keep Second Floor" width="600"/>


Residence floor.

<img src="assets/scenes/getha-keep-3.webp" alt="Getha Keep Third Floor" width="600"/>


Roof and Towers.

<img src="assets/scenes/getha-keep-4.webp" alt="Getha Keep Fourth Floor" width="600"/>


# Credits

This module is made possible by the hard work of HârnWorld fans,
and is provided at no cost. This work is an adaptation of the article
[Getha Keep](https://www.lythia.com/harnworld/settlements/getha-keep/) available
at the HârnWorld fan site [Lythia.com](https://www.lythia.com/).

**Writer:** Joe Adams

**Original Maps:** George Kelln

**Contributor:** Robert Barfield

**Heraldry:** Matthias Janssen

**With Thanks To:** Dan Bell &amp; John Sgammato

**Adapted to Foundry VTT:** Tom Rodriguez

This module is "[Fanon](https://www.lythia.com/about/publishing-fan-written-material/)",
a derivative work of copyrighted material by Columbia Games Inc. and N. Robin Crossby.

Some assets used to create the maps in this module are from
[Forgotton Adventures](https://www.forgotten-adventures.net/).


# Development

Requires Node.js >= 24.

## Project structure

- `assets/packs/<name>/unique/` — source JSON files for each compendium pack
- `assets/templates/module.template.json` — module manifest template (version/URLs are injected at build time from `package.json`)
- `scripts/init.js` — ScenePacker integration
- `utils/` — build scripts

## Common tasks

```sh
npm install                  # install dependencies (first time / after pulling)
npm run deploy:qa            # build and deploy to local QA Foundry instance
npm run deploy:release       # build and create build/dist/module.zip
npm run release              # create GitHub release (needs GITHUB_TOKEN)
npm run clean                # remove build/
```

## Making content changes

Edit the JSON files in `assets/packs/<name>/unique/`. These are the source of truth — LevelDB packs are compiled from them at build time.

## Deploying locally for testing

Set environment variables for your Foundry data paths (in `.env.local` or your shell):

```
FOUNDRYVTT_DEV_DATA=/path/to/foundry/dev
FOUNDRYVTT_QA_DATA=/path/to/foundry/qa
FOUNDRYVTT_PROD_DATA=/path/to/foundry/prod
```

Then `npm run deploy:qa` (or `:dev` / `:prod`) will build and rsync to that instance.

## Releasing

1. Bump the version in `package.json`
2. Commit and push to `main`
3. `npm run deploy:release` — builds and creates `build/dist/module.zip`
4. `export GITHUB_TOKEN=$(gh auth token)` (or set in `.env.local`)
5. `npm run release` — creates a GitHub release with `module.zip` and `module.json` attached
