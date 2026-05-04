# AWI Yelp Screening Landing Page

Static HTML landing page deployed to GitHub Pages on
**`start.anytimewelding.com`**. Customers reach this page by clicking
the "Website" link from the Anytime Welding, Inc. profile on Yelp.

The job of the page is to **filter unserious leads** before they call.
Pricing, minimums, hours, and out-of-scope work are all front-and-center
so callers self-screen on the way in. The Squarespace site at
`anytimewelding.com` is unaffected by this repo.

## Files

| File | Purpose |
|---|---|
| `index.html` | The page. Static HTML, no build step, no JS framework. |
| `styles.css` | The stylesheet. Industrial / craftsman aesthetic by Claude Design. |
| `photos/` | Image assets the page references. See `photos/README.md` for the expected filenames and notes on dimensions. |
| `CNAME` | Single line `start.anytimewelding.com` — tells GitHub Pages to serve at the custom subdomain. |
| `.gitignore` | Standard ignores plus the original handoff source files. |
| `source-page.jsx` | The React component this static page was converted from. **Not deployed.** Kept in the working tree (gitignored) for reference when copy needs to change. |
| `source-styles.css` | The original stylesheet from Claude Design. **Not deployed**, gitignored — `styles.css` is the canonical copy. |
| `CLAUDE_CODE_PROMPT.md` | The original handoff brief that produced this build. **Not deployed**, gitignored. |

## Maintaining the page

There is no build step. To change copy, headline, hours, or pricing,
edit `index.html` directly. To change colors, spacing, or layout,
edit `styles.css`. The CSS at the top of `styles.css` is preserved
verbatim from the original Claude Design handoff — only the
photo-fallback override block at the very bottom of the file was
added during the static conversion.

### To preview locally before pushing

```bash
cd ~/Projects/AWI/awi-yelp/awi_yelp_handoff
python3 -m http.server 8000
# then open http://localhost:8000 in a browser
```

The page should look identical to the React Proof.

### To swap tone of voice

The body element in `index.html` carries `class="tone-friendly accent-steel"`.

- **Tone** options: `tone-friendly`, `tone-blunt`, `tone-warm`. All three
  copy variants are rendered into the HTML — the CSS hides the inactive
  two. Change the body class to switch.
- **Accent color** options: `accent-spark` (orange-red), `accent-steel`
  (blue, current default), `accent-arc` (gold). Same mechanism.

### To add or replace a photo

Drop the file into `photos/` with the exact filename listed in
`photos/README.md`. Commit, push, done. Filenames are case-sensitive
on GitHub Pages — `.jpeg` is not the same as `.JPEG`.

## Deployment notes

This repo is deployed via GitHub Pages, served from the `main`
branch root. The `CNAME` file makes it answer at the custom
subdomain. DNS for `start.anytimewelding.com` points at GitHub's
Pages servers (`185.199.108-111.153` A records plus an AAAA set,
documented in the deployment summary).

## Decisions made during the React → static conversion

A few things that were ambiguous in the JSX and got picked
autonomously:

- **TweaksPanel** (the design-tool overlay) and the floating
  "⚙ Tweaks" button were skipped — design-tool scaffolding, not
  production copy.
- **`<Sparks/>` component** was defined in the JSX but the App
  composition never rendered it, so it was skipped.
- **Default accent color** was set to `accent-steel` (blue) per the
  `TWEAK_DEFAULTS` object in the JSX, not `accent-spark` (the
  orange-red `:root` value). Change the body class if Randy prefers
  the spark accent.
- **Image fallback color** uses `var(--bg-2)` (warm paper deep tone)
  rather than the brief's suggested `--paper-deep`, because
  `--paper-deep` was never declared in the source CSS. The override
  block at the bottom of `styles.css` also defines `--paper-deep` as
  an alias for `--bg-2` so any future selector that reads it still
  works.
- **Source CSS referenced `--paper`, `--paper-2`, and `--paper-deep`**
  in the shop-address-bar block, but none were declared in `:root`.
  Aliases for all three were added in the override block at the
  bottom of `styles.css` so those tokens resolve to warm paper tones
  instead of falling back to inherit.

## Maintainer

Randy Botkins · Anytime Welding, Inc. · San Jose, CA

