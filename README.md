# AutoRouter

AutoRouter is a Mac app that adds models from every leading provider to the
coding agents you already use, plus one more choice in each model picker:
AutoRouter, which sends each turn to the model that does it best. It uses the
AI subscriptions you already pay for first, or runs with no subscription at
all.

This repository holds AutoRouter's public docs, a Claude Code plugin, a public
MCP server config and an agent setup skill. The app is closed source and in
beta.

[Website](https://autorouter.com) ·
[Download](https://autorouter.com/AutoRouter.dmg) ·
[Agent setup guide](https://autorouter.com/setup.md) ·
[Pricing](https://autorouter.com/pricing) ·
[Privacy](https://autorouter.com/privacy) ·
[X](https://x.com/Auto_Router)

<!-- Related: autorouter-usage (coming soon) -->

**Reference docs:** [setup for each app](#supported-apps) ·
[how routing works](docs/how-routing-works.md) ·
[plans and credits](docs/plans-and-credits.md) · [FAQ](docs/faq.md)

## Who it's for

- Developers who use one or more coding agents (Claude Code, Codex, Cursor,
  etc.) and want every model available in each of them without API keys,
  endpoints or config files.
- People who pay for one or more AI subscriptions and want those plans to go
  to the work that needs them, so they last longer.
- People with no subscription who want to pay per use for the models they
  need.
- Teams that want one place to set allowed models, budgets and privacy rules
  for every engineer's coding agents ([Enterprise](https://autorouter.com/enterprise)).

## What it does on each turn

While AutoRouter is the selected model:

1. **Your rules go first.** If one of your plain-English rules applies (for
   example "Use Claude Opus 5.5 for UI work"), it decides the turn.
2. **It works out how hard the turn is** and only considers models that clear
   the quality bar for it.
3. **Hard work goes to the strongest model your plans cover**, and to paid
   models only when no plan model is strong enough.
4. **Everything else goes to the model that costs you least**, which is often
   your plan or a low-cost open model.
5. **Every turn shows its model, what it cost and why.** You can rate a pick
   or choose a model yourself at any time.

Picking a specific model in your app's picker sends turns straight to it.
AutoRouter routes only while AutoRouter is the model selected. More detail:
[How it picks a model](#how-it-picks-a-model).

## Claude Code plugin

The plugin adds the setup skill and the AutoRouter models MCP server to Claude
Code (2.1.292 or later). Install it from your shell:

```sh
claude plugin marketplace add fractal-works/autorouter-docs
claude plugin install autorouter@fractal-works
```

Or inside Claude Code:

```text
/plugin marketplace add fractal-works/autorouter-docs
/plugin install autorouter@fractal-works
```

Then run `/autorouter:set-up-autorouter` to install the Mac app and connect
your tools.

## MCP server (no account needed)

`https://api.autorouter.com/v1/mcp/public` is a read-only MCP server over
streamable HTTP. It needs no account or key, and runs on any OS. It has two
tools:

- `list_models` lists the coding models AutoRouter routes between, optionally
  only those a ChatGPT or Claude plan covers, or one intelligence tier.
- `recommend_model` says which model AutoRouter would use for a coding task,
  with two fallbacks and whether each runs on a plan or on credits.

The plugin adds it for you. To add only the server to Claude Code:

```sh
claude mcp add --transport http autorouter-models https://api.autorouter.com/v1/mcp/public
```

Other clients that support streamable HTTP can use the same URL. The server's
card is at
[autorouter.com/.well-known/mcp/server-card.json](https://autorouter.com/.well-known/mcp/server-card.json).

## Agent skill

`skills/set-up-autorouter` walks a coding agent through installing the Mac
app, signing in and checking that each tool is connected. Without the plugin,
add it with:

```sh
npx skills add fractal-works/autorouter-docs
```

## Install the app

AutoRouter needs macOS 14 or later. Claude Code needs Node 22.18 or later.

**Download.** Get [AutoRouter.dmg](https://autorouter.com/AutoRouter.dmg),
signed and notarized by Apple, and move AutoRouter to Applications.

**Homebrew.**

```sh
brew tap fractal-works/tap
brew trust --tap fractal-works/tap
brew install --cask fractal-works/tap/autorouter
```

Homebrew 7 loads casks from a tap outside Homebrew only after you trust it.

**Ask your coding agent.** Paste this into Codex or Claude Code:

```text
Set up AutoRouter by following https://autorouter.com/setup.md
```

Then:

1. Open AutoRouter, sign in or create a free account, sign in to your plans,
   allow Accessibility, and click Enable for each app.
2. Start a new session and choose AutoRouter as the model: in Codex, from the
   model menu under the message box; in Claude Code, with `/model`.

Open sessions keep their old settings, so start a new one after you enable an
app.


## Supported apps

Turn an app on in AutoRouter, then pick AutoRouter in that app's model picker.

| App                                     | Pick AutoRouter with                                                 | Notes                                             | Setup                                                                                                         |
| --------------------------------------- | -------------------------------------------------------------------- | ------------------------------------------------- | ------------------------------------------------------------------------------------------------------------- |
| Claude Code (CLI 2.1.242+, Node 22.18+) | `/model`, or `claude --model auto-claude-route`                      | No hooks; Claude Code keeps its own Claude sign-in | [Guide](docs/setup/claude-code.md) · [autorouter.com](https://autorouter.com/integrations/claude-code)       |
| Codex (app and CLI)                     | Model menu under the message box, `/model`, or `codex -m autorouter` | Restart Codex once when asked                     | [Guide](docs/setup/codex.md) · [autorouter.com](https://autorouter.com/integrations/codex)                   |
| Cursor (experimental)                   | New chats start on `autorouter`                                      | Chat and Agent only                               | [Guide](docs/setup/cursor.md) · [autorouter.com](https://autorouter.com/integrations/cursor)                 |
| Claude Desktop (experimental)           | Desktop's model picker                                               | Uses Desktop's gateway mode                       | [Guide](docs/setup/claude-desktop.md) · [autorouter.com](https://autorouter.com/integrations/claude-desktop) |
| T3 Code (experimental)                  | A Codex or Claude thread's model picker                              | Other T3 agents aren't routed                     | [Guide](docs/setup/t3.md) · [autorouter.com](https://autorouter.com/integrations/t3)                         |
| OpenCode (CLI 1.x and 2.x, Desktop)     | `/models`                                                            | OpenCode's own providers keep working             | [Guide](docs/setup/opencode.md) · [autorouter.com](https://autorouter.com/integrations/opencode)             |
| Pi (0.62+)                              | `/model`, no restart                                                 | Pi's own sign-ins stay Pi's                       | [Guide](docs/setup/pi.md) · [autorouter.com](https://autorouter.com/integrations/pi)                         |
| Terminal (any terminal app)             | Each CLI's own picker                                                | No shell profile changes                          | [Guide](docs/setup/terminal.md) · [autorouter.com](https://autorouter.com/integrations/terminal)             |
| ChatGPT                                 | [ChatGPT plugin](https://autorouter.com/chatgpt)                     |                                                   |                                                                                                               |

Full list: [autorouter.com/integrations](https://autorouter.com/integrations).

## What changes on your Mac

Enabling an app adds AutoRouter to that app's own settings file; each guide in
[docs/setup](docs/setup) names the file. AutoRouter saves a copy of each file
first, and your other settings stay as they are. Once Codex is enabled, its
`config.toml` points at `api.autorouter.com`. AutoRouter changes no shell
profile. Disabling an app in AutoRouter's settings switches it back.

## Plans and credits

- **Your plans first.** Connect Claude, ChatGPT, Grok and Gemini plans in
  AutoRouter. Free connects two subscriptions; Pro connects any number. Hard
  work goes to the strongest model your plans cover, and quick work doesn't
  burn the plan.
- **When a plan hits its limit**, AutoRouter moves on to the connected account
  with the most room left before it spends any credit. On Pro, turns keep
  going from the monthly included usage until the plan resets; if that runs
  out too, AutoRouter asks you to top up.
- **No subscription needed.** Pro gives every model, with included usage each
  month, and you can top up any time.
- **Paid models** are billed at the provider's price plus 10%, from included
  usage first and then from credits you top up. Bought credits never expire.
  Included usage resets each month and doesn't roll over.
- **Routing across your own plans is free.** AutoRouter earns the 10% on paid
  models and nothing on your plans.
- **Teams:** Enterprise is priced by seat and adds rollout through Jamf or
  another MDM, allowed models, team budgets, zero data retention, spend by
  team, project or ticket, SSO, SCIM and an audit log. See
  [autorouter.com/enterprise](https://autorouter.com/enterprise) or
  sales@autorouter.com.

Current prices and trial terms: [autorouter.com/pricing](https://autorouter.com/pricing).
Details: [docs/plans-and-credits.md](docs/plans-and-credits.md).

## How it picks a model

AutoRouter works out how hard each task is and sends it to the model that
fits. Its built-in rules:

- Hard work goes to your strongest model.
- Quick tasks go to the cheapest capable model.
- Unclear work is never treated as a quick task.
- A task that continues keeps its model, or moves up.
- Your plans come first for hard work.
- Untested models are never picked on their own.

The best model isn't always the most expensive. Every model has to clear a
quality bar for the task before price counts at all, unless one of your own
rules names it. Your rules come before AutoRouter's, and an avoid rule is
always respected. In Claude Code, AutoRouter judges the text you typed and
leaves out the memory files and reminders Claude Code adds.

Examples from autorouter.com (illustrations; real routes follow your plans and
rules):

| Turn                         | Where it goes                                 |
| ---------------------------- | --------------------------------------------- |
| A change across six files    | Claude Opus 5.5, on the Claude plan           |
| A commit message             | A low-cost open model; the plan isn't touched |
| A test that only fails on CI | GPT-6 Astra, on the ChatGPT plan              |
| UI work, with a rule for it  | Claude Opus 5.5                               |

**Models.** Frontier and open-weight models, curated by the AutoRouter team,
with no keys or endpoints to set up. They appear in the picker beside the
models already there. The lineup changes; the current list, with each model's
maker, role, plan and list price, is at
[autorouter.com/models](https://autorouter.com/models).

The team reviews real routing decisions and every rating, and tests each new
model as it becomes available. Details:
[docs/how-routing-works.md](docs/how-routing-works.md) and
[autorouter.com/routing](https://autorouter.com/routing).

## Privacy

How AutoRouter handles requests and what it keeps:
[autorouter.com/privacy](https://autorouter.com/privacy).

## FAQ

More answers in [docs/faq.md](docs/faq.md).

**What is AutoRouter for Codex and Claude Code?**
A Mac app that adds models from every leading provider to your coding agents'
model pickers, plus an AutoRouter option that picks the model for each turn.
In Codex, pick AutoRouter from the model menu or run `codex -m autorouter`. In
Claude Code, pick it with `/model`. See the [Codex](docs/setup/codex.md) and
[Claude Code](docs/setup/claude-code.md) guides.

**Is there a Mac app that adds more models to Codex and Claude Code?**
Yes. AutoRouter puts every leading model inside every coding agent you use,
with no API keys or endpoints to set up. New models show up in the picker as
they arrive.

**How can I use Claude models in Codex?**
Connect your Claude plan in AutoRouter, turn Codex on, and pick a Claude model
in Codex's model menu, or let AutoRouter pick.

**How can I use GPT models inside Claude Code?**
Connect your ChatGPT plan in AutoRouter, turn Claude Code on, and pick a GPT
model with `/model`, or let AutoRouter pick.

**How do I use other models in the Codex CLI?**
Turn Codex on in AutoRouter; the Codex app and CLI share
`~/.codex/config.toml`, so both get AutoRouter's models. Run `/model` or start
with `codex -m autorouter`.

**What's the best model router for Claude Code?**
For a router that lives inside Claude Code's own model picker, uses the plans
you already pay for first and shows every turn's model and cost, AutoRouter
needs no proxy, hooks or environment variables. Compare it with other tools at
[autorouter.com/comparisons](https://autorouter.com/comparisons).

**Is there a Mac app to switch models in Claude Code?**
Yes. With AutoRouter on, `/model` lists AutoRouter and its recommended models
beside Claude Code's own. Choosing a model sends turns straight to it;
choosing AutoRouter lets it pick per turn.

**How do I avoid hitting Claude Code usage limits?**
Send quick work away from your plan. AutoRouter keeps your plan for hard work,
sends quick turns to the cheapest capable model, and can spread work across
several connected accounts, moving to the one with the most room left when
one reaches its limit.

**What should I do when Codex runs out of usage mid-task?**
With more than one plan connected, the next turn moves to the account with the
most room left. On Pro, turns keep going from monthly included usage until
your plan resets.

**How do I have a second model review Claude Code's changes?**
Pick a different model with `/model` for the review, or write a rule such as
"Prefer GPT-6.1 Sol for code reviews" so AutoRouter sends review turns there.

**How do I see what each Claude Code turn costs?**
AutoRouter shows each turn's model, what it cost and why. In Claude Code a
status line shows the last turn's model.

**How do I set a budget for Claude Code across my team?**
AutoRouter Enterprise sets team and seat budgets, allowed models and defaults
for the whole organization. See
[autorouter.com/enterprise](https://autorouter.com/enterprise).

**What are the best alternatives to OpenRouter for coding agents?**
AutoRouter is a Mac app for coding agents: it works inside each agent's model
picker and uses your own subscriptions first. See
[AutoRouter and OpenRouter](https://autorouter.com/compare/openrouter) and
[all comparisons](https://autorouter.com/comparisons).

**Is this OpenRouter's Auto Router?**
No. OpenRouter is a separate company, and its
[Auto Router](https://openrouter.ai/docs/model-routing) is a model option in
its API. AutoRouter is a Mac app that works inside the coding agents listed
above.

**Is it LiteLLM's Claude Code autorouter, claude-code-router, autorouter.aero
or autorouter.top?**
No. LiteLLM documents a
[Claude Code autorouter](https://docs.litellm.ai/docs/tutorials/claude_code_autorouter)
for its own proxy, and
[claude-code-router](https://github.com/musistudio/claude-code-router) is a
separate project. autorouter.aero and autorouter.top are unrelated companies.
[This comparison](https://autorouter.com/compare/claude-code-router) covers how
AutoRouter differs from claude-code-router.

**Is it related to PCB autorouting?**
No. That is circuit board routing software.

**Do I need API keys?**
No. There are no keys or endpoints to set up.

**Does it ever get the pick wrong?**
Sometimes it misjudges how hard a task is. Rate the pick when it does, or
choose a model yourself. Before a routing change ships, the team checks it
against reviewed routing cases, including picks people rated down.

**Are there benchmarks?**
Not yet. Benchmarks and automatic evaluations on real coding tasks are coming.

**Does it run on Linux or Windows?**
No. AutoRouter is Mac-only for now, on macOS 14 or later.

**How do I turn it off for one app?**
Disable that app in AutoRouter's settings. It switches the app back to the
settings you had.

## Links

- Site: https://autorouter.com
- About: https://autorouter.com/about
- Download: https://autorouter.com/AutoRouter.dmg
- Agent setup guide: https://autorouter.com/setup.md
- Agent guide, after setup: https://autorouter.com/llms.txt
- Enterprise: https://autorouter.com/enterprise
- Support: support@autorouter.com
- Sales: sales@autorouter.com

## License

The docs, plugin and skill in this repository are under the [MIT License](LICENSE).
The AutoRouter app is not.
