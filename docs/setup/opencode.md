# AutoRouter for OpenCode

Source: [autorouter.com/integrations/opencode](https://autorouter.com/integrations/opencode)

Turn OpenCode on in the AutoRouter Mac app and pick AutoRouter in OpenCode's
model picker. Each turn goes to the model that fits it, on the AI
subscriptions you already pay for first. No API keys.

**Works in:** the OpenCode CLI (1.x and 2.x) and OpenCode Desktop, on macOS 14
or later.

## Set up

1. **Install the Mac app.** [Download AutoRouter](https://autorouter.com/AutoRouter.dmg),
   sign in or create a free account, then connect your plans.
2. **Turn on OpenCode.** Click Enable on OpenCode's row, in setup or in
   Settings, under Apps.
3. **Pick AutoRouter.** Start a new session, run `/models` and choose
   AutoRouter under the AutoRouter provider. Or start with:

   ```sh
   opencode -m autorouter/autorouter
   ```

4. **Keep building.** OpenCode 2.x picks up the change on its own. Restart
   OpenCode 1.x or OpenCode Desktop once.

## What changes

- **One provider, nothing else.** AutoRouter adds an `autorouter` provider to
  `~/.config/opencode/opencode.json` and lists AutoRouter first among its
  models. The rest of the file stays yours. A config kept in a dotfiles folder
  is written through its link.
- **No key in your config.** The provider names a key file that only your Mac
  account can read, so a config you share or commit holds no secret.
- **Your default comes back.** The first time, AutoRouter becomes OpenCode's
  default model and remembers the one it replaced. A default you pick later
  stays yours. Turning OpenCode off, signing out or uninstalling puts your old
  default back.

OpenCode's own providers, sign-ins and models keep working beside AutoRouter;
only AutoRouter's models go through AutoRouter.

## Plans

The plans you connect in AutoRouter: Claude, ChatGPT, Grok and Gemini. Models
no plan covers run on credits.

## Limits

- Mac only, macOS 14 or later.
- An `opencode.json` with comments can't be edited safely, so AutoRouter
  leaves it alone and Settings says why.
- AutoRouter sometimes misjudges how hard a task is. Rate the pick, or choose
  a model yourself.
