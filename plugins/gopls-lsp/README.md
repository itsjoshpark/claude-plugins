# gopls-lsp

Go language server for Claude Code, providing code intelligence, refactoring, and analysis.

## Supported Extensions
`.go`

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

Install gopls using the Go toolchain:

```bash
go install golang.org/x/tools/gopls@latest
```

Make sure `$GOPATH/bin` (or `$HOME/go/bin`) is in your PATH.

## More Information
- [gopls Documentation](https://pkg.go.dev/golang.org/x/tools/gopls)
- [GitHub Repository](https://github.com/golang/tools/tree/master/gopls)
