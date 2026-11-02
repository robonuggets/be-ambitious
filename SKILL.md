---
name: be-ambitious
description: Raise the ambition of a task or prompt with Felix Rieseberg's Altitude (the goal beyond the goal), Depth (work like the field's best expert, from raw data, checked by an outside judge) and Range (bring in other fields and do what their experts do). Writes the plan and a rewritten prompt, then does the work when handed a task. Use when the user types /be-ambitious, asks to be more ambitious, aim higher, raise the bar or go deeper, asks for the goal beyond the goal or what a top expert would do, or wants a prompt made more ambitious.
license: MIT
metadata:
  author: RoboNuggets
  source: https://felixrieseberg.com/how-to-be-more-ambitious-a-tutorial-for-humans-with-models/
---

# Be ambitious

This skill turns Felix Rieseberg's article [How to be more ambitious: a tutorial for humans with models](https://felixrieseberg.com/how-to-be-more-ambitious-a-tutorial-for-humans-with-models/) (13 October 2026) into steps an agent can follow. Felix works on Claude at Anthropic. The ideas are his.

Most people use a model at the size of the task they typed. Model skills grow unevenly, "astounding in some directions, while inadequate in others" (Terence Tao), so the only way to find the astounding parts is to aim higher than feels reasonable.

## The rules that matter most

1. Better, not bigger. Each type raises one thing: the outcome (Altitude), the standard (Depth) or the set of perspectives (Range). None of them means more deliverables, features or side quests. Drop each suggestion that makes the job larger without making it better.
2. Do what the expert does, not how they talk. When you bring in a field, use its methods, tools and media. A switch of vocabulary without a switch of methods is role play: the transcript gets weirder and the result stays the same.
3. An outside judge decides if it worked. Find something other than you or the user that shows the result is right: a test, a benchmark, a reproduction, held-out data, a measurement. Best of all is a tool you can run to get feedback at once. Your own opinion of your work is not a judge.
4. Treat the hard target as reasonable. If a goal looks impossible, assume it is solvable and keep going. Grade the result against the target as written: the same statistic, on the same data split. A missed hard target with real numbers is a good result. A lenient reading or a faked hit is not.
5. Get the access, do not fake it. All of this needs a computer you can install software on and access to the real data, through MCP connectors (plug-ins that link an agent to other apps) or other means. If either is missing, name what is missing and what it unlocks. Report only sources, tools and results that you actually used. When you write a prompt for another agent, tell it to mark each fact it cannot find or measure as a TODO or a question for the user.
6. Ambition raises the standard, not the permissions. Ask before an action that replaces what the user asked for instead of raising it, spends money, changes a shared system (CI, production, a public repo or tracker) or cannot be undone. A rewritten prompt holds the same line: each action the plan says needs the user's OK appears in the prompt as "ask me before ...", not as a step.

## Input

The task is whatever follows `/be-ambitious`. If nothing follows, use the user's most recent request. If there is none, ask for the task in one line and stop.

Then decide what you were handed:

- A task to do (fix this, build this, analyze this): plan it at the ambitious level, then do it.
- A prompt to improve (a rewrite request, or a task meant for another agent or tool): stop after the rewritten prompt.

If you cannot tell which, stop after the rewritten prompt.

## Pick the types that fit

Felix names four types of ambition. Speed (the same work in less time) is how most people already use AI and needs no creativity, so he skips it, and so does this skill. Use the other three only where they fit. Most tasks need one or two.

| Type | Fits when | Skip when |
| --- | --- | --- |
| Altitude | The task serves an outcome. A good tell: people will hold meetings about it | Creative work with no outcome beyond itself |
| Depth | The task should be done really well | Throwaway work |
| Range | The result has to land with people, or the obvious field has run out of ideas | A narrow fix with one right answer |

### Altitude: aim at the outcome

A task is the user's best guess at how to get an outcome. Find the outcome: what does the user want to happen next, what is the goal beyond the goal? Felix used to ask Claude to fix single crashes. Then he asked it to keep the apps crash-free.

Build a ladder of three rungs, each more ambitious than the last. Felix's example is a quarterly business review (QBR) deck:

1. Understand, do not fill in. Skip updating the numbers in the template. Take in all the data you can get and work out "what changed this quarter, why, and what we should do about it."
2. Get to the decisions. "Work out which three decisions are most urgent in the face of everything you've learned, and start working on potential directions with for/against arguments."
3. Replace the ritual. "The review exists so leadership catches problems early and moves money and people to the right places. Design a better way to do that than a quarterly deck, show from our own history that it would have caught things sooner, and run it beside the current one for a quarter."

