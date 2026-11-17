# 13. Token efficiency: the right model for each job

Every message to an AI costs tokens. On a subscription that means you hit your weekly limit sooner. On pay-as-you-go it means money. The biggest saving is not writing shorter prompts. It is picking the right model for each job.

## The idea (credit: Javier Lozada)

Javier Lozada, a self-taught programmer at Berklee's Creative Technology Center, showed us his pattern in November 2026. He runs it in Cursor with a skill he published: https://github.com/jlozada24/composer-delegate

- One strong model is the lead. It plans, decides and reviews, and can run for days because its context stays clean.
- Many cheaper workers do the volume: reading files, searching, writing code against a clear spec, running tests. Each starts with a fresh, empty context, does one job, and hands back a short receipt.
- The lead never reads the piles of files the workers read. It reads only their summaries and the exact lines they point to.

Think of a head chef and line cooks. The head chef doesn't chop every onion. They decide the menu, taste every plate and send back the ones that are wrong.

## Why it saves so much

Long sessions get expensive because the AI rereads its whole conversation on every turn. If the lead reads 40 files itself, those 40 files ride along on every later message. If a worker reads them and returns ten lines, only the ten lines ride along. You save twice: the work runs on a cheaper model, and the expensive model's context stays small.

## How we built it in Claude Code

We didn't switch to Cursor. We copied the method inside Claude Code:

1. Workers default to Sonnet. One line in `.claude/settings.json` makes every subagent use Sonnet unless the lead asks for something else:
   ```json
   { "env": { "CLAUDE_CODE_SUBAGENT_MODEL": "sonnet" } }
   ```
2. A worker definition, `.claude/agents/sonnet-worker.md`, with strict rules: stay inside the files you were given, never commit or send anything, run the checks, return a receipt. Copy: [examples/claude/agents/sonnet-worker.md](../examples/claude/agents/sonnet-worker.md)
3. A skill, `/sonnet-delegate`, that tells the lead how to decide and how to hand off. Copy: [examples/claude/skills/sonnet-delegate/SKILL.md](../examples/claude/skills/sonnet-delegate/SKILL.md)
4. Background jobs (voice memo routing, sorting, tagging) switched to Sonnet with `claude -p --model sonnet ...`.
5. Some jobs stayed on the strong model on purpose: anything published under your name, graded, or that needs real judgment (design, code review, security).

## Full, split or none

For each request the lead picks one:

- Full: the whole job goes to a worker, and the lead only reviews it. Use this for clear, bounded jobs like renaming, extracting data, a mechanical edit, or building to a clear spec.
- Split: the lead does the thinking and workers do the volume. A worker maps the files and reports back with path:line anchors. The lead makes the decision and writes it as a contract. Another worker builds and tests to that contract.
- None: the lead does it. Use this when the job is mostly judgment, or when writing the handoff would take longer than doing the work.

## A good handoff

The worker knows nothing about your conversation, so every brief says:
- the folder path
- the task and what "done" looks like
- what is already known (file and line)
- which files it may change, or "edit nothing"
- the checks to run
- "no commits, no sending, stop and report if you need more"
- the receipt format

## The model menu (Claude, late 2026)

- Opus: lead, planning, design, review, anything that goes out under your name.
- Sonnet: workers, routing memos, search, extraction, building to a spec, tests.
- Haiku: tiny yes/no or sorting checks, very cheap.
- A local model (Ollama, qwen): free, offline, private. Good for transcription cleanup, extraction, and anything sensitive. Weak at voice and nuance.

Codex users: same idea. Use a strong model for the lead and a smaller one for workers. Name the model in each command you script.

## Measure it

Don't assume it worked. Check your usage page before and after a week. When we checked, about 84% of our usage was on the most expensive model and almost none on Sonnet, even though a third of the work was subagents. That was the opportunity. If a cheaper lane starts making mistakes, move only that lane back up.

## Try this

1. Add the settings line and the worker file to your folder.
2. Ask: "/sonnet-delegate find every file that mentions my ESL course and list them with one line each."
3. Then try a split job: "plan a quiz tool, and have a worker build it."
4. Compare your usage page at the end of the week.
