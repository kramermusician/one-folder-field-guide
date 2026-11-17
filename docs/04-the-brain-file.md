# 04. The brain file (CLAUDE.md)

`CLAUDE.md` loads into every session. It is the one file the AI always reads. Treat it as rules and routing, not a diary.

## What goes in

1. Who you are, in three lines, plus "read about-me.md".
2. Startup steps: what to read first each session (journal summary, todo.md).
3. The folder map and the filing rule.
4. Always-on rules: the people rule, output style, what never to do.
5. Routing: which teammate handles which kind of job.
6. Pointers: "for PDFs, read SOPs/PDF_SOP.md first."

## What stays out

Project detail. Each project gets its own `README.md` or `CLAUDE.md` inside its folder; the AI reads that only when it works there. One line in the main file points to it.

## Keep it small

Give it a size budget (ours is 50 KB). Before adding a line, ask: does the AI need this before it knows which project it is touching? If not, it goes in the project folder.

## Writing good rules

- Say why. "No bold in handouts, because students skim bold and skip the rest" is followed better than "no bold".
- Date them. "(rule, 2026-11-17)" lets you find and retire old rules.
- Write the failure, not just the fix. "The PDF footer overlapped the table twice; check footer space before saving."
- Prohibitions in plain words. "Never send email. Drafts only."

## The coaching loop

When the AI gets something wrong, do not just fix the output. Say: "write that down as a rule." Ask it which file the rule belongs in. That one habit is how the system gets smarter.

## Back it up

Before a big edit, ask the AI to copy the file to `past-work/brain-backups/CLAUDE.md.<date>`.
