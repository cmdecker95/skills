---
name: discussion-writer
description: >
  Write college discussion posts/replies from course notes. Rewrite placeholder
  in actual file. Trigger: user mentions writing discussion post, dir w/
  placeholder (WRITE HERE / WRITE ME / TODO / <blank>). Also "write my discussion",
  "draft reply", "fill discussion section", markdown w/ Discussion heading + placeholder.
---

# Discussion Writer

Write discussion posts/replies from course notes. Rewrite file in-place.

## Input

Dir of Markdown files (course):
- Dir = course topic
- File = module (subtopic)
- Top = lecture/reading notes
- Bottom = discussion section

## Identify Task

Scan file bottom for `## Discussion`. Structure determines task:

### Task A — Post

```markdown
## Discussion
### Prompt
...
### Post
<WRITE HERE>
```

→ Fill `### Post`.

### Task B — Replies

```markdown
## Discussion
...
### Original 1
...classmate post...
### Reply 1
<WRITE HERE>
### Original 2
...
### Reply 2
<WRITE HERE>
```

→ Fill each `### Reply N`.

## Placeholder Variants

Recognize (case-insensitive):
- `<WRITE HERE>` / `WRITE HERE`
- `WRITE ME`
- `TODO`
- `<blank>` / `[blank]` / `[Write here]`
- Any similar variant

## Read Dir

1. Read all files in dir (other modules = context).
2. Find files w/ placeholder -> those need writing.
3. Use all notes, anchor to prompt's file.

## Writing Post

- Address prompt directly + substantively
- Draw on course concepts, terminology, ideas
- Clear position/argument where appropriate
- Specific — reference examples, frameworks from material
- 150–300 words unless prompt says more
- First person, natural student voice
- No headers/bullets unless prompt asks
- No filler ("Great question!", "In conclusion...")

## Writing Reply

- Read classmate post carefully
- Engage substantively — dont just agree/summarize
  - Extend w/ point they didn't make
  - Counterpoint grounded in course material
  - Connect to different module
  - Genuine follow-up question (optional end)
- 100–200 words unless context demands more
- Collegial, direct — no "What a great post!"
- First person, natural student voice

## Tone

- Thoughtful undergrad
- Engaged, not over-formal
- Academically grounded (course vocabulary)
- Confident but not arrogant

## Rewrite File

**Rewrite file in-place** (e.g., `Module 4.md`). Replace placeholder in actual file with generated text (write via tool). Write multiple replies into respective `### Reply N` sections. Do NOT return content as output.
