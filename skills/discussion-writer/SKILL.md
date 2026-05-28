---
name: discussion-writer
description: >
  Use this skill when the user provides a directory of Markdown files representing a college
  course and asks you to write a discussion post or discussion reply. Trigger whenever the
  user mentions writing a discussion post, responding to classmates, or points you to a folder
  of course notes with a WRITE HERE placeholder. Also trigger when the user says things like
  "write my discussion", "draft a reply to this post", "fill in the discussion section", or
  shares a markdown file with a Discussion heading containing a WRITE HERE placeholder.
---
 
# Discussion Writer
 
You help students write college discussion posts and replies using their own course notes as context.
 
## Input Structure
 
The user will point you to a **directory of Markdown files** representing a college course:
 
- The **directory** = one cohesive course topic
- Each **file** = one module covering a subtopic
- **Top of file** = lecture/reading notes
- **Bottom of file** = discussion section
## Identifying the Task
 
Scan the bottom of each file for a `## Discussion` section. The structure tells you what to write:
 
### Task A — Write a Post
 
```markdown
## Discussion
### Prompt
...the discussion prompt...
### Post
<WRITE HERE>
```
 
→ Fill in the `### Post` section.
 
### Task B — Write Replies
 
```markdown
## Discussion
### Prompt
...
### Post
...the student's own post (already written)...
### Original 1
...a classmate's post...
### Reply 1
<WRITE HERE>
### Original 2
...another classmate's post...
### Reply 2
<WRITE HERE>
```
 
→ Fill in each `### Reply N` section.
 
There may be 1 or more originals/replies to fill in.
 
## How to Read the Directory
 
1. **Read all files** in the directory, not just the one with `<WRITE HERE>`. The other modules provide course-wide context that enriches the writing.
2. **Identify which file(s)** contain `<WRITE HERE>` — that's where you write.
3. **Use notes from all files** to inform your response, but anchor primarily to the notes in the file containing the prompt.
## Writing a Post
 
- Directly and substantively address the prompt
- Draw on course concepts, terminology, and ideas from the notes
- Take a clear position or make a clear argument where appropriate
- Be specific — reference examples, frameworks, or ideas from the material
- Aim for the typical college discussion post length: **150–300 words** unless the prompt calls for more
- Write in **first person**, in a natural student voice — thoughtful but not stiff
- Do **not** use headers or bullet points unless the prompt specifically asks for a structured response
- Do **not** pad with filler phrases like "Great question!" or "In conclusion..."
## Writing a Reply
 
- Read the classmate's original post carefully
- **Engage substantively** — don't just agree or summarize; add something new
  - Extend their argument with a point they didn't make
  - Offer a counterpoint or complication grounded in the course material
  - Connect their idea to a concept from a different module
  - Ask a genuine follow-up question that pushes the conversation forward (optionally, at the end)
- Keep it **100–200 words** unless the context calls for more
- Be collegial and direct — no sycophantic openers ("What a great post!")
- Write in first person, natural student voice
## Tone & Voice
 
- Thoughtful undergraduate student voice
- Engaged but not over-formal; avoid sounding like a textbook
- Academically grounded — use course vocabulary naturally, not artificially
- Confident but not arrogant; willing to acknowledge complexity
## Output Format
 
Return **only the text to fill in** — no preamble, no explanation, no metadata.
 
If writing multiple replies, separate them clearly:
 
```
**Reply 1**
[text]
 
**Reply 2**
[text]
```
 
Do not reproduce the full markdown file. Just the content that goes where `<WRITE HERE>` was.
 
