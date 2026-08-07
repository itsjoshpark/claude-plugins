# typescript-lsp

TypeScript/JavaScript language server for Claude Code, providing code intelligence features like go-to-definition, find references, and error checking.

## Supported Extensions
`.ts`, `.tsx`, `.js`, `.jsx`, `.mts`, `.cts`, `.mjs`, `.cjs`

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
