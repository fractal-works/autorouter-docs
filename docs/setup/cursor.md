# AutoRouter for Cursor

Source: [autorouter.com/integrations/cursor](https://autorouter.com/integrations/cursor)

Turn Cursor on in the AutoRouter Mac app and pick AutoRouter in Cursor's model
picker. Each Chat and Agent turn goes to the model that fits it, on the AI
subscriptions you already pay for first.

**Works in:** Cursor's Chat and Agent, on macOS 14 or later. Experimental.

## Set up

1. **Install the Mac app.** [Download AutoRouter](https://autorouter.com/AutoRouter.dmg),
   sign in or create a free account, then connect your plans.
2. **Turn on Cursor.** Click Enable on Cursor's row, in setup or in Settings,
   under Apps.
3. **Restart Cursor.** Click Restart on AutoRouter's notice. Cursor saves its
   own settings while it runs, so AutoRouter writes them the moment it quits.
4. **Pick AutoRouter.** Open a new chat. It starts on `autorouter`, or choose
   it in the model picker.

## What changes

AutoRouter sets Cursor's OpenAI key settings, so there is no key to paste:

| Cursor setting | AutoRouter sets it to |
| --- | --- |
| Use OpenAI API Key | On |
| Override OpenAI Base URL | AutoRouter's Cursor address |
| OpenAI API key | A key AutoRouter issues for Cursor on this Mac; it works nowhere else, lasts 90 days and is renewed automatically |
| Model list | `autorouter` plus AutoRouter's other model names |
| Agent's model | `autorouter`, the first time only |
| Default Model | Last Used, the first time only |
| Default Environment | `local`, the first time only, so a new chat runs on this Mac |

Turning Cursor off puts your earlier values back the next time Cursor quits,
and removes AutoRouter's models. A setting you changed since stays yours.

## Which Cursor modes use AutoRouter

| Cursor feature | Uses AutoRouter |
| --- | --- |
| Chat | Yes |
| Agent, running locally | Yes |
| Agent, running in Cloud | No |
| Tab | No, stays on Cursor |
| Cursor's Auto | No, stays on Cursor and keeps working |
| Cursor CLI | No, stays on Cursor |
| Cursor's own named models | Stop working while AutoRouter is on, because Cursor uses one API key for every model |

## Plans

The plans you connect in AutoRouter: Claude, ChatGPT, Grok and Gemini. Models
no plan covers run on credits.

## Troubleshooting

| What you see | What to do |
| --- | --- |
| `autorouter` is not in the model picker | Click Restart on AutoRouter's notice, or quit Cursor and reopen it. |
| A Cursor model fails with "This model does not support custom API keys" | Pick `autorouter` or Cursor's Auto, or turn Cursor off in AutoRouter to bring named models back. |
| A new chat starts on another model | Set Default Model to Last Used, then pick `autorouter`. |
| A chat runs in Cloud and nothing shows in AutoRouter | Open a workspace and start the chat with Run on set to Local. |
| Turns fail with "AutoRouter is signed out on this Mac" | Sign in to AutoRouter, then restart Cursor. |
| Cursor has no Enable row in AutoRouter | Install Cursor on this Mac, then reopen setup or Settings. |

## Limits

- While it's on, Cursor's own named models stop working. Cursor's Auto keeps
  working.
- Mac only, macOS 14 or later.
- AutoRouter sometimes misjudges how hard a task is. Rate the pick, or choose
  a model yourself.
