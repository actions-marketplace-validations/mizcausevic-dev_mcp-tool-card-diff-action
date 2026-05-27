# Changelog

## v0.1.0 — 2026-05-27

- Initial release: GitHub Action wrapping `mcp-tool-card-diff` as a per-PR MCP Tool Card breaking-change gate.
- Inputs: `card-path` (required), `base-sha` (default `pull_request.base.sha`), `comment-on-pr` (auto/true/false), `fail-on-breaking` (default true), `fail-on-any-change` (default false), `github-token`.
- Outputs: `breaking`, `change-count`, `new-card`.
- Vendored `diffToolCards()` + `toMarkdown` from `mcp-tool-card-diff`.
- Same diff-action template as `agent-card-diff-action`: retrieves the previous version of a tool card via `git show <base.sha>:<card-path>`, diffs against HEAD, posts diff as PR comment, fails on breaking.
- Handles 3 edge cases: newly-added card (no previous version), malformed previous version, missing card-path on disk.
- Composite Node 20 action with `dist/index.js` committed for SHA/tag pinning.
- 14 tests with injected `gitShow` for hermetic execution.
- 3 fixtures inherited from `mcp-tool-card-diff` (v1, v2-breaking, v2-nonbreaking).
- **Second in the per-protocol diff Action quintet** — follows `agent-card-diff-action`; next up: prompt-provenance-diff-action, evidence-bundle-diff-action, otel-genai-diff-action.
- Node 20/22 CI (lint, typecheck, coverage, build, `npm audit`), AGPL-3.0-or-later, Dependabot.
