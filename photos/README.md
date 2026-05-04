# photos/

The Yelp landing page expects these eight image files in this directory.
Drop them in and they will render automatically — no code changes needed.
The page degrades gracefully when files are missing (a soft warm-paper
tone fills the slot), so it's safe to deploy before all photos arrive.

## Expected files

```
photos/logo.png               — Anytime Welding logo (used in topbar, footer, website-callout)
photos/stair-glass-rail.jpg   — Hero image, stainless stair w/ glass infill
photos/pergola.jpg            — Gallery: powdercoated aluminum pergola
photos/laser-cut-gate.png     — Gallery: stainless gate with laser-cut infill
photos/shop-trucks.png        — Gallery: portable welding trucks at shop
photos/seismic-anchoring.jpeg — Gallery: seismic tool anchoring
photos/shop-fab.jpg           — Gallery: shop fabrication
photos/aluminum-kiosk.jpeg    — Gallery: structural aluminum (TecMart kiosk)
```

## Notes on file format

- Filenames are case-sensitive on GitHub Pages — match exactly.
- Extensions are case-sensitive too: `.jpg` ≠ `.JPG` ≠ `.jpeg`. Use the
  exact extension shown above.
- Recommended: keep each gallery image under ~600 KB. The hero image
  can be larger (up to ~1.5 MB) since it loads with the first paint.
- Recommended dimensions:
  - `logo.png`: 400 × 400 px PNG with transparent background (rendered
    at 112 px in topbar, 60 px in footer, 90 px in website-callout).
  - `stair-glass-rail.jpg`: 1600 × 2000 px (hero is a 4:5 portrait).
  - Gallery tiles: 1200 × 900 px landscape works well for the
    2-column desktop grid. The big tile (`pergola.jpg`) gets twice the
    vertical real estate, so a slightly taller crop is fine.

## To verify after upload

Open `index.html` in a browser (or push to GitHub Pages and visit
`start.anytimewelding.com`) and confirm every image loads. Use the
browser dev-tools Network tab to spot any 404s — those will be
filename mismatches.
