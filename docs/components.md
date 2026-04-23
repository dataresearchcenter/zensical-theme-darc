# Components

Showcase of every reusable rendering feature wired up by the DARC zensical
theme. Copy the markdown blocks as templates for your own pages.

## Admonitions

Each variant uses a different DARC palette accent, scaled per scheme.

!!! note
    Lorem ipsum dolor sit amet, consectetur adipiscing elit. Notes use the
    purple accent.

!!! info
    Sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.

!!! tip
    Ut enim ad minim veniam, quis nostrud exercitation. Tips use green.

!!! success
    Duis aute irure dolor in reprehenderit in voluptate velit esse cillum.

!!! warning
    Excepteur sint occaecat cupidatat non proident, sunt in culpa qui
    officia deserunt. Warnings use yellow-orange.

!!! danger
    Mollit anim id est laborum. Danger uses the orange ember.

!!! example
    Falls back to the default DARC ember accent.

??? note "Collapsible note (click to expand)"
    Same styling, but rendered from `???` for a `<details>` element.

## Code blocks

Inline `code()` snippets get a panel chip background. Block code uses a
filename header with a small ember dot:

``` python title="example.py"
from anyio import run

async def main() -> None:
    print("hello, world")

run(main)
```

``` bash title="install.sh"
#!/usr/bin/env bash
set -euo pipefail
poetry install --with dev --all-extras
```

## Content tabs

=== "Python"

    ``` python
    def greet(name: str) -> str:
        return f"hello, {name}"
    ```

=== "Bash"

    ``` bash
    echo "hello, $1"
    ```

=== "JSON"

    ``` json
    {"greeting": "hello", "to": "world"}
    ```

## Tables

| Feature       | Status   | Notes                         |
| ------------- | -------- | ----------------------------- |
| Light scheme  | shipped  | warm paper background         |
| Dark scheme   | shipped  | near-black with ember accent  |
| Lucide icons  | shipped  | admonitions + social links    |
| Per-site logo | shipped  | swap via `extra.logo_light`   |

## Blockquote

> Quote with an ember left rule. Lorem ipsum dolor sit amet, consectetur
> adipiscing elit. Sed do eiusmod tempor incididunt ut labore et dolore.

## Lists

- First item — bullets use the ember accent
- Second item with **bold** text and a `code` chip
- Third item with [a link](#admonitions) that hovers to body color

1. Ordered item one
2. Ordered item two
3. Ordered item three

## Task list

- [x] Wire up DARC palette
- [x] Light + dark scheme tokens
- [ ] Customize for your project

## Footnote

Inline reference[^1] renders as a superscript link to the bottom of the
page.

[^1]: This is the footnote body. It picks up the muted body color and a
      thin top divider.

## Buttons

[Primary action](#){.md-button .md-button--primary}
[Secondary action](#){.md-button}
