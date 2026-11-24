# AutoRouter for Claude Code

Source: [autorouter.com/integrations/claude-code](https://autorouter.com/integrations/claude-code)

Turn Claude Code on in the AutoRouter Mac app and pick AutoRouter with
`/model`. Each turn goes to the model that fits it, on the AI subscriptions
you already pay for first. No API keys.

**Works in:** the Claude Code CLI, 2.1.242 or later, with Node 22.18 or later,
on macOS 14 or later.

## Set up

1. **Install the Mac app.** [Download AutoRouter](https://autorouter.com/AutoRouter.dmg),
   sign in or create a free account, then connect your plans.
2. **Turn on Claude Code.** Click Enable on Claude Code's row, in setup or in
   Settings, under Apps.
3. **Pick AutoRouter.** Start a new session with `claude`, run `/model` and
   choose AutoRouter. Or start with:

   ```sh
   claude --model auto-claude-route
   ```

4. **Keep building.** A session that was already open picks up the change
   once you start it again.

## What changes

- AutoRouter adds its address, a header that identifies your Mac, a status
  line, and AutoRouter with its recommended models to `/model` in
  `~/.claude/settings.json` (or the folder `CLAUDE_CONFIG_DIR` names). Claude
  Code's own models stay listed. It saves a copy of the file first.
- **No hooks, no proxy.** AutoRouter installs no hooks and runs nothing on
  your Mac when you send a prompt. Claude Code still signs in to your Claude
  plan itself, and AutoRouter passes that sign-in on without storing it.
- **Your default comes back.** The first time, AutoRouter becomes Claude
  Code's default model and remembers the one it replaced. A default you pick
  later stays yours. Turning Claude Code off puts your old default back.

## Plans

Claude models run on your Claude plan, through Claude Code's own sign-in. You
can also connect Claude, ChatGPT, Grok and Gemini plans in AutoRouter. Models
no plan covers run on credits. To use GPT models in Claude Code, connect your
ChatGPT plan and pick a GPT model in `/model`, or let AutoRouter pick.

## Limits

- Mac only, macOS 14 or later.
- Claude Code 2.1.242 or later. An older version fails setup, and AutoRouter
  asks you to update.
- AutoRouter sometimes misjudges how hard a task is. Rate the pick, or choose
  a model yourself.
