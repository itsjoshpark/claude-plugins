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

## License

[Apache-2.0](LICENSE)
