# 03. The people folder

This is the single most useful habit in the whole system.

Every person you mention gets a file: `people/first-last.md`. A colleague, a student, a dentist, a bandmate, your aunt, the guy who fixes your car. The AI creates it the first time the name comes up, then adds to it every time after.

## Why it works

An assistant without memory treats every name as a stranger. With a people folder:

- "Draft a thank-you to Marta" comes out right, because the AI knows Marta lent you the amp, prefers Spanish, and has a gig on Friday.
- "Who did I promise something to?" has an answer.
- Before a meeting, "brief me on Sam" gives you the last three things you talked about.
- Birthdays, kids' names, favorite restaurants, what someone is struggling with: remembered, so you can be a better friend and colleague.

## The rule to put in CLAUDE.md

> People rule: whenever I mention a person, check `people/` (file names and `aliases`). If there is no file, create `people/first-last.md` right away using the template. Never leave a named person without a file. Link to them as `[[first-last|First Last]]`.

## The template

```markdown
---
type: person
name: Marta Ruiz
aliases: [Marta, Ms. Ruiz]
relationship: colleague
created: 2026-11-17
tags: [person, colleague]
---

# Marta Ruiz

## Who
Guitar faculty, Building 7. Met at orientation 2025.

## How to work with her
- Prefers Spanish in messages. Short and warm.
- Answers email in the morning, never at night.

## Things to remember
- Lent me the Fender amp (2026-10-02). Return by December.
- Daughter Lucía starts college next fall.

## Log
- 2026-11-17: Talked about co-teaching a songwriting lab. She's in.
```

## Tips

- Aliases matter. Add nicknames and spellings ("Jo", "Joanna", "Prof. Kim") so the AI finds the file whatever you call them.
- Log, don't rewrite. New facts go at the bottom with a date. History is the value.
- Let voice memos feed it. "Remind me to call Sam about the drum kit" should create or update `people/sam-....md` and add a to-do that links to it.
- Groups get folders. Students for a course can live in `people/<course>/`.
- Ask it questions. "Who have I not talked to in two months?" "Which people are linked to the jazz project?"
- Be kind in what you write. Write every file as if the person might read it one day.

## Privacy

People files hold real details about real people. Keep them local, keep the folder private, and never paste them into a public repo or website. This guide uses only invented people.
