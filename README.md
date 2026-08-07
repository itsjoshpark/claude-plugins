# claude-plugins

Josh's Claude Code plugins.

## Usage

Add the marketplace:

```
/plugin marketplace add itsjoshpark/claude-plugins
```

Then install a plugin:

```
/plugin install typescript-lsp@itsjoshpark
```

## Plugins

| Plugin | Description |
| :-- | :-- |
| [clangd-lsp](plugins/clangd-lsp) | C/C++ language server (clangd) for code intelligence |
| [csharp-lsp](plugins/csharp-lsp) | C# language server for code intelligence |
| [gopls-lsp](plugins/gopls-lsp) | Go language server for code intelligence and refactoring |
| [jdtls-lsp](plugins/jdtls-lsp) | Java language server (Eclipse JDT.LS) for code intelligence |
| [kotlin-lsp](plugins/kotlin-lsp) | Kotlin language server for code intelligence |
| [lua-lsp](plugins/lua-lsp) | Lua language server for code intelligence |
| [php-lsp](plugins/php-lsp) | PHP language server (Intelephense) for code intelligence |
| [pyright-lsp](plugins/pyright-lsp) | Python language server (Pyright) for type checking and code intelligence |
| [ruby-lsp](plugins/ruby-lsp) | Ruby language server for code intelligence and analysis |
| [rust-analyzer-lsp](plugins/rust-analyzer-lsp) | Rust language server for code intelligence and analysis |
| [swift-lsp](plugins/swift-lsp) | Swift language server (SourceKit-LSP) for code intelligence |
| [typescript-lsp](plugins/typescript-lsp) | TypeScript/JavaScript language server for code intelligence, backed by TypeScript 7's native Go language server |

## Why these plugins exist

The LSP plugins in the official marketplace ship their `lspServers` config only in the
marketplace-level `marketplace.json` — the plugin directories themselves contain nothing
but a `README.md`. Because installing a plugin copies its source directory into the plugin
cache, the installed copy ends up with no LSP configuration at all, and Claude Code reports
**"No LSP server available for file type."**

You can see it in any local cache:

```
~/.claude/plugins/marketplaces/claude-plugins-official/plugins/swift-lsp/
  LICENSE
  README.md          ← no manifest, so nothing configures the language server
```

The usual workaround is hand-writing the missing manifest into the marketplace cache, which
gets wiped on the next reinstall. It was diagnosed in
[claude-code#15619](https://github.com/anthropics/claude-code/issues/15619#issuecomment-4027578739)
and fixed in [claude-plugins-official#378](https://github.com/anthropics/claude-plugins-official/pull/378),
which was closed unmerged — so upstream is still affected.

Every plugin here keeps its `lspServers` config in its own `.claude-plugin/plugin.json`, so
the configuration travels with the plugin and survives installation. Server commands, args
and extension mappings are otherwise identical to the official ones; `typescript-lsp` is the
one deliberate exception, using TypeScript 7's native Go language server (`tsc --lsp --stdio`)
instead of `typescript-language-server`.

## License

[Apache-2.0](LICENSE)
