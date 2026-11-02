<p align="center">
  <img src="assets/banner.png" alt="be-ambitious" width="100%">
</p>

# be-ambitious

A free Claude skill that makes your agent more ambitious when you invoke it.

It turns Felix Rieseberg's article [How to be more ambitious: a tutorial for humans with models](https://felixrieseberg.com/how-to-be-more-ambitious-a-tutorial-for-humans-with-models/) into steps an agent follows. Felix works on Claude at Anthropic. All the ideas are his.

## What it does

Most of us use a model at the size of the task we typed. Felix's point: the model can do far more if you aim it higher, deeper or wider. He names four types of ambition. The skill uses three of them:

| Type | The question it asks | Example |
|---|---|---|
| **Altitude** | What's the goal beyond the goal? | Don't fix one crash. Keep the app crash-free. |
| **Depth** | What would the best expert in the field do, from the raw data, and what outside check proves it's right? | Don't make a markdown table. Load the data into a database and fit a real statistical model. |
| **Range** | Which other fields would help, and what do their experts actually do? | Bring in a journalist, an editor and a short seller, and have each do their real job. |

The fourth type, **Speed** (the same work in less time), is how most people already use AI, so Felix skips it and so does the skill.

When you invoke it, the skill:

1. Finds the goal beyond the goal.
2. Picks the types that fit your task (usually one or two, not all three).
3. Writes the ambitious plan: a 3-rung ladder for Altitude, Felix's four expert questions for Depth, and the crew for Range.
4. Lists the data, tools and access the plan needs, and what's missing.
5. Rewrites your prompt at that level. The prompt states a specific hard target, cites real proof that it can be done when there is any, gives permission to miss, and asks for an early result the check can score. It tells the worker to mark unknown facts as TODOs and to ask you before risky actions, and it ends with an outside check and what counts as a pass.
6. Does the work, if you handed it a task, then reports the answer first and grades it against the target as written. Stops after the rewrite, if you handed it a prompt to improve.

It holds a few hard lines from the article: better, not bigger. Do what the expert does, not role play. Never grade your own work. Treat the hard target as reasonable, and report honestly against the check. It adds one more: ambition raises the standard, not the permissions.

## Install

**Claude Code.** Put the skill in a folder named `be-ambitious` inside your skills folder.

For all your projects:

```bash
git clone https://github.com/robonuggets/be-ambitious ~/.claude/skills/be-ambitious
```

For one project only, run this from the project folder:

```bash
git clone https://github.com/robonuggets/be-ambitious .claude/skills/be-ambitious
```

The skill is one file, so copying `SKILL.md` into `~/.claude/skills/be-ambitious/` works too. On Windows, `~/.claude` is the `.claude` folder inside your user folder.

**claude.ai.** Zip `SKILL.md` and `LICENSE` in a folder named `be-ambitious`, then upload it under Skills in your claude.ai settings.

## Use it

Type `/be-ambitious` and your task:

```text
/be-ambitious make our quarterly business review deck from the sales CSVs in /data
```

- **A task to do** (fix, build, analyse): you get the plan and the rewritten prompt, then the agent starts on the rung it picked. It asks first only if the rung replaces what you asked for, costs money, changes a shared system (CI, production, a public repo), or cannot be undone.
- **A prompt to improve** ("rewrite this prompt", or a prompt meant for another tool): you get the plan and the rewritten prompt, and it stops.
- **No task:** `/be-ambitious` on its own uses your last request.

You can also say it in plain words, like "be more ambitious with this" or "what would a top expert do here?"

## Example

You type:

```text
/be-ambitious our marketing website takes 8 seconds to load, speed it up
```

You get (from a real test run, trimmed):

- **Goal beyond the goal:** visitors never leave because the site is slow.
- **Types:** Altitude and Depth. Range skipped, since a speed fix has mostly one right answer.
- **Altitude ladder:**
  1. Get the page under a set load time, with before and after measurements.
  2. Find every slow page and fix the causes.
  3. Keep the site fast: a performance budget checked on every deploy, failing the build when it slips.
- **Depth:** start from a real trace, not guesses. Use Lighthouse, WebPageTest, the network waterfall and a bundle analyzer. Hard target: about 200 ms to first useful content, not 5 seconds.
- **Outside judge:** repeated measured runs and real-user numbers.
- **Rewritten prompt:**

```text
Our marketing website takes 8 seconds to load. Start from a real trace (Lighthouse,
WebPageTest, the network waterfall), not guesses, and list the biggest causes by time
cost. Fix them in order, measuring after each fix. Aim for about 200 ms to first useful
content. Then add a performance budget to our deploys so it can't get slow again.
Pass = repeated test runs show the target met, and the deploy check fails when the
budget is broken. Report real numbers, including any missed target.
```

Then it starts: a baseline Lighthouse run on the live site, the slowest requests ranked, and the top cause fixed and measured again.

## What it needs

Felix's note, and it matters: all of this needs a model with **a computer it can install software on** and **access to the real data**, through MCP connectors (plug-ins that link the agent to your apps) or other means. Without them, the skill tells you exactly what's missing and what it would unlock. It won't invent data to fill the gap.

## Credits

- **Felix Rieseberg** for the article this skill is built on: [How to be more ambitious: a tutorial for humans with models](https://felixrieseberg.com/how-to-be-more-ambitious-a-tutorial-for-humans-with-models/) (13 Oct 2026). The types, the examples, the Depth prompt and the warnings are his.
- **DannyMac180** for the earlier, prompt-only version: [DannyMac180/skills](https://github.com/DannyMac180/skills/tree/main/be-ambitious). It wraps Felix's "deeper, not bigger" prompt. This version adds Altitude and Range.
- **Tom Kelley and Jonathan Littman** for the nouns-to-verbs trick in *The Art of Innovation*, which Felix uses for Range.

## License

MIT. See [LICENSE](LICENSE).

Made by [RoboNuggets](https://www.skool.com/robonuggets)
