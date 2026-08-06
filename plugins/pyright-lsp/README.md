# pyright-lsp

Python language server (Pyright) for Claude Code, providing static type checking and code intelligence.

## Supported Extensions
`.py`, `.pyi`

## Why this plugin

The LSP plugins in the official marketplace ship their `lspServers` config only in
the marketplace-level `marketplace.json` — the plugin directories themselves contain
nothing but a `README.md`. Because installing a plugin copies its source directory
into the plugin cache, the installed copy ends up with no LSP configuration at all,
and Claude Code reports **"No LSP server available for file type."**

See [claude-code#15619](https://github.com/anthropics/claude-code/issues/15619#issuecomment-4027578739)
and [claude-plugins-official#378](https://github.com/anthropics/claude-plugins-official/pull/378)
(closed unmerged, so upstream is still affected).

This plugin keeps its `lspServers` config in its own `.claude-plugin/plugin.json`, so
the configuration travels with the plugin and survives installation.

## Installation

Install Pyright globally via npm:

```bash
npm install -g pyright
```

Or with pip:

```bash
pip install pyright
```

Or with pipx (recommended for CLI tools):

```bash
pipx install pyright
```

## More Information
- [Pyright on npm](https://www.npmjs.com/package/pyright)
- [Pyright on PyPI](https://pypi.org/project/pyright/)
- [GitHub Repository](https://github.com/microsoft/pyright)
