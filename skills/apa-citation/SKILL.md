---
name: apa-citation
description: "Generate APA7 reference citations. Trigger when user asks for citation/reference/bibliography entry in APA format — URL given, source type named, partial details, or link pasted with 'cite this.' Also trigger when user needs citation for paper/essay/reference list. Handles: webpages, journal articles, books, YouTube videos, news articles, social media, reports, podcasts, etc."
---

# APA 7th Edition Citation Skill

Produce correct APA7 reference entries. Accuracy first — every field matters; wrong formatting undermines academic credibility.

---

## Workflow

For every citation request:

### Step 1 — Identify source type

- **URL given** → web-search/fetch page, extract metadata, determine source type (webpage, news article, journal article, YouTube video, etc.)
- **Source type + partial info** → identify missing required fields (see templates below)
- **Vague / just title** → ask user what type of source

When unsure: use APA hierarchy — pick most specific category. Report on gov site = "report," not "webpage." News article = "news article," not "webpage." Use webpage template only when nothing else fits.

### Step 2 — Gather required fields

`*` = required. `†` = include when available.

**URL given:**

1. Fetch/search page for: author(s), publication/update date, title, site/publication name, DOI or stable URL
2. Use page's actual URL (canonicalize — drop tracking params like `?utm_source=…`)
3. No visible author → check bylines, meta tags, or "About" page

**Fields still missing after search:** ask user only for required fields that can't be inferred. Skip optional fields.

### Step 3 — Format citation

Apply universal rules + source-specific template. Output citation in code block (preserves formatting), followed by plain-text version.

---

## Universal Formatting Rules

### Authors

- Format: `Last, F. M.`
- **1 author:** `Smith, J. A.`
- **2 authors:** `Smith, J. A., & Jones, B. C.`
- **3–20 authors:** list all, comma-separated, `&` before last
- **21+ authors:** first 19, `…`, then final author (no `&`)
- **Group/org author:** spell out fully — `World Health Organization.` (no abbreviation unless org uses it officially)
- **No author:** move title to author position (no "Anonymous")
- **Editor(s) in place of author:** `Smith, J. A. (Ed.).` / `Smith, J. A., & Jones, B. (Eds.).`

### Date

- Year only: `(2023).`
- Year + month: `(2023, March).`
- Year + month + day: `(2023, March 15).`
- No date: `(n.d.).`
- Advance online publication: `(2023, March 15).` — use date available

### Titles

- **Sentence case:** capitalize first word, first word after colon/em dash, proper nouns only
- **Italicize** stand-alone works: books, reports, dissertations, whole websites/journals (journal name, not article title)
- **Do not italicize** article/chapter titles (plain text)

### DOI and URLs

- Prefer DOI over URL when both available
- Format DOIs: `https://doi.org/10.xxxx/xxxxx` (not old `doi:` prefix)
- Include URL for online sources without DOI
- Drop retrieval dates unless content changes (e.g., wikis, social media profiles, live dashboards)
- No period after URL/DOI

### Punctuation

- Each element ends with period, except when ending in URL/DOI or followed by bracketed descriptor
- En dash (–) for page ranges, not hyphen

---

## Source Type Templates

Types not listed → see `references/source-types.md`.

---

### Webpage / Website

Use only when content fits no more specific category.

```
Author, A. A. (Year, Month Day). Title of page in sentence case. Site Name. URL
```

- If author = site name, omit site name
- Retrieval date (`Retrieved Month Day, Year, from URL`) only if content changes
- No author → begin with page title

**Example:**
```
Mayo Clinic. (2023, August 10). Caffeine: How much is too much? https://www.mayoclinic.org/healthy-lifestyle/nutrition-and-healthy-eating/in-depth/caffeine/art-20045678
```

Required\*: title, URL  
Often available†: author, date, site name

---

### News Article (online newspaper or news site)

```
Author, A. A. (Year, Month Day). Title of article in sentence case. *Newspaper Name*. URL
```

- Italicize newspaper/publication name, not article title
- Print edition with pages: `pp. A1–A3.` (no URL)
- Library database, no DOI: omit URL