The top rung is where durable workflows live, ones that take the human out of the loop. They often need setup first. Before Claude could keep Felix's apps crash-free, it needed to fetch crash reports, map each app version to its git commit, and use Windows, macOS and Linux machines to reproduce and verify fixes. Name that setup as part of the plan.

Know the ceiling. "Go make money" is still too high for most businesses, but the ceiling rises as models get more capable. If a rung has no outside judge, step down one rung.

### Depth: work like the field's best

Go one level below the task, to the underlying data, tools and problems. Keep pushing until even the best people in the field could learn something from the work.

- Use the expert's instruments and media. Where you reach for a markdown table, a top data scientist reaches for a database and a statistical model. The result's medium counts too: a script that reruns the analysis beats a pasted number. The user does not need to know what the experts use. You usually do.
- Set an unreasonable goal, and treat it as reasonable. The page loads in 10 seconds and the user asked for 5? Aim for 200 milliseconds.
- Challenge what everyone believes. Get the raw data and test the belief adversarially: "We believe churn is an onboarding problem. Try to reproduce that from the raw data." In a rewritten prompt, ask for the test, not the verdict: "is the new cache faster than the old one under the same load?", not "show why the new cache is faster".
- Produce new knowledge. Once you are deep in the data, look for blind spots: "Build a simulation of our customers that reproduces the last year from our logs. Then find the earliest signal of churn we don't know about yet, and show it predicts on data it has not seen."
- Bring in an outside judge (rule 3).

Run every Depth pass through Felix's prompt:

> I want a deeper version of this task, not a bigger one. Before rewriting it: (1) say what a top professional in this field would do here that I'm not asking for; (2) name the rawest material they would start from instead of what has already been digested for me; (3) name the specific methods and tools they would use; (4) say what, other than you or me, would show the result is right. Then rewrite my prompt to ask for exactly that.

### Range: bring in other fields

Look at the work through more fields than used to be affordable. Every heist movie spends its first 30 minutes assembling the crew. Felix sees the most magic here, and it takes the most creativity.

People trust themselves only in narrow disciplines. Michelangelo did not want to paint the Sistine Chapel, because he was a sculptor, not a painter. The task's home field is the one its words name, plus its next-door neighbors. Put at least one field on the crew that the task's words would never suggest, and carry its method into the rewritten prompt.

- Replace the nouns with verbs. A trick from *The Art of Innovation* by Tom Kelley and Jonathan Littman. A quarterly review is not "a deck". It is "getting busy people to believe a story about cause and effect, and to decide under uncertainty, in 30 minutes". The verbs show which fields can help.
- Assemble the crew. Raise the stakes: the deck has to be amazing or aliens blow up Earth, so who does humanity send? For quality: an analyst, a journalist and an editor. If it is presented: a motion designer and an audio designer. As a red team: a short seller and a forensic accountant.
- Borrow their tools. A field brings its software, not only its ideas. Felix never thought of 3D for his homepage until his colleague Alex Albert rendered interior designs in Blender, a 3D tool.
- Do, do not play (rule 2). Ask for what a short seller does to research a position, not for prose in a short seller's voice. If you can run subagents, give each field its own subagent with that field's method and tools.

## Make the hard thing feel possible

Felix ends on self-efficacy: people who believe in their own abilities accomplish more, and that belief can be hacked. Locke and Latham's review of 35 years of goal-setting research found that specific hard goals beat "do your best". A model that reads your prompt responds the same way. Build these four moves into every rewritten prompt:

1. A specific hard target, stated as homework. George Dantzig solved two unsolved statistics problems in 1939 because he thought they were homework. Write the target with numbers, in the same plain tone as the rest of the task, as a normal part of the job.
2. Proof that it can be done, when real proof exists. Roger Bannister broke the four-minute mile in 1954, and someone else broke it 46 days later. Name a public result, an open-source project, a competitor or the team's own best run that reached the target or came close. Cite only proof you can point to. If there is none, leave this move out.
3. Permission to miss. *The Inner Game of Tennis* argues you play your best when you stop trying so hard, and Linux started as "just a hobby". Say in the prompt that a missed target, reported with real numbers against the judge, is a good result.
4. A tight first deadline. Patrick Collison's "Fast" list records what people built with audacious goals and tight deadlines. Ask for the first result the judge can score as early as possible, before any polish.

## Output

