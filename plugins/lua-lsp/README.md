# lua-lsp

Lua language server for Claude Code, providing code intelligence and diagnostics.

## Supported Extensions
`.lua`

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

### Via Homebrew (macOS)
```bash
brew install lua-language-server
```

### Via package manager (Linux)
```bash
# Ubuntu/Debian (via snap)
sudo snap install lua-language-server --classic

# Arch Linux
sudo pacman -S lua-language-server

# Fedora
sudo dnf install lua-language-server
```

### Manual Installation
Download pre-built binaries from the [releases page](https://github.com/LuaLS/lua-language-server/releases).

## More Information
- [Lua Language Server GitHub](https://github.com/LuaLS/lua-language-server)
- [Documentation](https://luals.github.io/)
