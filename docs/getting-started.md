# Getting started

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed do eiusmod
tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim
veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea
commodo consequat.

## Installation

Duis aute irure dolor in reprehenderit in voluptate velit esse cillum.
Excepteur sint occaecat cupidatat non proident.

```bash
# install via pip
pip install your-package

# or via uv
uv add your-package
```

## Quick example

Sunt in culpa qui officia deserunt mollit anim id est laborum.

```python
from your_package import client

with client.Session() as s:
    result = s.do_something("hello")
    print(result)
```

## Next steps

- [Components](components.md) — admonitions, tabs, code blocks, tables
- [Typography](typography.md) — headings, paragraphs, links, lists
