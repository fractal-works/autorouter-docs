# AutoRouter in Terminal

Source: [autorouter.com/integrations/terminal](https://autorouter.com/integrations/terminal)

Coding agents in your terminal route the same way as their apps. Turn each one
on in the AutoRouter Mac app and pick AutoRouter in its model picker. Nothing
to export and no API keys.

**Works in:** Terminal, iTerm2, Ghostty or any other terminal app, on macOS 14
or later.

## Pick AutoRouter in each CLI

| CLI | Pick AutoRouter with | Setup |
| --- | --- | --- |
| Claude Code (2.1.242+, Node 22.18+) | `/model`, or `claude --model auto-claude-route` | [claude-code.md](claude-code.md) |
| Codex CLI | `/model`, or `codex -m autorouter` | [codex.md](codex.md) |
| OpenCode (1.x, 2.x) | `/models`, or `opencode -m autorouter/autorouter` | [opencode.md](opencode.md) |
| Pi (0.62+) | `/model`, with no restart | [pi.md](pi.md) |

## Set up

1. **Install the Mac app.** [Download AutoRouter](https://autorouter.com/AutoRouter.dmg),
   sign in or create a free account, then connect your plans.
2. **Turn on each CLI.** Click Enable on its row, in setup or in Settings,
   under Apps.
3. **Start a new session.** A session that was already open picks up the
   change once you start it again. OpenCode 2.x reloads on its own, and Pi
   needs no restart.
4. **Pick AutoRouter.** Choose it in the CLI's model picker. It also starts as
   each CLI's default model.

## What changes

- **No shell changes.** AutoRouter writes to each CLI's settings file, not to
  your shell profile, and runs no local proxy. So a CLI routes the same in
  every terminal app and every window, with no environment variables to set.
- **One file per CLI:**
  - Claude Code: `~/.claude/settings.json`
  - Codex: `~/.codex/config.toml`, shared with the Codex app
  - OpenCode: `~/.config/opencode/opencode.json`
  - Pi: `~/.pi/agent/models.json`
- **Your default comes back.** The first time, AutoRouter becomes each CLI's
  default model and remembers the one it replaced. A model you pick later
  stays yours. Turning a CLI off puts your old default back.

## Plans

The plans you connect in AutoRouter: Claude, ChatGPT, Grok and Gemini. Claude
Code and Codex also keep their own sign-ins. Models no plan covers run on
credits.

## Limits

- Mac only, macOS 14 or later.
- AutoRouter sometimes misjudges how hard a task is. Rate the pick, or choose
  a model yourself.
