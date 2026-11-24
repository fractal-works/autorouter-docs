# AutoRouter for Codex

Source: [autorouter.com/integrations/codex](https://autorouter.com/integrations/codex)

Turn Codex on in the AutoRouter Mac app and pick AutoRouter in Codex's model
menu. Each turn goes to the model that fits it, on the AI subscriptions you
already pay for first. No API keys.

**Works in:** the Codex app and the Codex CLI, on macOS 14 or later.

## Set up

1. **Install the Mac app.** [Download AutoRouter](https://autorouter.com/AutoRouter.dmg),
   sign in or create a free account, then connect your plans.
2. **Turn on Codex.** Click Enable on Codex's row, in setup or in Settings,
   under Apps.
3. **Restart Codex once.** AutoRouter asks when Codex needs a restart to load
   the new provider. Model list changes after that need no restart.
4. **Pick AutoRouter.** Start a new chat and choose AutoRouter from the model
   menu under the message box. In the CLI, run `/model`, or start with:

   ```sh
   codex -m autorouter
   ```

## What changes

- **One block in `config.toml`.** AutoRouter writes its settings between
  marked lines in `~/.codex/config.toml` (or the folder `CODEX_HOME` names):
  Codex's own OpenAI provider pointed at `api.autorouter.com`, a model list
  with AutoRouter first, and live web search for every model. It saves a copy
  of the file first, and the rest stays yours.
- **One profile for app and CLI.** Both read the same file, so turning Codex
  on covers both. The address carries a credential tied to this Mac, which
  AutoRouter renews on its own and revokes when you sign out.
- **Your default comes back.** The first time, AutoRouter becomes Codex's
  default model and remembers the one it replaced. A model you pick later
  stays yours. Turning Codex off puts your old default back.

## Plans

OpenAI models run on your ChatGPT plan, through Codex's own sign-in. You can
also connect Claude, ChatGPT, Grok and Gemini plans in AutoRouter. Models no
plan covers run on credits. To use Claude models in Codex, connect your Claude
plan and pick a Claude model in the model menu, or let AutoRouter pick.

## AutoRouter is missing from the model picker

Open AutoRouter and check that Codex is enabled under Settings → Apps. Restart
Codex if AutoRouter asks you to, then start a new chat and open the model menu
below the message box. In the CLI, check the list with `/model`. If it still
doesn't appear, see [autorouter.com/support](https://autorouter.com/support).

## Limits

- Mac only, macOS 14 or later.
- A task compacted while AutoRouter was on can't be resumed in Codex after
  AutoRouter is removed.
- AutoRouter sometimes misjudges how hard a task is. Rate the pick, or choose
  a model yourself.
