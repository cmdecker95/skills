---
name: readme-from-code
description: >
  Generate or vet+upsert README.md from source code. Trigger when user asks create README from code, edit existing README, audit README, check drift, verify README vs impl, reconcile docs with code, refresh outdated README, document project/subfolder, summarize lessons learned, or add assignment brief + takeaways from impl. Use whenever README must match code reality (not rubrics/external specs), even if user does not say "from code".
---

Write or upsert `README.md` in project root or subfolder. Content from code in scope.

If README exists, vet vs code and update in place:
- Keep accurate, useful context.
- Fix/remove claims not supported by code.
- Normalize structure: short assignment brief top, high-impact lessons below.

## Input

Target scope path (whole project or subfolder). Contains code files (`.cpp`, `.py`, `.java`, `.ts`, `.tsx`, `.js`, `.h`, etc.) and maybe subdirs.

## Output

Create or update `README.md` in target scope dir.

## Format

```
# [Title from Code Context]

## Assignment Brief
[2-4 sentence brief: what this code implements, scope, and key constraints/approach inferred from code]

## Lessons Learned (High Impact)
- **[Tech1, Tech2, ...]:** Concrete lesson from code. Why it matters (correctness, speed, reliability, maintainability, etc.).
...
```

### Title

- Use course code + project/module name if structure suggests (e.g., parent dir `CS210`).
- Else use concise title from code purpose.

### Assignment Brief (2-4 sentences)

- State what code in scope does (filenames, fns, comments, module boundaries).
- Include key languages/frameworks/tools in scope.
- If subfolder target, note ownership vs project-wide system.
- Keep concise, factual; no invented reqs.

### Lessons Learned (High Impact)

Each bullet = real insight from code:

```
- **[Tech tags]:** Lesson description. Why it matters or impact.
```

Rules:

- **Tech tags** comma-separated in bold brackets. Use concrete tech (languages, libs, frameworks, patterns, tools). Example: `[C++, std::map, File I/O]`.
- **Lesson** = one sentence: what code demonstrates.
- **Impact** = one sentence/fragment: why it matters (performance, maintainability, correctness, reliability, security, operability).
- Each lesson must reference observable code — never invent.
- Prioritize high-impact lessons over exhaustive low-value detail.
- Present tense, terse, no filler.

Example:

```
- **[C++, std::map]:** Used map for O(log n) frequency lookups instead of vector scan. More readable and scales to large data.
- **[C++, fstream]:** Separate ifstream/ofstream prevent accidental file overwrite. Clear read vs write intent.
```

## Process

### 1. Survey dir

- Determine scope root from user request (whole project or subfolder).
- List files in scope (exclude `.git/`, build artifacts, caches).
- Identify code files by extension: `.cpp`, `.h`, `.py`, `.java`, `.ts`, `.tsx`, `.js`, `.jsx`, `.cs`, `.go`, `.rb`, `.rs`, `.kt`, `.swift`, `.php`, `.sql`, `.sh`
- Check stack/config files: `package.json`, `pom.xml`, `compose.yml`, `Cargo.toml`, `CMakeLists.txt`, `Makefile`, `tsconfig.json`.
- Check for existing `README.md` in scope.

### 2. Read code

- Read source files in scope fully. No partial assumptions.
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
- Note patterns, architecture decisions, tradeoffs, outcomes visible in code.

### 3. Vet existing README (if present)

- Parse existing sections and claims.
- Mark each claim as:
  - **Supported** by code in scope -> keep (tighten wording if needed).
  - **Partially supported** -> rewrite precise, code-grounded claim.
  - **Unsupported/outdated** -> remove.
- Preserve useful non-conflicting context that helps orientation.
- Reconcile terminology with actual symbols/files in code.

### 4. Identify technologies

From extensions + imports/includes + config files, determine:

- Language(s)
- Frameworks / libraries
- Build tools
- Testing frameworks
- Infrastructure (Docker, cloud configs)

### 5. Derive high-impact lessons

For each observed tech/pattern, write lesson:

- What does code show about this tech?
- What would reader learn from this code?
- What important tradeoff/decision is visible?
- Why does it matter in practice?

Good lessons: specific + code-grounded. Bad lessons: generic.

- BAD: `"[Python]: Learned about variables and functions."` (generic, no ref)
- GOOD: `"[C++, std::map]:` Used map to track item frequencies from grocery data. Insertion + lookup O(log n) avoids manual array management."

### 6. Upsert README.md

Write/update `./README.md` at scope root.

Upsert behavior:
- If no README exists, create using required format.
- If README exists, preserve valid context where helpful but enforce required section order:
  1. `# Title`
  2. `## Assignment Brief`
  3. `## Lessons Learned (High Impact)`
- Replace stale or generic lesson bullets with code-grounded high-impact bullets.

## Edge Cases

- **Empty dir** (no code files): Write README noting empty.
- **Single file**: Derive lessons from that file. Cover structure, imports, logic.
- **Many subdirs**: Include lessons about project structure, module separation, and build system. Read files across subdirs in scope.
- **Subfolder target**: Document module-level behavior; include note README covers subfolder scope.
- **Config files but no code**: Derive lessons from config (e.g., Docker, Maven deps).
- **README.md exists**: Vet + upsert in place. Do not blindly overwrite accurate content.
- **Binary-only dir**: Note no source code found.

## Checking

- Are assignment brief statements supported by code in scope?
- Does every lesson reference something observable in code?
- Are lessons high-impact (not trivial restatements)?
- Format correct (`[Tech tags]: lesson. impact.`)?
- Would a new reader understand what was built and why the lessons matter?
