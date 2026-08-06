# clangd-lsp

C/C++ language server (clangd) for Claude Code, providing code intelligence, diagnostics, and formatting.

## Supported Extensions
`.c`, `.h`, `.cpp`, `.cc`, `.cxx`, `.hpp`, `.hxx`, `.C`, `.H`

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
brew install llvm
# Add to PATH: export PATH="/opt/homebrew/opt/llvm/bin:$PATH"
```

### Via package manager (Linux)
```bash
# Ubuntu/Debian
sudo apt install clangd

# Fedora
sudo dnf install clang-tools-extra

# Arch Linux
sudo pacman -S clang
```

### Windows
Download from [LLVM releases](https://github.com/llvm/llvm-project/releases) or install via:
```bash
winget install LLVM.LLVM
```

## More Information
- [clangd Website](https://clangd.llvm.org/)
- [Getting Started Guide](https://clangd.llvm.org/installation)
