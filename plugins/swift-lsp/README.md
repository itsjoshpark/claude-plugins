# swift-lsp

Swift language server (SourceKit-LSP) for Claude Code, providing code intelligence for Swift projects.

## Supported Extensions
`.swift`

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

SourceKit-LSP is included with the Swift toolchain.

### macOS
Install Xcode from the App Store, or install Swift via:
```bash
brew install swift
```

### Linux
Download and install Swift from [swift.org](https://www.swift.org/download/).

After installation, `sourcekit-lsp` should be available in your PATH.

## More Information
- [SourceKit-LSP GitHub](https://github.com/apple/sourcekit-lsp)
- [Swift.org](https://www.swift.org/)
