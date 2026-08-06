# typescript-lsp

TypeScript/JavaScript language server for Claude Code, providing code intelligence features like go-to-definition, find references, and error checking.

## Supported Extensions
`.ts`, `.tsx`, `.js`, `.jsx`, `.mts`, `.cts`, `.mjs`, `.cjs`

## Why this plugin

The LSP plugins in the official marketplace ship their `lspServers` config only in the marketplace-level `marketplace.json` — the plugin directories themselves contain nothing but a `README.md`. Because installing a plugin copies its source directory into the plugin cache, the installed copy ends up with no LSP configuration at all, and Claude Code reports **"No LSP server available for file type."**

The usual workaround is to hand-write the missing manifest into the marketplace cache, which gets wiped on the next reinstall or update. See [claude-code#15619](https://github.com/anthropics/claude-code/issues/15619#issuecomment-4027578739) and [claude-plugins-official#378](https://github.com/anthropics/claude-plugins-official/pull/378) for the diagnosis.

This plugin keeps its `lspServers` config in its own `.claude-plugin/plugin.json`, so the configuration travels with the plugin and survives installation.

## TypeScript 7

This plugin drives TypeScript 7's language server directly with `tsc --lsp --stdio`. TypeScript 7 is the [native Go port of the compiler](https://github.com/microsoft/typescript-go), so the server starts faster and uses less memory than the previous JavaScript-based `tsserver` wrapper — a meaningful difference on large projects, where language-server startup was often the slowest part of the loop.

TypeScript 7 or newer is required. Check with `tsc --version`.

## Installation

Install TypeScript globally via npm:

```bash
npm install -g typescript
```

Or with pnpm:

```bash
pnpm add -g typescript
```

## More Information
- [typescript on npm](https://www.npmjs.com/package/typescript)
- [microsoft/TypeScript](https://github.com/microsoft/TypeScript)
- [microsoft/typescript-go](https://github.com/microsoft/typescript-go) — the native Go implementation
