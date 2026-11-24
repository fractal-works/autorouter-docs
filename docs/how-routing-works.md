# How AutoRouter picks a model

Source: [autorouter.com/routing](https://autorouter.com/routing)

AutoRouter works out how hard each task is and sends it to the model that
fits. Hard work gets the best model; quick work doesn't burn your plan.

## The order of decisions

1. **Your rules.** If one of your rules applies, it decides the turn.
2. **Difficulty.** Otherwise AutoRouter works out how hard the turn is and
   only considers models that clear the quality bar for it.
3. **Hard work** goes to the most capable model your plans cover, and to
   credits only when no plan model is strong enough.
4. **Everything else** goes to the model that costs you least, which is often
   your plan or a low-cost open model.

Price only decides between models that already clear the quality bar. Hard
work goes to the strongest model your plans cover, even when a cheaper one
comes close. If a task is unclear, it goes to a model that can do it well,
never the cheapest one.

## Built-in rules

- Hard work goes to your strongest model.
- Quick tasks go to the cheapest capable model.
- Unclear work is never treated as a quick task.
- A task that continues keeps its model, or moves up.
- Your plans come first for hard work.
- Untested models are never picked on their own.

## Your rules

Write rules in plain English, for example:

- "Use Claude Opus 5.5 for UI work."
- "Prefer GPT-6.1 Sol for code reviews."
- Send git commands to a low-cost model.

Your rules come before AutoRouter's recommended ones, and you can see how
often each rule is used.

An **avoid** rule is always respected. AutoRouter never sends the turn to the
avoided model, even to continue an earlier turn that ran on it. It picks the
next model that clears the quality bar, even when that model costs more. If no
other model clears the bar, the strongest remaining model runs the turn; if no
other model can run the turn at all, AutoRouter refuses it and names the rule.

## Examples

Illustrations from autorouter.com; real routes follow your plans and rules.

| Turn | Where it goes | Why |
| --- | --- | --- |
| A change across six files | Claude Opus 5.5, on the Claude plan | Hard work, covered by a plan |
| A commit message | A low-cost open model | Quick work; the plan isn't touched |
| A test that only fails on CI | GPT-6 Astra, on the ChatGPT plan | Hard work, covered by a plan |
| UI work | Claude Opus 5.5 | A rule names it |

## How Claude Code turns are judged

For Claude Code, AutoRouter judges how hard a turn is from the text you typed,
leaving out the memory files and reminders Claude Code adds. When a message
holds only that added text, it uses the last request you typed.

## Seeing and overriding picks

- Every turn shows its model, what it cost and why.
- You can see which models do best on which tasks, then set a rule or pick a
  model yourself.
- Choosing a model in your app's picker sends turns straight to it.
  AutoRouter routes only while it is the model selected.
- If a pick falls short, rate it or choose a model yourself.

## How it improves

Ratings retune the router, along with tests of every new model as it becomes
available. The AutoRouter team reviews real routing decisions and every rating
people send. Before a routing change ships, the team checks it against
reviewed routing cases, including picks people rated down, run through the
same rule path production uses.

Not available yet: published benchmarks, automatic evaluations on real coding
tasks, and routing that learns on its own.

## How it differs from an app's own Auto mode

You can see which model handled every turn and what it cost, change it with a
rule or the app's model picker, and use models from every provider.

## Limits

AutoRouter sometimes misjudges how hard a task is. Rate the pick when it does,
or choose a model yourself.
