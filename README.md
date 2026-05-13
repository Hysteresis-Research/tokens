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

## Versioning

Semver. Releases tagged `vX.Y.Z` are published to GitHub Packages via CI (`.github/workflows/publish.yml`).

Tag must match `package.json` version exactly — the workflow refuses mismatched tags.

## License

Proprietary — see [LICENSE](LICENSE).
