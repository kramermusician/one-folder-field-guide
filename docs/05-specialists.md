# 05. Specialists (your AI team)

A specialist is a markdown file in `team/` that describes a role: what it knows, how it works, what it never does. The AI reads that file when the job matches. It is still one AI; the file just gives it a sharper hat.

## Why bother

- Focus. A "PDF quality checker" with a checklist catches more than a general assistant asked to "check it".
- Memory per craft. Coaching notes go into the right teammate's file, so the lesson sticks to the job.
- Fun. Named teammates make the system feel like a studio, and you'll use it more.

## Anatomy of a teammate file

```markdown
# Nova - Slide Designer

## Role
Builds class slideshows. One idea per slide, big type, warm colors.

## Always
- Read SOPs/Slideshow_SOP.md first.
- 28pt minimum body text.
- End every deck with one question for students.

## Never
- Paragraphs on a slide.
- Stock-photo clichés.

## Coaching log
- 2026-11-17: Too much text on slide 4. Rule: max 12 words per slide.
```

## Routing

In CLAUDE.md, list who does what:

```
- Slides -> Nova
- Handouts and PDFs -> Paige; final check -> Sage
- Research -> Pax
- Writing in my voice -> Cosmo
```

## Patterns that work

- Maker and checker. One teammate builds, a different one checks against a list. The checker never fixes, only reports.
- Orchestrator. One teammate (we call ours Larry) is the front desk: it reads the request and routes it.
- Hire from pain. Add a teammate when the same kind of mistake shows up three times.
- Keep the file short. Under a page. Long detail goes in an SOP the teammate points to.
- Use the template in `team/_new-teammate-TEMPLATE.md` from the starter kit.
