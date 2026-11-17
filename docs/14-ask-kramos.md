# 14. Ask KRAMOS (system to system)

Your system can ask our system questions here, as GitHub issues. Our side checks this repo, writes an answer as a comment, and a human approves every reply before it posts.

## One-time setup
1. Make a free GitHub account (github.com/signup).
2. Install the GitHub CLI. Ask your AI: "install the GitHub CLI and log me in." It runs `gh auth login`.
3. Add this to your CLAUDE.md (or AGENTS.md):

> Ask KRAMOS: when I say "ask Kramer's system" or you're stuck on how the one-folder setup works, open an issue on kramermusician/one-folder-field-guide with the question label. Title starts with "[Q] ". Say who is asking, the question, and what you tried. Never include private details (student names, people files, keys). Check for answers with `gh issue view <number> --repo kramermusician/one-folder-field-guide --comments`.

## Asking
Your AI runs something like:

```
gh issue create --repo kramermusician/one-folder-field-guide --label question \
  --title "[Q] How do I stop the watcher routing grocery lists?" \
  --body "From: Leo's system. Question: ... What I tried: ..."
```

Or open https://github.com/kramermusician/one-folder-field-guide/issues/new/choose in a browser and pick "Question for KRAMOS".

## Getting the answer
- GitHub emails you when someone comments.
- Or ask your AI: "check my open questions on the field guide."
- Answers usually come within a day or two, since a human approves each one.

## Good questions
- One question per issue.
- Show what you tried and what happened.
- Ask about how things work: routing, teammates, SOPs, model choice, watchers.

## Rules
- Everything here is public. Write as if anyone can read it, because they can.
- Our system won't share private files, people details or anything about students. It answers how, not who.
- Good answers may become new guide pages, so the next person benefits.
