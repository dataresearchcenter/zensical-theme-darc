# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this repo is

A drop-in boilerplate for DARC documentation sites built with [zensical](https://zensical.org/) (a mkdocs-material drop-in). It bundles the shared DARC design system, per-scheme logo handling, and custom hero/stats components for the home page. There is no Python packaging — the only dependency is the `zensical` CLI, installed directly with `pip`.

## Commands

```bash
pip install zensical
zensical serve   # → http://127.0.0.1:8000 (live reload)
zensical build   # → ./site
```

There are no tests or linters — this is a static-site config repo. Validate changes by running `zensical serve` and visually checking both light/dark schemes (toggle via the sun/moon button).

## Architecture

The site's appearance comes from two layers stacked in `mkdocs.yml` under `extra_css` — order matters:

1. **`docs/stylesheets/darc-zensical.css`** — the shared DARC design system. Declares `@font-face` for Inter + Sligoil Micro (font files served from `cdn.investigativedata.org/style/fonts/…`) and holds palette tokens, per-scheme admonition/syntax colors, typography, and hero + stats components. **This file is shared across all DARC docs sites and must stay in sync upstream.** Do not put project-specific tweaks here; copy design-system improvements back upstream instead.
2. **`docs/stylesheets/extra.css`** — project-specific overrides. Loaded last so it wins. Add per-site styling here.

### Home page / hero

- `docs/index.md` is nearly empty — it only carries front-matter `template: home.html` plus `hide:` rules. All visible content lives in `docs/overrides/home.html`.
- `home.html` extends `base.html`, blanks `{% block tabs %}` and `{% block footer %}`, and fills `{% block hero %}` with `.darc-hero` + `.darc-stats` markup. Stats values render in the mono display font and work best at ≤6 uppercase characters.
- Customizing a new project means editing the hero title / lede / CTA buttons / stats rows in `home.html` and adjusting `site_name`, `site_url`, optional `repo_url`, and `nav` in `mkdocs.yml`.

### Per-scheme logo

`docs/overrides/partials/logo.html` emits **both** logo variants into the DOM:

- `config.theme.logo` → dark-mode variant (Neg), class `md-logo__img--dark`
- `config.extra.logo_light` → light-mode variant (Pos), class `md-logo__img--light`

Visibility is toggled entirely in CSS via `[data-md-color-scheme="slate"]` / `"default"` selectors in `darc-zensical.css`. If you swap the logo, update both `theme.logo` and `extra.logo_light` in `mkdocs.yml`.

### Footer

`docs/overrides/partials/copyright.html` overrides the default mkdocs-material copyright block with DARC's attribution. It respects `config.extra.generator` for the "Made with Zensical" line.

## Conventions

- Markdown extensions enabled: `admonition`, `attr_list` (required for `{ .md-button }` button syntax), `md_in_html`, `footnotes`, `pymdownx.details`/`highlight`/`inlinehilite`/`snippets`/`superfences`/`tabbed`/`tasklist`. When adding new content, prefer these over custom HTML.
- Icons: Lucide (`lucide/<name>`) is the default set for UI glyphs (admonitions, palette toggles, mail/globe social links). Lucide does **not** ship brand logos — use `simple/<brand>` (e.g. `simple/github`) or `fontawesome/brands/<brand>` for those. Bundled sets live under `<zensical>/templates/.icons/`: `lucide`, `simple`, `material`, `fontawesome`, `octicons`.
- The palette tokens in `darc-zensical.css` use the `--oa-*` prefix (from the OpenAleph design handoff the system was adapted from). Reference these rather than hard-coding colors.
