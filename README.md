# Density reproduction

One `<Image>` uses `densities={[1, '1x', 2]}` with a generated 1200 × 840 PNG, rendered at 400 × 280.

[View the reproduction on GitHub Pages](https://yusaku01.github.io/astro-image-densities-repro/).

## Reproduction of duplicate densities

Use Node.js **22.23.4 or newer** and pnpm 12.4.2.

```sh
git clone https://github.com/Yusaku01/astro-image-densities-repro.git
cd astro-image-densities-repro
pnpm install --frozen-lockfile
pnpm build
pnpm preview
```

Open the URL shown by `pnpm preview` in your browser.
The “Actual srcset from the image” section reads the rendered image's `srcset` property; its output is not hardcoded.

- Expected: one `1x` candidate and one `2x` candidate.
- Actual in Astro 7.4.2: `1x, 1x, 2x`; the first two candidates have identical URLs.

- The project uses static output and Astro's default image service, with no adapters or integrations.
- The PNG was generated specifically for this reproduction.
- The `site` and `base` settings support the GitHub Pages project URL.
- The deployment uses the [official Astro GitHub Pages action](https://docs.astro.build/en/guides/deploy/github/).
