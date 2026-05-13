# @hysres/tokens

Design tokens for [Hysteresis Research](https://github.com/hysres) surfaces.

A single CSS file shipping three Notebook variants (Bound / Engineer's graph pad / Archive card), each in light and dark mode, on a shared serif + 8-pt skeleton.

## Install

This package is hosted on **GitHub Packages**. Even for public packages, GitHub Packages requires authentication to install.

### 1. Create a Personal Access Token

Generate a [classic PAT](https://github.com/settings/tokens/new) with the `read:packages` scope.

### 2. Configure `.npmrc`

In your project root (or `~/.npmrc` for all projects):

```
@hysres:registry=https://npm.pkg.github.com
//npm.pkg.github.com/:_authToken=${NPM_TOKEN}
```

Then set `NPM_TOKEN` in your shell env (do **not** inline the PAT into `.npmrc` if the file is committed).

### 3. Install

```bash
npm install @hysres/tokens
```

## Usage

Import the CSS once in your app entry:

```js
import '@hysres/tokens/tokens.css';
```

Apply a variant class to `<body>` (or any container):

```html
<body class="va-dark">
  <!-- … -->
</body>
```

### Variant classes

| Class | Description |
|---|---|
| `.va-light` / `.va-dark` | **Bound notebook** — cocoa / cream paper, oxblood accent (default) |
| `.vb-light` / `.vb-dark` | **Engineer's graph pad** — graph paper substrate, blueprint blue |
| `.vc-light` / `.vc-dark` | **Archive card** — substrate-mounted card, deep oxblood + ochre |

### Shared CSS variables

| Variable | Purpose |
|---|---|
| `--paper`, `--paper-soft` | Background surfaces |
| `--ink`, `--ink-2`, `--ink-3` | Text — primary / secondary / tertiary |
| `--rule`, `--rule-soft` | Dividers / hairlines |
| `--accent` | Variant-specific accent (oxblood / blueprint / terracotta) |
| `--hilite` | Highlight (selections, marginalia, etc.) |
| `--serif`, `--serif-tight`, `--mono` | Typography stacks |
| `--grid-base` | 8-pt grid unit |

Variant B additionally exposes `--grid` / `--grid-2` for the graph-paper background.
Variant C additionally exposes `--substrate` for the mounting card.

## Examples

See [`examples/`](./examples/) for self-contained HTML files demonstrating each variant:

- [`examples/variant-a.html`](./examples/variant-a.html) — Bound notebook (cocoa + oxblood; the default used by hysres/web)
- [`examples/variant-b.html`](./examples/variant-b.html) — Engineer's graph pad (blueprint blue + grid background)
- [`examples/variant-c.html`](./examples/variant-c.html) — Archive card (substrate-mounted + ochre)
- [`examples/index.html`](./examples/index.html) — gallery linking all three
- [`examples/lockup.html`](./examples/lockup.html) — cross-variant lockup specimen + palette swatches (cycles through all 6 modes)

Each file is standalone (loads `../tokens.css` and inlines layout CSS) — open directly in a browser, or use as a starting template. To flip a variant from dark to light, swap the body class suffix (`va-dark` → `va-light`, etc).

## Brand assets

Since `v0.3.0`, this package also ships brand assets under [`assets/`](./assets/):

| File | Use |
|---|---|
| [`assets/bh-mark.svg`](./assets/bh-mark.svg) | master B-H curve mark · `currentColor` · scales 1.4–3.0 |
| [`assets/stamp.svg`](./assets/stamp.svg) | corner-stamp variant · stroke 2.6 |
| [`assets/favicon.svg`](./assets/favicon.svg) | auto-theme favicon · square 100×100 · `prefers-color-scheme` |
| [`assets/wordmark.svg`](./assets/wordmark.svg) | mark + EN wordmark · horizontal lockup |
| [`assets/wordmark-bilingual.svg`](./assets/wordmark-bilingual.svg) | mark + EN + CN 迟 滞 研 究 lockup |

Import from a Next.js / Vite / webpack-style bundler:

```ts
import bhMark from '@hysres/tokens/assets/bh-mark.svg';
```

Or copy into your `public/` directory for `<link rel="icon">` and other browser-known paths.

See [BRAND.md](./BRAND.md) for voice rules, type / color tokens, CMYK approximations, mark size scale, and the variant-to-surface map. BRAND.md is the normative brand reference; everything else in this package implements it.

## Versioning

Semver. Releases tagged `vX.Y.Z` are published to GitHub Packages via CI (`.github/workflows/publish.yml`).

Tag must match `package.json` version exactly — the workflow refuses mismatched tags.

## License

Proprietary — see [LICENSE](LICENSE).
