---
name: ooga-booga
description: >
  Compress SKILL.md into token-efficient caveman version preserving tech accuracy + agent-usability,
  slashing filler/articles/verbose phrasing. Use when user asks to cavemanify/compress/make caveman/
  token-optimize skill, or says "make shorter / fewer tokens / caveman mode". Also trigger when user
  pastes skill content and asks to compress/minify.
---

# OOGA BOOGA

Turn verbose SKILL.md -> token-efficient caveman version. Keep all technical substance. Kill fluff.

## Goal

Target: ~50-70% token reduction vs original. Floor: skill still usable by agent + readable by human.

## Input

User provides:
- File path to SKILL.md
- Pasted skill content inline
- Both (path + content in context)

If path given, read file first. If content in context, use directly.

## Caveman Rules (all prose)

**Drop:**

- Articles: a / an / the
- Filler: just / really / basically / actually / simply / essentially / generally / typically
- Pleasantries: sure / certainly / please / note that / keep in mind / remember to / make sure to
- Hedging: might want to / you may / feel free to / it's worth noting
- Redundant verbs: "in order to" -> "to", "is able to" -> "can", "will need to" -> "need"
- Padding phrases: "at a high level" / "the process of" / "what this means is"

**Compress:**

- Long noun phrases -> short synonyms: "implement a solution for" -> "fix", "make a determination" -> "decide"
- Common tech terms -> abbreviations: config / auth / DB / fn / impl / req / res / dir / env / ref / doc
- Causality -> arrows: "X causes Y" -> "X -> Y"
- Lists with intros -> just the list (drop "The following are the steps:")
- Passive -> active where shorter: "should be loaded" -> "load"

**Preserve exactly:**

- All technical terms, method names, file paths, code blocks, command strings
- YAML frontmatter structure (name, description fields — compress description prose)
- Section headers (shorten if unambiguous)
- Numbered/bulleted lists (keep structure, compress text inside)
- Warnings / destructive-action callouts (shorten prose, keep WARNING label)
- All conditional logic ("if X then Y" -> "X -> Y" or "if X: Y")

**Fragments OK.** Full sentences not required. One word when enough.

## Output Structure

Produce complete SKILL.md:

1. YAML frontmatter (name unchanged, description compressed)
2. Compressed body — same sections, fewer words
3. Code blocks / file trees / commands untouched

Do NOT add "this is caveman version" note. Just output file.

## Compression Patterns

| Original                                                 | Caveman                                |
| -------------------------------------------------------- | -------------------------------------- |
| "Make sure to read the file before editing"              | "Read file before edit."               |
| "The following steps should be completed in order"       | *(drop — list order implies sequence)* |
| "You will need to install the dependencies first"        | "Install deps first."                  |
| "This is particularly useful for cases where..."         | "Use when..."                          |
| "It's important to note that..."                         | *(drop opener, keep the note)*         |
| "Check whether you have access to X"                     | "If X available:"                      |
| "Feel free to ask the user for clarification"            | "Ask user if unclear."                 |
| "The user might be asking you to do X"                   | "User may want X."                     |
| "Based on the user interview, fill in these components:" | "Fill:"                                |

## Process

1. Read source skill fully.
2. Note: name, core purpose, all required behaviors, file paths.
3. Rewrite section by section applying rules above.
4. Verify: no tech content dropped. All file paths / commands / code intact.
5. Rough token savings check — if <40% reduction, compress harder.
6. Output final SKILL.md.

## Quality Check Before Output

Ask internally:

- Any file path / command / code block changed? -> revert
- Any required behavior dropped? -> restore terse version
- Any section now ambiguous to agent? -> add clarifying word
- Headers still findable? -> OK to shorten if meaning preserved

## Example

**Before (excerpt):**

> Make sure to always read the relevant SKILL.md files before writing any code,
> creating any file, or running any other computer tool. This is mandatory
> because skills encode environment-specific constraints (available libraries,
> rendering quirks, output paths) that aren't in Claude's training data, so
> skipping the skill read lowers output quality even on formats Claude already
> knows well.

**After:**

> Read SKILL.md before any code/file/tool use. Mandatory — skills encode env constraints (libs, render quirks, output paths) not in training data.
