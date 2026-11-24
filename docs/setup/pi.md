# AutoRouter for Pi

Source: [autorouter.com/integrations/pi](https://autorouter.com/integrations/pi)

Turn Pi on in the AutoRouter Mac app and pick AutoRouter with `/model`. Each
turn goes to the model that fits it, on the AI subscriptions you already pay
for first. No API keys and no restart.

**Works in:** Pi 0.62 or later in any terminal, on macOS 14 or later.

## Set up

1. **Install the Mac app.** [Download AutoRouter](https://autorouter.com/AutoRouter.dmg),
   sign in or create a free account, then connect your plans.
2. **Turn on Pi.** Click Enable on Pi's row, in setup or in Settings, under
   Apps.
3. **Pick AutoRouter.** Run `/model` and choose AutoRouter under the
   AutoRouter provider. Pi reloads its models each time `/model` opens, so a
   running session sees it.
4. **Keep building.** New sessions start on AutoRouter. Save another default
   with `/model` any time.

## What changes

- **One provider, nothing else.** AutoRouter adds an `autorouter` provider to
  `~/.pi/agent/models.json` (or the folder `PI_CODING_AGENT_DIR` names). Every
  other provider in the file stays yours. The file holds this Mac's AutoRouter
  token, so AutoRouter keeps it readable only by your account.
- **Kept current.** AutoRouter refreshes the provider as its model list
  changes, so new models show up in `/model`.
- **Your default comes back.** The first time, AutoRouter becomes Pi's startup
  model in `settings.json` and remembers yours. A default you save later stays
  yours. Turning Pi off puts your old default back.

Pi's own providers and `/login` sign-ins stay Pi's. AutoRouter doesn't read or
use them.

## Plans

The plans you connect in AutoRouter: Claude, ChatGPT, Grok and Gemini. Models
no plan covers run on credits.

## Limits

- Mac only, macOS 14 or later.
- A `models.json` that isn't plain JSON is left alone, and Enable says why.
- Two Pi sessions in one terminal window, or Pi inside tmux, still route, but
  the menu bar can't tell which session is in front.
- AutoRouter sometimes misjudges how hard a task is. Rate the pick, or choose
  a model yourself.
