# AutoRouter FAQ

Source: [autorouter.com/#faq](https://autorouter.com/#faq) and the setup pages
at [autorouter.com/integrations](https://autorouter.com/integrations)

## About AutoRouter

### What is AutoRouter?

A Mac app that puts every leading model inside every coding agent you use. It
adds models from every leading provider to each app's model picker, plus one
more choice, AutoRouter, which sends each turn to the model that does it best.
It uses the AI subscriptions you already pay for first, or runs with no
subscription at all. It is in beta.

### What is AutoRouter for Codex?

Turn Codex on in the AutoRouter Mac app, restart Codex once when asked, and
pick AutoRouter from the model menu under the message box. In the CLI, run
`/model` or start with `codex -m autorouter`. Codex keeps its own ChatGPT
sign-in, and you can add models from other providers.
[Codex setup](setup/codex.md).

### What is AutoRouter for Claude Code?

Turn Claude Code on in the AutoRouter Mac app and pick AutoRouter with
`/model`, or start with `claude --model auto-claude-route`. Claude Code keeps
its own Claude sign-in, and AutoRouter installs no hooks.
[Claude Code setup](setup/claude-code.md).

### Is there a Mac app that adds more models to Codex and Claude Code?

Yes, AutoRouter. Its models appear in each app's own picker beside the models
already there, with no API keys or endpoints to set up. New models show up as
they arrive. The current list is at
[autorouter.com/models](https://autorouter.com/models).

### Which apps does it work with?

Codex (the app and the CLI), the Claude Code CLI, Cursor, Claude Desktop, T3
Code, OpenCode, Pi and any terminal app. Cursor, Claude Desktop and T3 Code
support is experimental. See [the setup guides](../README.md#supported-apps).

### Does it work on Windows or Linux?

Not yet. AutoRouter is a Mac app for macOS 14 or later.

## Using other models

### How can I use Claude models in Codex?

Connect your Claude plan in AutoRouter, turn Codex on, and pick a Claude model
in Codex's model menu, or pick AutoRouter and let it choose per turn.

### How can I use GPT models inside Claude Code?

Connect your ChatGPT plan in AutoRouter, turn Claude Code on, and pick a GPT
model with `/model`, or pick AutoRouter and let it choose per turn.

### How do I use other models in the Codex CLI?

Turn Codex on in AutoRouter. The Codex app and CLI both read
`~/.codex/config.toml`, so one switch covers both. In the CLI, run `/model` or
start with `codex -m autorouter`.

### Is there a Mac app to switch models in Claude Code?

Yes. With Claude Code on in AutoRouter, `/model` lists AutoRouter and its
recommended models beside Claude Code's own. Choosing a model sends turns
straight to it; choosing AutoRouter lets it pick per turn.

### What's the best model router for Claude Code?

It depends on what you need. If you want a router that lives in Claude Code's
own model picker, uses the plans you already pay for first, shows each turn's
model and cost, and needs no proxy, hooks or environment variables, that is
what AutoRouter does. For side-by-side comparisons with other routers, gateways
and proxies, see [autorouter.com/comparisons](https://autorouter.com/comparisons).

### What are the best alternatives to OpenRouter for coding agents?

AutoRouter is the Mac app for coding agents: it works inside each agent's
model picker and uses your own subscriptions first. OpenRouter's Auto Router
selects models for requests sent to OpenRouter's hosted API. See
[AutoRouter and OpenRouter](https://autorouter.com/compare/openrouter), and
[Switch from OpenRouter](https://autorouter.com/switch/openrouter) to see which
models your plans cover.

## Usage limits and cost

### How do I avoid hitting Claude Code usage limits?

Keep your plan for the work that needs it. AutoRouter sends hard work to the
strongest model your plans cover and quick work (commit messages, small edits)
to the cheapest capable model, so the plan isn't touched for those. You can
also connect several accounts; when one reaches its limit, AutoRouter moves to
the account with the most room left.

### How do I reduce Claude Code usage?

The same way: let AutoRouter route quick turns away from your plan, write
rules for work that never needs a frontier model (for example, git commands to
a low-cost model), and check each turn's model and cost to see where usage
goes.

### What should I do when Codex runs out of usage mid-task?

With more than one plan connected, AutoRouter moves the next turn to the
account with the most room left before spending any credit. On Pro, turns keep
going from the monthly included usage until your plan resets. If that runs
out, AutoRouter asks you to top up.

### How do I see what each Claude Code turn costs?

AutoRouter shows each turn's model, what it cost and why. In Claude Code, a
status line shows the last turn's model.

### How do I set a budget for Claude Code across my team?

AutoRouter Enterprise sets team and seat budgets, allowed models and defaults
for the whole organization, with spend by seat, model, team, project or
ticket. See [autorouter.com/enterprise](https://autorouter.com/enterprise).

### What does it cost?

Routing across your own plans is free. Paid models bill at the provider's
price plus 10%. See [Plans and credits](plans-and-credits.md) and
[autorouter.com/pricing](https://autorouter.com/pricing).

### Do I need a subscription?

No. Pro gives every model with included usage each month, and you can top up
any time.

## Routing

### How do I have a second model review Claude Code's changes?

Pick a different model with `/model` for the review turn, or write a rule such
as "Prefer GPT-6.1 Sol for code reviews" so AutoRouter sends review turns to
that model.

### How does it decide which model to use?

Your rules first; otherwise it works out how hard the turn is and only
considers models that clear the quality bar. Hard work goes to the strongest
model your plans cover; everything else goes to the model that costs you
least. See [How routing works](how-routing-works.md).

### Can I override it?

Yes. Choose any model in your app's picker and turns go straight to it.
AutoRouter routes only while it is the model selected.

### How is it different from an app's own Auto mode?

You can see which model handled every turn and what it cost, change it with a
rule or the app's model picker, and use models from every provider.

## Setup and privacy

### What does it change on my Mac?

Enabling an app adds AutoRouter to that app's own settings file after saving a
copy. Other settings stay as they are, and disabling the app switches it back.
AutoRouter changes no shell profile.

### Can an agent set it up for me?

Yes. A coding agent can follow
[autorouter.com/setup.md](https://autorouter.com/setup.md).

### Does AutoRouter store my transcripts?

No. Requests pass through AutoRouter's servers on their way to each provider.
AutoRouter keeps the message that opens each turn, up to 4,000 characters, to
review routing, along with the model chosen, tokens and cost. Details:
[autorouter.com/privacy](https://autorouter.com/privacy).