**Example:**
```
Metz, C. (2024, January 22). A.I. companies are redefining what it means to be an author. *The New York Times*. https://www.nytimes.com/2024/01/22/technology/ai-author.html
```

---

### Journal Article (online, with DOI)

```
Author, A. A., & Author, B. B. (Year). Title of article in sentence case. *Journal Name in Title Case*, *volume*(issue), pages. https://doi.org/xxxxx
```

- Journal name + volume italicized; issue NOT italicized, in parentheses
- No DOI → use URL; database without stable URL → end after pages
- No issue number → omit parentheses

**Example:**
```
Twenge, J. M., Haidt, J., Lozano, J., & Cummins, K. M. (2022). Specification curve analysis shows that social media use is linked to poor mental health, especially among girls. *Acta Psychologica*, *224*, Article 103512. https://doi.org/10.1016/j.actpsy.2022.103512
```

---

### Book (print or ebook)

```
Author, A. A. (Year). *Title of book in sentence case* (Xth ed.). Publisher. https://doi.org/xxxxx
```

- Italicize book title
- Edition only if not first: `(2nd ed.)`, `(Rev. ed.)`
- Ebooks: DOI or URL after publisher if available; no format/platform/device (Kindle, PDF, EPUB, etc.)
- Publisher: omit location; drop `Inc.`, `Ltd.`, `Co.`, `Publishers`, `Publishing Co.`; keep `Press` and `Books`

**Example:**
```
Kahneman, D. (2011). *Thinking, fast and slow*. Farrar, Straus and Giroux.
```

---

### Book Chapter in Edited Volume

```
Author, A. A. (Year). Title of chapter in sentence case. In E. E. Editor & F. F. Editor (Eds.), *Title of book* (pp. xx–xx). Publisher. https://doi.org/xxxxx
```

**Example:**
```
Baumeister, R. F. (2018). Self-regulation and self-control. In R. F. Baumeister & K. D. Vohs (Eds.), *Handbook of self-regulation: Research, theory, and applications* (3rd ed., pp. 3–27). Guilford Press.
```

---

### YouTube Video or Online Video

```
Author, A. A. [ChannelName]. (Year, Month Day). *Title of video in sentence case* [Video]. YouTube. URL
```

- Real name + [channel name] when uploader has known real name
- [ChannelName] only when real name unknown
- Non-YouTube platforms → replace "YouTube" with platform name (Vimeo, TED, etc.)
- Use `[Video]` descriptor

**Example:**
```
Kurzgesagt – In a Nutshell. (2023, September 12). *The last human* [Video]. YouTube. https://www.youtube.com/watch?v=LEENEFaVUzU
```

---

### Report (government, corporate, or institutional)

```
Author, A. A., or Organisation Name. (Year). *Title of report in sentence case* (Report No. xxx). Publisher Name. URL
```

- If author = publisher, omit publisher
- Include report/document number when available
- Gov reports: use agency as author if no individual author named

**Example:**
```
World Health Organization. (2023). *World mental health report: Transforming mental health for all*. https://www.who.int/publications/i/item/9789240049338
```

---

## Handling Missing Information

| Missing | What to do |
|---|---|
| No author | Move title to author position |
| No date | Use `(n.d.)` |
| No page numbers | Use `Article XXXXX`, paragraph number, or omit |
| No volume/issue (journal) | Omit that element |
| No publisher | Omit |
| Paywalled / can't verify | Ask user to confirm available fields |

---

## Output Format

Always present:

1. Formatted citation in code block (preserves hanging indent)
2. Brief note of assumptions (e.g., "couldn't confirm author first name — using initials from byline")
3. Flag uncertain/guessed fields

### In-text citation (when useful)

- One author: `(Smith, 2023)`
- Two authors: `(Smith & Jones, 2023)`
- Three+: `(Smith et al., 2023)`
- Group author, long name: spell out first, abbreviate after: `(World Health Organization [WHO], 2023)` → `(WHO, 2023)`

---

## Less Common Source Types

Podcasts, social media posts, dissertations, conference papers, blog posts, ChatGPT/AI tools, magazine articles, encyclopedia entries, etc. → read `references/source-types.md` before formatting.
