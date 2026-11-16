# Changelog

Changes to the AutoRouter plugin, MCP config and setup skill in this
repository. The AutoRouter Mac app has its own changelog at
[autorouter.com/changelog](https://autorouter.com/changelog).

## 1.0.0 (2026-11-16)

First release.

- Claude Code plugin `autorouter`, installable from this repository's
  marketplace with `claude plugin marketplace add fractal-works/autorouter-docs`
  and `claude plugin install autorouter@fractal-works`.
- The plugin adds the `autorouter-models` MCP server at
  `https://api.autorouter.com/v1/mcp/public`. It needs no account and has two
  tools: `list_models` and `recommend_model`.
- `set-up-autorouter` skill, run as `/autorouter:set-up-autorouter` or added
  on its own with `npx skills add fractal-works/autorouter-docs`. It installs
  the Mac app and checks that Claude Code, Codex and Cursor are connected.
- Public docs: install, supported tools, how routing works, pricing and FAQ.
