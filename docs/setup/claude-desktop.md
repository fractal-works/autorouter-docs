# AutoRouter for Claude Desktop

Source: [autorouter.com/integrations/claude-desktop](https://autorouter.com/integrations/claude-desktop)

Turn Claude Desktop on in the AutoRouter Mac app and pick AutoRouter in
Desktop's model picker. Each turn goes to the model that fits it, on the AI
subscriptions you already pay for first.

**Works in:** Claude Desktop, on macOS 14 or later. Experimental.

## Set up

1. **Install the Mac app.** [Download AutoRouter](https://autorouter.com/AutoRouter.dmg),
   sign in or create a free account, then connect your Claude plan.
2. **Turn on Claude Desktop.** Click Enable on Claude Desktop's row, in setup
   or in Settings, under Apps, then Turn on.
3. **Restart and pick AutoRouter.** Restart Desktop when AutoRouter asks, then
   choose AutoRouter in the model picker.
4. **Import your chats.** Press Import history in Claude Desktop's column in
   AutoRouter's Settings, then import in Desktop with your claude.ai sign-in.

## What changes

- **Gateway mode.** AutoRouter switches Desktop to its gateway mode, pointed
  at AutoRouter, with the AutoRouter app as its credential helper. The profile
  holds a path to the app, not a key. Desktop gets a credential that works
  only for its model requests and lasts 24 hours.
- **Connectors come along once.** AutoRouter copies your claude.ai connectors
  into Desktop's gateway connector list once. After that you manage them in
  Desktop, under Configure Third-Party Inference. Some may need reconnecting.
- **Your chats stay.** Gateway mode keeps chats on this Mac. Your claude.ai
  chats aren't deleted: they leave the sidebar while AutoRouter is on and come
  back when you turn it off. Importing copies them once; import again to pick
  up newer ones.
- **Artifacts work.**

To go back, turn Claude Desktop off in AutoRouter's Settings, under Apps.
Desktop returns to your claude.ai account, with its chats, connectors and
cloud sessions.

## Plans

The plans you connect in AutoRouter. Claude turns run on your connected Claude
accounts, in your order, not on Desktop's own claude.ai sign-in. Models no
plan covers run on credits.

Claude Desktop and Claude Code each have their own switch, and either can be
on without the other. See [Claude Code setup](claude-code.md).

## Limits

- Experimental. Cloud sessions, including ones started from claude.ai or a
  phone, aren't available in gateway mode.
- Claude turns need a Claude plan connected in AutoRouter. Without one, they
  follow your paid-models setting.
- Mac only, macOS 14 or later.
