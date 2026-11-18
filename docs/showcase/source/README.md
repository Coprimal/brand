# Showcase source

Re-renders `../coprimal-poster.png`: a 1200×630 poster (PNG at 2×, 2400×1260), built on `Coprimal_Brand_Identity.pdf`.

`poster.html` holds everything:

- Copy: the `STR` table (`en` only): "Coprimal" (wordmark, cased as in the brand lockup), "By devs. For devs. Still devs.", the about line "We build free, open source apps and materials so solo devs can keep loving being devs in the AI era." (two lines, broken after "materials") and "coprimal.dev".
- Colors: the brand palette as CSS variables on `:root` (Deep Navy `#11376e`, Bright Navy `#225db4`, Sky `#73a7e8`, Mist `#eaf3ff`).
- Font: Lato 700 (wordmark, URL) and 400 (tagline), loaded from Google Fonts (needs network).
- Assets, copied from the repo's `assets/` into `source/assets/`:
  - `banner.webp`: full-bleed background, scaled to 112% of the frame height and anchored right, so its waves sit right and bottom and the plain navy on the left carries the text.
  - `logo_white.png`: the symbol in the horizontal lockup (the guide's "white on dark navy surfaces").
- `coprimal.dev` sits bottom-right because the bottom-left lies on the banner's light wave (contrast too low for small text).

If the brand assets change, copy the new `assets/banner.webp` and `assets/logo_white.png` over the ones in `source/assets/` and re-render. The layout is fixed at 1200×630.

## Setup

`node_modules/` lives one level up (`docs/showcase/`), shared by every showcase version. Run `npm install` there if it is missing. `capture.mjs` drives the local Chrome; set `CHROME_PATH` if it is somewhere unusual.

## Render

Run from this folder:

```bash
node inline-assets.mjs --src poster.html --out dist/poster.html
node capture.mjs --mode poster --src dist/poster.html --size 1200x630 --format png --lang en --out ../coprimal-poster.png
```

Add a PDF with `--format pdf --out ../coprimal-poster.pdf`. Capture aborts if a font fails to load.
