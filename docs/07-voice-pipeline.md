# 07. Voice pipeline

The habit that makes the system feel alive: talk to your phone, and a minute later the right files have changed.

## The flow

1. Phone Shortcut records a memo and saves it to `team-inbox/voice/` (Dropbox).
2. A watcher on your Mac notices the new file.
3. Whisper (free, runs on your Mac) turns it into text in `team-inbox/transcripts/`.
4. The watcher hands the transcript to Claude (or Codex) with `tools/route-prompt.md`.
5. The AI routes it: to-dos to `todo.md`, people to `people/`, ideas to `topics/`, work orders to `owners-inbox/_New/`.
6. It logs what it did in `activity-log.md`. The memo moves to `team-inbox/processed/`.

## Good memos

- One idea per memo, one language per memo.
- Say names clearly. "Add to Sam Ortiz's file: he wants the drum charts."
- Say the verb. "Remind me", "idea", "make me", "journal".

## Things to teach the route prompt over time

- Never build anything big from a memo; propose it in `_New/` instead.
- Grocery lists and shopping never become pages.
- If unsure where something goes, `_New/`, with a note why.
