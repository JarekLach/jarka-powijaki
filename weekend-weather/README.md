# Three Skies — weekend weather

Design canvas source for a weekend forecast app covering Döttingen
(CH-5312), Dębina (PL 76-211) and Warszawa, each with its own flat-vector
illustration.

Published canvas: https://claude.ai/code/artifact/c7894475-c1bf-40a9-9934-4529ba016941

## Files

| File | What it is |
| --- | --- |
| `Main.dc.html` | Desktop app, three place cards side by side. Interactive. |
| `Phone.dc.html` | 390x844 mobile version with a place switcher. Interactive. |
| `DirectionB.dc.html` | Low-fi alternate direction: dark "night sky" list. |
| `DirectionC.dc.html` | Low-fi alternate direction: departure-board / ticket. |
| `canvas.json` | Artboard positions, sticky notes, launch view. |
| `fetch-forecast.mjs` | Pulls the real weekend forecast and writes it into the artboards. |
| `three-skies-weekend-weather.html` | Generated canvas. Do not edit by hand — re-seed instead. |

## Data

The checked-in forecast is a **placeholder** — plausible late-August figures,
not a live feed. The artboards say so themselves: an amber strip across the top
of the desktop view reads "Placeholder forecast", and the phone hero carries a
small amber pill. Both flip to green "Live · Open-Meteo · updated ..." as soon
as `META.source` is set.

To fill in real numbers, on any machine with ordinary internet access:

```sh
node fetch-forecast.mjs --dry    # inspect what would be written
node fetch-forecast.mjs          # rewrite the data block in both artboards
```

It queries [Open-Meteo](https://open-meteo.com) (free, no API key) for the
coming Saturday and Sunday, maps WMO weather codes onto the four icons the
artboards draw, and replaces everything between the `FORECAST-DATA` markers in
`Main.dc.html` and `Phone.dc.html`. Then re-seed the canvas and republish.

Why not already done: the Claude Code remote sandbox that generated this canvas
has an egress policy that denies every weather host (open-meteo, met.no, yr.no,
IMGW, wttr.in — all 403 at the proxy). A published Artifact cannot fetch either;
its CSP allows `connect-src 'self'` plus Google Fonts and nothing else. So the
data has to be baked in at build time, by this script.

## Re-generating the canvas

Edit the `.dc.html` files and `canvas.json`, then re-seed a fresh copy with
the `/design` skill's helper (`seed-canvas.mjs --template ... --out
three-skies-weekend-weather.html --title "Three Skies" --artboard ... --canvas
canvas.json`) and republish to the same artifact URL. Never edit the generated
HTML directly.
