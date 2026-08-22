# Three Skies — weekend weather

Design canvas source for a weekend forecast app covering San Francisco,
London and Tokyo, each with its own flat-vector city illustration.

Published canvas: https://claude.ai/code/artifact/c7894475-c1bf-40a9-9934-4529ba016941

## Files

| File | What it is |
| --- | --- |
| `Main.dc.html` | Desktop app, three city cards side by side. Interactive. |
| `Phone.dc.html` | 390x844 mobile version with a city switcher. Interactive. |
| `DirectionB.dc.html` | Low-fi alternate direction: dark "night sky" list. |
| `DirectionC.dc.html` | Low-fi alternate direction: departure-board / ticket. |
| `canvas.json` | Artboard positions, sticky notes, launch view. |
| `three-skies-weekend-weather.html` | Generated canvas. Do not edit by hand — re-seed instead. |

## Note on the data

Every forecast value is sample data — plausible late-August figures for
Sat 22 / Sun 23 August 2026, not a live feed. Replace before real use.

## Re-generating the canvas

Edit the `.dc.html` files and `canvas.json`, then re-seed a fresh copy with
the `/design` skill's helper (`seed-canvas.mjs --template ... --out
three-skies-weekend-weather.html --title "Three Skies" --artboard ... --canvas
canvas.json`) and republish to the same artifact URL. Never edit the generated
HTML directly.
