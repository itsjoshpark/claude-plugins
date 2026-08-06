# jdtls-lsp

Java language server (Eclipse JDT.LS) for Claude Code, providing code intelligence and refactoring.

## Supported Extensions
`.java`

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
brew install jdtls
```

### Via package manager (Linux)
```bash
# Arch Linux (AUR)
yay -S jdtls

# Other distros: manual installation required
```

### Manual Installation
1. Download from [Eclipse JDT.LS releases](https://download.eclipse.org/jdtls/snapshots/)
2. Extract to a directory (e.g., `~/.local/share/jdtls`)
3. Create a wrapper script named `jdtls` in your PATH

## Requirements
- Java 17 or later (JDK, not just JRE)

## More Information
- [Eclipse JDT.LS GitHub](https://github.com/eclipse-jdtls/eclipse.jdt.ls)
- [VSCode Java Extension](https://github.com/redhat-developer/vscode-java) (uses JDT.LS)
