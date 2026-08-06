# claude-plugins

A personal Claude Code **plugin marketplace**. Each plugin lives in `plugins/<name>/` and carries its own manifest.

```
.claude-plugin/marketplace.json          # marketplace manifest (name, owner, plugin list)
plugins/<name>/.claude-plugin/plugin.json # per-plugin manifest — components live HERE
plugins/<name>/README.md                  # user-facing docs for that plugin
```

## Non-obvious constraints

**The marketplace `name` is `itsjoshpark`, not `claude-plugins`.** Claude Code rejects `claude-plugins` outright with *"name impersonates an official Anthropic/Claude marketplace"*, and the marketplace then fails to load. Do not "fix" the name to match the repo directory. The repo slug and the marketplace name are independent:

- `/plugin marketplace add itsjoshpark/claude-plugins` — the GitHub slug (where to fetch)
- `/plugin install typescript-lsp@itsjoshpark` — the `name` field (what users type)

Any new marketplace name must avoid `claude`/`anthropic` prefixes; see the reserved-names list in the [marketplace docs](https://code.claude.com/docs/en/plugin-marketplaces).

**Component configs (`lspServers`, `mcpServers`, hooks, …) belong in the plugin's `plugin.json`, never only in `marketplace.json`.** Installing a plugin copies its source directory into the plugin cache. Config that exists only in `marketplace.json` never reaches the cache, and the plugin silently does nothing — this is exactly the upstream bug that `typescript-lsp` exists to work around ([claude-code#15619](https://github.com/anthropics/claude-code/issues/15619#issuecomment-4027578739), [claude-plugins-official#378](https://github.com/anthropics/claude-plugins-official/pull/378), closed unmerged). Keep a single copy in `plugin.json`; mirroring it into `marketplace.json` just creates drift.

## Verify before committing

```bash
claude plugin validate .                      # marketplace manifest
claude plugin validate plugins/<name>         # each plugin manifest
```

Both must pass with `--strict` (it promotes warnings to errors — notably a missing `version`). Manifests are strict JSON: no trailing commas, no comments.

`.github/workflows/validate.yml` runs exactly these checks on every push and PR. It installs the CLI unpinned, so a tightening of Claude Code's validation rules surfaces as a CI failure rather than a broken marketplace for users — that is intentional; fix the manifest rather than pinning the version.

For LSP plugins, also confirm the server binary actually speaks the configured flags before trusting the config, e.g. `tsc --lsp` exits with `only stdio is supported`, which proves `--lsp` is dispatched.

## Adding a plugin

1. Create `plugins/<name>/.claude-plugin/plugin.json` with `name`, `description`, `version` (semver), `author`, and its component config.
2. Add a `plugins[]` entry to `.claude-plugin/marketplace.json` with `name`, `description`, `author`, `source: "./plugins/<name>"`, `category`.
3. Write `plugins/<name>/README.md` — what it does, prerequisites, install steps.
4. Add a row to the root `README.md` table.
5. Validate as above.

Bump the plugin's `version` on any user-visible change; that field is how Claude Code tracks updates.

## Commits

Use [Conventional Commits](https://www.conventionalcommits.org/): `type(scope): summary`.

Scope is the plugin name, or `marketplace` for repo-level manifest/docs changes.

```
feat(typescript-lsp): use TypeScript 7 native language server
fix(marketplace): rename marketplace to avoid impersonation check
docs(typescript-lsp): document pnpm install path
chore(marketplace): add plugin manifest validation
```

Use `feat`/`fix`/`docs`/`refactor`/`chore`. Breaking changes get a `!` before the colon and a `BREAKING CHANGE:` footer.
