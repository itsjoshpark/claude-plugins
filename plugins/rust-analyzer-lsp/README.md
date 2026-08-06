# rust-analyzer-lsp

Rust language server for Claude Code, providing code intelligence and analysis.

## Supported Extensions
`.rs`

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

### Via rustup (recommended)
```bash
rustup component add rust-analyzer
```

### Via Homebrew (macOS)
```bash
brew install rust-analyzer
```

### Via package manager (Linux)
```bash
# Ubuntu/Debian
sudo apt install rust-analyzer

# Arch Linux
sudo pacman -S rust-analyzer
```

### Manual download
Download pre-built binaries from the [releases page](https://github.com/rust-lang/rust-analyzer/releases).

## More Information
- [rust-analyzer Website](https://rust-analyzer.github.io/)
- [GitHub Repository](https://github.com/rust-lang/rust-analyzer)