Size the output to the task. For a request of one or two sentences, steps 1 to 4 fit on one screen, about 300 words: one line per item, no paragraphs. The rewritten prompt is the product, so spend the words there. In this order:

1. The goal beyond the goal, in one line.
2. The types that fit, one line each on why, plus whichever of Altitude, Depth and Range you skipped.
3. The plan for each type you picked. Altitude: the three-rung ladder. Depth: the four answers from Felix's prompt and the hard target. Range: the verbs, then the crew as field, the job they do, and the method or tool they use for it.
4. What it needs: each missing piece of data, tool or access on one short line with what it unlocks, then one line for what is already there.
5. The rewritten prompt in one fenced block the user can copy, written the way they type. It carries the four moves from "Make the hard thing feel possible", the TODO instruction from rule 5 and the "ask me before" lines from rule 6, and it ends with the outside judge and what counts as a pass.
6. Next. Pick the highest rung you can finish and check with the access you have now. For a prompt to improve, name that rung and stop. For a task to do, name it in one line and start. If even the first rung needs access you do not have, ask for it and stop. Ask first, too, for any action that rule 6 names.
7. Report, for a task you did. The work is done when the outside judge has run on the rung you picked. The report is the final answer, so it comes first, and steps 1 to 5 follow it as a recap of at most five lines: the user reads the result first and saw the plan when you started. Open with the answer to the user's question in one or two sentences. Then give the judge's verdict against the hard target as written, with the real numbers, hit or missed, then what you did not get to and the next rung up.

## Example: Altitude and Depth

`/be-ambitious fix the crash in the login screen`

- Goal beyond the goal: people can always log in.
- Types: Altitude and Depth. Range skipped, since a crash fix has one right answer.
- Altitude ladder: (1) fix this crash with a test that fails before and passes after; (2) find every crash of this kind in the crash reports and fix the cause, not the symptom; (3) keep login crash-free: fetch crash reports, map versions to commits, reproduce on every platform, fix and verify without waiting to be asked.
- Depth: start from the raw crash dumps and logs, not the bug report. Reproduce before you fix. Target zero login crashes in the next release, not fewer.
- Outside judge: the failing test turns green, and the crash rate in the reporting tool drops to zero for that build.

```text
Fix the login screen crash. Start from the raw crash dumps and logs, not the bug
report, and reproduce the crash before you change code. Then find every crash of
this kind in the crash reports and fix the shared cause. Target: zero login
crashes in the next release. Felix Rieseberg's team keeps its apps crash-free
with this loop. Show me the failing test first. A miss with real crash counts is
a fine result. Mark anything the dumps do not show as a TODO for me, and ask me
before you ship a build. Pass = the test fails before the fix and passes after,
and the crash tool shows zero login crashes for the new build.
```

## Example: Range

`/be-ambitious help me with my all-hands talk about last month's outage`

- Goal beyond the goal: the outage does not happen again, because the engineers in the room change one habit.
- Types: Range and Altitude. Range because the talk has to land with people who were not there. Depth skipped, since the postmortem already did the root-cause work.
- Altitude ladder: (1) a clear story of what happened; (2) a talk that ends with one decision the room makes; (3) the habit change itself, with a prompt in the deploy tool and a measure of adoption, launched by the talk.
- Verbs: not "a talk", but "making 200 busy people who were not there feel the outage, believe its cause chain, and change one habit, in 15 minutes".
- Crew, as field, job and method:
  - Accident investigator: rebuild the minute-by-minute timeline from raw logs and the incident channel, the way an air-crash board does.
  - Documentary editor: cut the timeline to one story with one turning point, with a paper edit (a ranked list of beats, cut to time).
  - Behavioral scientist, from outside the home field: pick the one habit, design the cue that triggers it, and measure adoption before and after.
  - Red team: an engineer who missed the outage retells the cause chain after a dry run.
- Outside judge: 4 of 5 dry-run listeners retell the cause chain correctly, and the deploy tool shows the habit in 80% of deploys 30 days later.

```text
Help me give a 15-minute all-hands talk on last month's outage. The real job: the
engineers who were not there change one habit, so it does not happen again.
Rebuild the timeline from the raw logs and the incident channel, cut it to one
story with one turning point, pick the single habit that breaks the cause chain,
and design the cue in our deploy tool that prompts it. Ask me before you change
the deploy tool. Target: 4 of 5 people at a dry run retell the cause chain
correctly, and the habit shows up in 80% of deploys 30 days later. Give me the
dry-run version first, before any polish. A missed target with real numbers is
a fine result. Mark anything you cannot find in the logs as a TODO for me.
```
