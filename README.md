# AutoRouter

AutoRouter is a Mac app by Fractal Works, Inc. It adds 20+ models to Codex
and Claude Code, plus one more choice in the model picker: AutoRouter, which
picks the right model for each turn. It also works in Claude Desktop, T3 and
Terminal. It uses the ChatGPT and Claude plans you already pay for first.

This repository holds AutoRouter's public docs and its agent setup skill
(`skills/set-up-autorouter`). The app is closed source and in beta. Download it from
[autorouter.com](https://autorouter.com).

[Website](https://autorouter.com) ·
[Download](https://autorouter.com/AutoRouter.dmg) ·
[Agent setup guide](https://autorouter.com/setup.md) ·
[Pricing](https://autorouter.com/pricing) ·
[Privacy](https://autorouter.com/privacy) ·
[X](https://x.com/Auto_Router)

## Install

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

## Supported tools

| Tool                | Status                                           |
| ------------------- | ------------------------------------------------ |
| Codex (app and CLI) | Supported                                        |
| Claude Code (CLI)   | Supported                                        |
| Claude Desktop      | Supported                                        |
| T3                  | Supported                                        |
| Terminal            | Supported                                        |
| ChatGPT             | [ChatGPT plugin](https://autorouter.com/chatgpt) |
| OpenCode            | Coming soon                                      |
| Pi                  | Coming soon                                      |

## What changes on your Mac

Enabling an app adds AutoRouter to that app's own settings: Codex's
`config.toml` and Claude Code's `settings.json`. AutoRouter saves a copy of
each file first, and your other settings stay as they are. Once Codex is
enabled, its `config.toml` points at `api.autorouter.com`. Disabling an app in
AutoRouter's settings switches it back.

## How routing works

While AutoRouter is the selected model, each turn goes through these steps:

1. **Your rules go first.** If one of your rules applies, it decides the turn.
   You write rules in plain English, such as "Use Claude Opus 5.5 for UI work"
   or "Prefer GPT-6.1 Sol for code reviews", and you can see how often each
   one is used.
2. **AutoRouter works out how hard the turn is** and only considers models
   that clear the quality bar for it. In Claude Code it judges the text you
   typed and leaves out the memory files and reminders Claude Code adds.
3. **Hard work goes to the most capable model your plans cover**, and to
   credits only when none of them is strong enough.
4. **Everything else goes to the model that costs you least** among those that
   clear the bar, which is often your plan or a low-cost open model.

A few built-in rules sit under that: unclear work is never treated as a quick
task, a task that continues keeps its model or moves up, and untested models
are never picked on their own. An avoid rule is always respected.

Every turn shows the model it ran on, what it cost and why. Choosing a model
in the picker sends turns straight to it; AutoRouter routes only while it is
the selected model. If a pick falls short, rate it or choose a model yourself.
The team reviews real routing decisions and every rating, and tests each new
model as it becomes available.

**Models.** Frontier and open-weight models, curated by the AutoRouter team,
with no keys or endpoints to set up. They appear in the picker beside the
models already there. In Codex, OpenAI models run on your ChatGPT plan; in
Claude Code, Claude models run on your Claude plan. Examples today: GPT-6
Astra and GPT-6.1 Sol on the ChatGPT plan; Claude Opus 5.5 and Claude Sonnet
5.5 on the Claude plan; Gemini 4 Argon, Grok 4.7, DeepSeek V4.1 Flash, Kimi K3
and MiniMax M3.1 Flash pay per use. The lineup changes.

## Pricing

| Plan       | Price          | What you get                                                                                                                                                                     |
| ---------- | -------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Free       | $0 a month     | Routing across your ChatGPT and Claude plans                                                                                                                                     |
| Pro        | $50 a month    | Every other model, with $20 of included usage each month. When a ChatGPT or Claude plan hits its limit, Pro keeps those turns going from the monthly usage until the plan resets |
| Enterprise | Priced by seat | Everything in Pro, plus rollout through Jamf or another MDM, allowed models, team budgets, zero data retention, spend by team, project or ticket, SSO, SCIM and an audit log     |

- Paid models are billed at the provider's price plus 10%, from the included
  usage first and then from credits you top up. Credits you buy never expire.
  Included usage resets each month and doesn't roll over.
- You don't need a ChatGPT or Claude subscription. Pro gives every model.
- New accounts get their first month of Pro at no charge, or until $20 of
  usage is spent, whichever comes first. After that, Pro is $50 a month.
- AutoRouter earns the 10% on paid models and nothing on your plans. Price
  only decides between models that already clear the quality bar.
- Enterprise: [autorouter.com/enterprise](https://autorouter.com/enterprise)
  or sales@autorouter.com.

## Privacy

How AutoRouter handles requests and what it keeps:
[autorouter.com/privacy](https://autorouter.com/privacy).

## FAQ

**Is this OpenRouter's Auto Router?**
No. OpenRouter is a separate company, and its
[Auto Router](https://openrouter.ai/docs/model-routing) is a model option in
its API. AutoRouter is a Mac app from Fractal Works that works inside Codex,
Claude Code and the other tools above.

**Is it LiteLLM's Claude Code autorouter, claude-code-router, autorouter.aero
or autorouter.top?**
No. LiteLLM documents a
[Claude Code autorouter](https://docs.litellm.ai/docs/tutorials/claude_code_autorouter)
for its own proxy, and
[claude-code-router](https://github.com/musistudio/claude-code-router) is a
separate open-source project. autorouter.aero and autorouter.top are unrelated
companies. [This comparison](https://autorouter.com/compare/claude-code-router)
covers how AutoRouter differs from claude-code-router.

**Is it related to PCB autorouting?**
No. That is circuit board routing software.

**Do I need API keys?**
No. There are no keys or endpoints to set up.

**Do I need a ChatGPT or Claude subscription?**
No. Free routes across the plans you have. Pro gives every model, with $20 of
included usage each month, and you can top up any time.

**What happens when my plan hits its limit?**
On Pro, those turns keep going from the monthly usage until the plan resets.
If that runs out too, AutoRouter asks you to top up.

**Can I pick the model myself?**
Yes. Choose any model in the picker and turns go straight to it. AutoRouter
routes only while it is the selected model.

**How is it different from my app's own Auto mode?**
You can see which model handled every turn and what it cost, change it with a
rule or the app's model picker, and use models from every provider.

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

**How does it compare with OpenRouter, LiteLLM or Vercel AI Gateway?**
See [autorouter.com/comparisons](https://autorouter.com/comparisons).

## Links

- Site: https://autorouter.com
- About: https://autorouter.com/about
- Download: https://autorouter.com/AutoRouter.dmg
- Agent setup guide: https://autorouter.com/setup.md
- Agent guide, after setup: https://autorouter.com/llms.txt
- Enterprise: https://autorouter.com/enterprise
- Support: support@autorouter.com
- Sales: sales@autorouter.com

AutoRouter is made by Fractal Works, Inc.