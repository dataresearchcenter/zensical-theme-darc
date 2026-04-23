# DARC zensical boilerplate

Drop-in starter for DARC documentation sites built with
[zensical](https://zensical.org/) (mkdocs-material drop-in). Includes the
shared DARC design system, per-scheme DARC logo, custom hero/stats
components for the home page, and a sample showcasing every supported
markdown feature.

## Layout

```
darc-zensical/
├── README.md
├── .gitignore
├── mkdocs.yml                          # site config — palette, plugins, extras
└── docs/
    ├── index.md                        # uses overrides/home.html for the hero
    ├── getting-started.md              # placeholder content
    ├── components.md                   # admonitions, tabs, code, tables…
    ├── typography.md                   # headings, body text, links
    ├── stylesheets/
    │   ├── darc-zensical.css           # shared design — copy as-is
    │   └── extra.css                   # site-specific tweaks (empty by default)
    └── overrides/
        ├── home.html                   # hero template
        └── partials/
            ├── logo.html               # per-scheme DARC logo (Neg / Pos)
            └── copyright.html          # DARC footer copyright
```

## Run it

```bash
pip install zensical
zensical serve   # → http://127.0.0.1:8000
zensical build   # → ./site
```

Open <http://127.0.0.1:8000>. Toggle light/dark via the sun/moon button in
the header — both logo variants and all palette tokens swap with the
scheme.

## Customizing for your project

1. **`mkdocs.yml`** — set `site_name`, `site_url`, optionally `repo_url`,
   adjust the `nav`, swap social links.
2. **`docs/overrides/home.html`** — rewrite the hero title, lede, CTA
   buttons, and the four `.darc-stats__row` highlights to match your
   project. Stats values work best at ≤ 6 mono uppercase characters.
3. **`docs/stylesheets/extra.css`** — add any project-specific styling
   here (custom hero classes, page-only tweaks). Loaded after the shared
   sheet so overrides win.
4. **Logo** — replace `theme.logo` (dark-mode variant) and
   `extra.logo_light` (light-mode variant) with your project URLs. Both
   should be hosted somewhere stable; the DARC logo CDN is the default.

What you should *not* touch in `darc-zensical.css` unless you're changing
the design system itself: it's shared across DARC docs sites and meant to
stay in sync. Copy improvements back upstream.

## What the design provides

- **Both color schemes** — warm paper light mode, near-black dark mode.
- **DARC palette** — full scale of grays, oranges (ember accent),
  greens, purples, yellows mapped to mkdocs-material color tokens.
- **Per-scheme admonition + syntax-highlight colors** — readable on
  either background.
- **Typography** — Inter sans + Sligoil Micro mono served from the DARC
  fonts CDN; H1 in mono, body inherits zensical's responsive scale.
- **Hero + stats card** — opt-in marketing components for the home page.
- **Lucide icons** — admonition glyphs and social links.
- **Translucent blurred header** — zensical default, kept intact.
