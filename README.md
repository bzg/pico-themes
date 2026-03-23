# Pico themes

Shared CSS themes for [topics](https://github.com/bzg/topics), [trees](https://github.com/bzg/trees), [BARK](https://github.com/bzg/bark), and [org-parse](https://github.com/bzg/org-parse).

Three themes are available:

| Theme    | File       | Brand                                     |
|----------|------------|-------------------------------------------|
| **DSFR** | `dsfr.css` | Système de Design de l'État (Blue France) |
| **SWH**  | `swh.css`  | Software Heritage (Red→Orange→Yellow)     |
| **Org**  | `org.css`  | Org-mode / Worg (Teal, indigo dark mode)  |

## What each theme covers

Each file is self-contained and styles:

- **Base elements** — body, links, headings, tables, code, blockquotes, buttons (works with org-parse bare HTML)
- **Pico CSS overrides** — `--pico-*` variables, cards, details/accordion, search, header/footer (topics, BARK)
- **BARK components** — type badges (`mark[data-type=*]`), filter buttons, status buttons, theme toggle, nav, stripe rows
- **Trees components** — `--status-*` variables, `.trees button`, `.summary`, `.score-result`, `aside.help`, progress bar
- **Dark mode** via both `prefers-color-scheme` (automatic) and `[data-theme=dark]` (BARK JS toggle)
- **Print**, reduced motion, scrollbar styling

## Usage

### Via jsDelivr CDN (recommended)

Once this repo is on GitHub, files are available via jsDelivr:

```html
<link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/bzg/themes@main/dsfr.css">
```

Pin to a specific commit for stability:

```html
<link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/bzg/themes@COMMIT_SHA/swh.css">
```

### Per project

**topics** — set `:theme-url` in config to the CDN URL.

**trees** — set `theme:` in `config.yml` to a local path or download the file:

```yaml
theme: themes/dsfr.css
```

**BARK** — add a `<link>` in `bark-html.clj`'s `html-head` function, after the Pico CDN link:

```clojure
(str "<link rel=\"stylesheet\" href=\"" pico-cdn "\">\n"
     "<link rel=\"stylesheet\" href=\"https://cdn.jsdelivr.net/gh/bzg/themes@main/swh.css\">\n")
```

**org-parse** — link the theme in the HTML output. Add after the `<style>` block in `html-template`:

```clojure
(str "  <link rel=\"stylesheet\" href=\"https://cdn.jsdelivr.net/gh/bzg/themes@main/org.css\">\n")
```

The theme `<link>` must come **after** any inline `<style>` block so it overrides the defaults.

## Dark mode

- **topics**, **trees**, **org-parse**: automatic via `prefers-color-scheme`
- **BARK**: JS toggle sets `[data-theme=dark]` on `<html>` — themes respond to both selectors

## License

CSS files in this repository are published under MPL.
