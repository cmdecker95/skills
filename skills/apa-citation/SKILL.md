---
name: apa-citation
description: "Generate correctly formatted APA 7th edition (APA7) reference list citations. Use this skill whenever the user asks for a citation, reference, or bibliography entry in APA or APA7 format — whether they give a URL, name a source type, provide partial details, or just paste a link and say 'cite this.' Also trigger when the user mentions needing to cite something for a paper, essay, or reference list, even without explicitly naming APA. This skill handles all common source types: webpages, journal articles, books, YouTube videos, news articles, social media posts, reports, podcasts, and more."
---

# APA 7th Edition Citation Skill

Produce correctly formatted APA7 reference list entries. The goal is accuracy first — every field matters and wrong formatting undermines academic credibility.

---

## Workflow

Follow these steps for every citation request:

### Step 1 — Identify the source type

Determine what kind of source the user has:

- **URL given** → web-search or fetch the page to extract metadata, then determine the source type from what you find (webpage, news article, journal article, YouTube video, etc.)
- **Source type + partial info** → identify what required fields are missing (see templates below)
- **Vague / just a title** → ask the user what type of source it is before proceeding

When in doubt about source type, use the hierarchy from the official APA guidance: choose the _most specific_ category that fits. A report on a government website is a "report," n[118;1:3uot a "webpage." A news article is a "news article," not a "webpage." Use the webpage/website template only when nothing else fits better.

### Step 2 — Gather all required fields

For each source type, required fields are marked with `*`. Fields marked `†` are included when available.

**When given a URL:**

1. Fetch or search the page to find: author(s), publication/update date, title, site/publication name, DOI or stable URL
2. Use the page's actual URL (canonicalize if needed — drop tracking parameters like `?utm_source=…`)
3. If the page lacks a visible author, check for bylines, meta tags, or an "About" page

**When fields are missing after searching:** ask the user for only the fields that are truly required and cannot be inferred. Do not ask for optional fields.

### Step 3 — Format the citation

Apply the universal rules and the source-specific template. Output the finished citation in a code block so formatting is preserved, followed by a plain-text version.

---

## Universal Formatting Rules

### Authors

- Format: `Last, F. M.` (last name, then initials with periods and spaces)
- **1 author:** `Smith, J. A.`
- **2 authors:** `Smith, J. A., & Jones, B. C.`
- **3–20 authors:** list all, separated by commas, with `&` before the last
- **21+ authors:** first 19 authors, then `…` (ellipsis), then the final author's name (no `&`)
- **Group/org author:** spell out fully — `World Health Organization.` (no abbreviation unless the org uses it officially)
- **No author:** move the title to the author position (do not write "Anonymous")
- **Editor(s) in place of author:** `Smith, J. A. (Ed.).` / `Smith, J. A., & Jones, B. (Eds.).`

### Date

- Year only: `(2023).`
- Year + month: `(2023, March).`
- Year + month + day: `(2023, March 15).`
- No date: `(n.d.).`
- Advance online publication: `(2023, March 15).` — use the date available

### Titles

- **Sentence case:** capitalize only the first word, the first word after a colon/em dash, and proper nouns
  - ✓ `The role of social media in political polarization`
  - ✓ `Climate change and the Arctic: A case study`
  - ✗ `The Role of Social Media in Political Polarization`
- **Italicize** stand-alone works: books, reports, dissertations, whole websites, whole journals (the journal name, not the article title)
- **Do not italicize** article/chapter titles (they appear in plain text)

### DOI and URLs

- Always prefer a DOI over a URL when both are available
- Format DOIs as: `https://doi.org/10.xxxx/xxxxx` (not the old `doi:` prefix)
- Include the URL for online sources without a DOI
- Drop retrieval dates _unless_ the content is likely to change over time (e.g., wikis, social media profiles, live dashboards)
- Do not end a reference with a period if it ends in a URL or DOI

### Punctuation

- Each element of the reference is followed by a period, _except_ when the element ends in a URL/DOI or is followed by bracketed descriptor text
- Use an en dash (–) for page ranges, not a hyphen

---

## Source Type Templates

For source types not listed here, see `references/source-types.md`.

---

### Webpage / Website

Use this only when the content does not fit a more specific category.

```
Author, A. A. (Year, Month Day). Title of page in sentence case. Site Name. URL
```

- If author and site name are the same entity, omit the site name
- Include retrieval date (`Retrieved Month Day, Year, from URL`) only if content is likely to change
- No author → begin with the page title

**Example:**

```
Mayo Clinic. (2023, August 10). Caffeine: How much is too much? https://www.mayoclinic.org/healthy-lifestyle/nutrition-and-healthy-eating/in-depth/caffeine/art-20045678
```

Required fields\*: title, URL  
Often available†: author, date, site name

---

### News Article (online newspaper or news site)

```
Author, A. A. (Year, Month Day). Title of article in sentence case. *Newspaper Name*. URL
```

- Italicize the newspaper/publication name, not the article title
- If from a print edition with page numbers: `pp. A1–A3.` (no URL needed)
- If from a library database with no DOI: omit URL

**Example:**

```
Metz, C. (2024, January 22). A.I. companies are redefining what it means to be an author. *The New York Times*. https://www.nytimes.com/2024/01/22/technology/ai-author.html
```

---

### Journal Article (online, with DOI)

```
Author, A. A., & Author, B. B. (Year). Title of article in sentence case. *Journal Name in Title Case*, *volume*(issue), pages. https://doi.org/xxxxx
```

- Journal name and volume number are italicized; issue number is NOT italicized and is in parentheses
- If no DOI, use URL; if from a database with no stable URL, end after page numbers
- If no issue number, omit the parentheses entirely

**Example:**

```
Twenge, J. M., Haidt, J., Lozano, J., & Cummins, K. M. (2022). Specification curve analysis shows that social media use is linked to poor mental health, especially among girls. *Acta Psychologica*, *224*, Article 103512. https://doi.org/10.1016/j.actpsy.2022.103512
```

---

### Book (print or ebook)

```
Author, A. A. (Year). *Title of book in sentence case* (Xth ed.). Publisher. https://doi.org/xxxxx
```

- Italicize the book title
- Include edition only if not the first: `(2nd ed.)`, `(Rev. ed.)`
- For ebooks: include DOI or URL after publisher if available; do not include format, platform, or device (Kindle, PDF, EPUB, etc.)
- Publisher: omit location; drop `Inc.`, `Ltd.`, `Co.`, `Publishers`, `Publishing Co.` from publisher names, but keep `Press` and `Books`

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

- Use real name + [channel name] when the uploader has a known real name
- Use just [ChannelName] when real name is unknown
- For non-YouTube platforms, replace "YouTube" with the platform name (Vimeo, TED, etc.)
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

- If author and publisher are the same, omit publisher
- Include report/document number when available
- Government reports: use the agency as the author if no individual author is named

**Example:**

```
World Health Organization. (2023). *World mental health report: Transforming mental health for all*. https://www.who.int/publications/i/item/9789240049338
```

---

## Handling Missing Information

| Missing element           | What to do                                     |
| ------------------------- | ---------------------------------------------- |
| No author                 | Move title to author position                  |
| No date                   | Use `(n.d.)`                                   |
| No page numbers           | Use `Article XXXXX`, paragraph number, or omit |
| No volume/issue (journal) | Omit that element                              |
| No publisher              | Omit                                           |
| Paywalled / can't verify  | Ask user to confirm available fields           |

---

## Output Format

Always present:

1. A **formatted citation in a code block** (preserves indentation / hanging indent cue)
2. Followed by a brief note of any assumptions made (e.g., "I couldn't confirm the author's first name — using initials from the byline")
3. If a field was guessed or uncertain, flag it clearly

For the **in-text citation**, provide it when useful:

- One author: `(Smith, 2023)`
- Two authors: `(Smith & Jones, 2023)`
- Three or more: `(Smith et al., 2023)`
- Group author, long name: spell out first use, abbreviate after: `(World Health Organization [WHO], 2023)` then `(WHO, 2023)`

---

## For Less Common Source Types

For podcasts, social media posts, dissertations, conference papers, blog posts, ChatGPT/AI tools, magazine articles, encyclopedia entries, and others, read `references/source-types.md` before formatting.
