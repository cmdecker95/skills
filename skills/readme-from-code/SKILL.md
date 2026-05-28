---
name: readme-from-code
description: >
  Generate README.md with lessons learned from examining source code.
  Trigger when user asks to create documentation for a code directory,
  write lessons learned from code, summarize what code does, generate a
  README for a project, or document a programming assignment.
  Use this skill whenever someone provides a directory of code files
  and wants a concise README extracted from the code itself — not from
  external specs or assignment prompts.
---

Writes README.md to a code directory. Content derived entirely from examining source files — NOT from assignment prompts, rubrics, or external docs.

## Input

A directory path. Directory contains code files (`.cpp`, `.py`, `.java`, `.ts`, `.tsx`, `.js`, `.h`, etc.) and possibly subdirectories.

## Output

Creates (or overwrites) `README.md` in the target directory.

## Format

```
# [Title Derived from Code Context]
[1-3 sentence brief context — what the code does, key technologies]

## Lessons Learned
- **[Tech1, Tech2, ...]:** Concrete lesson learned from the code. Impact or why it matters.
...
```

### Title
- Use course code + project/module name if directory structure suggests one (e.g., parent dir name like `CS210`)
- Otherwise use a concise descriptive name from the code's purpose

### Context (1-3 sentences)
- What does this code do? (derived from filenames, function names, comments)
- Key languages/frameworks
- Brief enough to orient a reader who hasn't seen the code

### Lessons Learned
Each bullet captures a real insight the code demonstrates:

```
- **[Tech tags]:** Lesson description. Why it matters or impact.
```

Rules:
- **Tech tags** are comma-separated in bold brackets. Always list concrete tech (languages, libraries, frameworks, patterns, tools). E.g., `[C++, std::map, File I/O]`.
- **Lesson** is one sentence describing what the code taught or demonstrates.
- **Impact** is one sentence or fragment showing why it matters (performance, maintainability, correctness, etc.).
- Each lesson must reference something observable in the code — never invent lessons.
- Write in present tense, terse. No filler articles where possible.

Example:
```
- **[C++, std::map]:** Used map for O(log n) frequency lookups instead of vector scan. More readable and scales to large data.
- **[C++, fstream]:** Separate ifstream/ofstream objects prevent accidental file overwrite. Clear read vs write intent.
```

## Process

### 1. Survey the directory
- List all files (excluding `README.md`, `.git/`, build artifacts)
- Identify code files by extension: `.cpp`, `.h`, `.py`, `.java`, `.ts`, `.tsx`, `.js`, `.jsx`, `.cs`, `.go`, `.rb`, `.rs`, `.kt`, `.swift`, `.php`, `.sql`, `.sh`
- Check for config files that reveal tech stack: `package.json`, `pom.xml`, `compose.yml`, `Cargo.toml`, `CMakeLists.txt`, `Makefile`, `tsconfig.json`

### 2. Read the code
- Read every source file in full. Do not skip files or read only a portion — the insights must be comprehensive.
- Pay attention to:
  - Classes, interfaces, type definitions
  - Function/method signatures and their bodies
  - Data structures used (maps, vectors, arrays, custom classes)
  - I/O patterns (file read/write, network, stdin/stdout)
  - Control flow (loops, recursion, state machines)
  - Error handling patterns
  - Design patterns (singleton, iterator, factory, observer, MVC)
  - Comments and documentation
  - Imports/includes
- Take notes — patterns you notice, technologies used, design decisions visible in the code

### 3. Identify technologies
From file extensions + imports/includes + config files, determine:
- Language(s)
- Frameworks / libraries
- Build tools
- Testing frameworks
- Infrastructure (Docker, cloud configs)

### 4. Derive lessons
For each technology or pattern observed, write a lesson:
- What does the code show about this tech?
- What would someone learn by reading this code?
- What tradeoff or decision is visible?

Good lessons are specific and reference actual code. Bad lessons are generic:
- BAD: `"[Python]: Learned about variables and functions."` (too generic, no code reference)
- GOOD: `"[C++, std::map]:` Used map to track item frequencies from grocery data. Insertion and lookup in O(log n) avoids manual array management."

### 5. Write README.md

Write the file to the input directory as `./README.md`.

## Edge Cases

- **Empty directory** (no code files): Write README noting directory is empty.
- **Single file**: Still derive lessons from that one file. Cover its structure, imports, logic.
- **Many subdirectories**: Include lessons about project structure, module separation, build system. Read files across subdirectories.
- **Config files but no code**: Derive lessons from config (e.g., Docker setup, Maven dependencies).
- **README.md already exists**: Overwrite it with the skill-generated version. The skill replaces templated or rubric content with lessons from actual code.
- **Binary-only dir**: Note that no source code was found.

## Checking

- Does every lesson reference something observable in the code?
- Is the format correct (`[Tech tags]): lesson. impact.`)?
- Would someone understand what this code does after reading the context?
