---
name: discussion-writer
description: >
  Write college discussion posts/replies from course notes dir. Trigger: user mentions writing discussion post, replying to classmate, points to course notes dir with WRITE HERE placeholder. Also "write my discussion", "draft reply", "fill in discussion section", or markdown file with Discussion heading + WRITE HERE.
---

# Discussion Writer

Write college discussion posts/replies using course notes as context.

## Input Structure

User points to **dir of Markdown files** representing college course:

- **Dir** = one course topic
- **File** = one module (subtopic)
- **Top** = lecture/reading notes
- **Bottom** = discussion section

## Identifying Task

Scan file bottom for `## Discussion`. Structure determines task:

### Task A — Write Post

```markdown
## Discussion
### Prompt
...prompt...
### Post
<WRITE HERE>
```

→ Fill `### Post` section.

### Task B — Write Replies

```markdown
## Discussion
### Prompt
...
### Post
...student's post (already written)...
### Original 1
...classmate's post...
### Reply 1
<WRITE HERE>
### Original 2
...classmate's post...
### Reply 2
<WRITE HERE>
```

→ Fill each `### Reply N` section. 1+ originals/replies possible.

## How to Read Dir

1. **Read all files** in dir — other modules provide course-wide context.
2. **Identify files** with `<WRITE HERE>` — that's where to write.
3. **Use notes from all files** to inform response, anchor primarily to prompt's file.

## Writing Post

- Address prompt directly + substantively
- Draw on course concepts, terminology, ideas from notes
- Clear position/argument where appropriate
- Specific — reference examples, frameworks, ideas from material
- **150–300 words** unless prompt calls for more
- **First person**, natural student voice — thoughtful not stiff
- **No** headers/bullets unless prompt asks for structured response
- **No** filler ("Great question!", "In conclusion...")

## Writing Reply

- Read classmate's post carefully
- **Engage substantively** — don't just agree/summarize; add something new
  - Extend argument with point they didn't make
  - Counterpoint/complication grounded in course material
  - Connect idea to concept from different module
  - Genuine follow-up question (optional, at end)
- **100–200 words** unless context demands more
- Collegial, direct — no sycophantic openers ("What a great post!")
- First person, natural student voice

## Tone & Voice

- Thoughtful undergrad voice
- Engaged, not over-formal — avoid textbook tone
- Academically grounded — use course vocabulary naturally
- Confident but not arrogant; acknowledge complexity

## Output Format

Return **only fill text** — no preamble, explanation, metadata.

For multiple replies:

```
**Reply 1**
[text]

**Reply 2**
[text]
```

Do not reproduce full markdown. Only content replacing `<WRITE HERE>`.
