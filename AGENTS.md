> **Before any work here:** read /workspace/RESOURCES.md (team rules), your /workspace/bot-tools/<slug>.md tool list, and the game order in /workspace/NAMES.md. (Will, Nov 1, 2026)

# South Dakota Explorer — agent handoff

Static Leaflet map, same shared app as the other state explorers. This folder was copied from Utah (which was copied from Idaho) on Nov 14 2026 and then filled with South Dakota base data. `explorer/build.py` `STATE` comes from `scripts/port_build.py --restate` (marker PORT_ST). The state in every script is the folder name via `scripts/common.py` (SD, FIPS 46, 66 counties, `ls` prefix `sdx_`, service-worker prefix `sdx-`). Folder name is `south-dakota` (hyphen) wherever a dict is keyed by the folder.

Not published. No GitHub repo was created. `scripts/sync_shared.sh` was not run: Kentucky `explorer/app.js` was not edited. Shared `BST_NAME` already includes South Dakota.

Live check when published: `share/county-minnehaha.html`. Lock: `/tmp/sdx_publish.lock`. Repo slug would be `south-dakota-explorer`.

## Caps
5+ acres, 1+ acre, and near-hospital: under $550,000. Houses/Towns (`nlh` / `tha`): $350,000. No cabin category.

## Blocks
66 counties (`data/statewide/raw/sd_blocks_500k.zip`).

## What is built (Nov 14 2026, ~16:33 ET)
Preliminary `python3 explorer/build.py` succeeded: 66 counties, 62 hospitals (56 in-state + 6 border), 712 schools, 24 colleges, 34 activities, 4 airports, 26 attractions, appeal for 66 counties, climate, compare areas for Sioux Falls, Rapid City, Aberdeen, Watertown, and Pierre. Homes, permanent jobs, travel jobs, for-sale, history, ski, border, Target, big-land, and cave/falls layers are not in this build.

Trauma source: South Dakota DOH designated trauma hospitals (content updated Sep 15 2026). Community Trauma Hospitals are shown as Level IV with that note. Trauma Receiving Hospitals were not named, so they have no level. Details and skips: `/workspace/south-dakota/STATUS.md`.

## How to rerun
Pandas and geopandas scripts need a venv. `/workspace/kentucky/.venv/bin/python` is not on this machine. The run on Nov 14 used `/tmp/plains/venv` (`python3 -m venv --system-site-packages` plus `pip install geopandas`). Other scripts use `/usr/bin/python3`.

Do not run `forsale`, `perm_jobs`, `travel_jobs`, `listings_build`, or `publish.sh` until those jobs are assigned. Do not import `perm_jobs` or `travel_jobs` just to check them. `scripts/build_hospital_systems.py` has an early exit for this folder that groups `data/hospitals.json` and does not import Vermont `spec.py`.

RN wages: O*NET May 2025 state median only. BLS county HTML was not fetched after Nebraska's page returned HTTP 403. Do not invent county or metro wages.

Airports still missing coordinates, so they are not on the map: Rapid City Regional Airport, Aberdeen Regional Airport, Denver International Airport.
