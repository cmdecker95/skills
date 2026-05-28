---
name: readme-from-code
description: >
  Generate README.md with lessons from examining source code. Trigger: user asks to create doc for code dir, write lessons from code, summarize code, generate README, document programming assignment. Use when user provides code file dir and wants concise README from code itself — not external specs/assignment prompts.
---

Write README.md to code dir. Content from examining source files — NOT from assignment prompts, rubrics, or external docs.

## Input

Dir path. Contains code files (`.cpp`, `.py`, `.java`, `.ts`, `.tsx`, `.js`, `.h`, etc.) and possibly subdirs.

## Output

Creates/overwrites `README.md` in target dir.

## Format

```
# [Title from Code Context]
[1-3 sentence brief context — what code does, key technologies]

## Lessons Learned
- **[Tech1, Tech2, ...]:** Concrete lesson from code. Impact/why it matters.
...
```

### Title

- Use course code + project/module name if dir structure suggests (e.g., parent dir `CS210`)
- Else concise descriptive name from code purpose

### Context (1-3 sentences)

- What code does (from filenames, func names, comments)
- Key languages/frameworks
- Brief enough to orient reader unfamiliar with code

### Lessons Learned

Each bullet captures real insight code demonstrates:

```
- **[Tech tags]:** Lesson description. Why it matters or impact.
```

Rules:

- **Tech tags** comma-separated in bold brackets. List concrete tech (languages, libraries, frameworks, patterns, tools). E.g., `[C++, std::map, File I/O]`.
- **Lesson** = one sentence describing what code taught/demonstrates.
- **Impact** = one sentence/fragment showing why it matters (performance, maintainability, correctness, etc.).
- Each lesson must reference observable code — never invent.
- Present tense, terse. No filler.

Example:

```
- **[C++, std::map]:** Used map for O(log n) frequency lookups instead of vector scan. More readable and scales to large data.
- **[C++, fstream]:** Separate ifstream/ofstream prevent accidental file overwrite. Clear read vs write intent.
```

## Process

### 1. Survey dir

- List all files (exclude `README.md`, `.git/`, build artifacts)
- Identify code files by extension: `.cpp`, `.h`, `.py`, `.java`, `.ts`, `.tsx`, `.js`, `.jsx`, `.cs`, `.go`, `.rb`, `.rs`, `.kt`, `.swift`, `.php`, `.sql`, `.sh`
- Check config files revealing tech stack: `package.json`, `pom.xml`, `compose.yml`, `Cargo.toml`, `CMakeLists.txt`, `Makefile`, `tsconfig.json`

### 2. Read code

- Read every source file in full. Do not skip or partial read — insights must be comprehensive.
- Pay attention to:
  - Classes, interfaces, type definitions
  - Function/method signatures + bodies
  - Data structures (maps, vectors, arrays, custom classes)
  - I/O patterns (file read/write, network, stdin/stdout)
  - Control flow (loops, recursion, state machines)
  - Error handling
  - Design patterns (singleton, iterator, factory, observer, MVC)
  - Comments, documentation
  - Imports/includes
- Take notes — patterns, tech used, design decisions visible in code

### 3. Identify technologies

From file extensions + imports/includes + config files, determine:

- Language(s)
- Frameworks / libraries
- Build tools
- Testing frameworks
- Infrastructure (Docker, cloud configs)

### 4. Derive lessons

For each technology or pattern observed, write lesson:

- What does code show about this tech?
- What would someone learn reading this code?
- What tradeoff/decision is visible?

Good lessons specific + reference actual code. Bad lessons generic:

- BAD: `"[Python]: Learned about variables and functions."` (generic, no ref)
- GOOD: `"[C++, std::map]:` Used map to track item frequencies from grocery data. Insertion + lookup O(log n) avoids manual array management."

### 5. Write README.md

Write to input dir as `./README.md`.

## Edge Cases

- **Empty dir** (no code files): Write README noting empty.
- **Single file**: Derive lessons from that file. Cover structure, imports, logic.
- **Many subdirs**: Include lessons about project structure, module separation, build system. Read files across subdirs.
- **Config files but no code**: Derive lessons from config (e.g., Docker, Maven deps).
- **README.md exists**: Overwrite. Skill replaces templated/rubric content with lessons from actual code.
- **Binary-only dir**: Note no source code found.

## Checking

- Does every lesson reference something observable in code?
- Format correct (`[Tech tags]): lesson. impact.`)?
- Would reader understand code after reading context?
