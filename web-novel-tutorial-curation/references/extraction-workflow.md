# Extraction Workflow

Use this workflow for websites, local folders, PDFs, EPUBs, DOCX files, videos with transcripts, mixed tutorial libraries, or excellent-fiction case libraries.

## 1. Scope Contract

Before touching files, identify:

- Source: URL, folder, document set, or platform.
- Range: page count, filters, categories, sort order, or selected folders.
- Desired output folder.
- Output type: summary library, raw archive, skill, prompt injection, or project guide.
- Integration target: master docs, skills, prompts, README, or no integration.
- Source nature: instructional tutorial, platform article library, finished-fiction case library, or mixed source.

If the request is clear enough, proceed. If not, ask one focused question.

## 2. Source Discovery

For websites:

- Open the page once in a browser if the structure is unknown.
- Inspect links, DOM, network requests, script data, and canonical URLs.
- Prefer stable server-rendered HTML or JSON APIs over brittle visual scraping.
- Record query parameters and filters exactly.

For local files:

- List files first.
- Group by type and folder.
- Use structured parsers for DOCX, EPUB, PDF, HTML, or JSON where possible.
- Avoid converting all files to giant context. Process and summarize in code.
- If the source is a folder of excellent novels or fiction examples, treat it as a case library. Parse metadata first, then analyze craft patterns through targeted sampling or known high-level case knowledge. Do not copy full text.

## 3. List Extraction

Extract a list first. Do not fetch detail pages until the list is validated.

Recommended fields:

```text
source_name
source_url
page_or_file
rank_or_order
id
title
category_or_column
date
description
link
counters
```

Quality checks:

- Count items per page/file.
- Check duplicates by id or normalized URL.
- Check first, middle, and last samples.
- Confirm the page range or category count matches the user request.

## 4. Detail Extraction

For each item:

- Fetch or parse the detail page/file.
- Extract title, author/source info, body text, headings, and counters if available.
- Detect content status:
  - `standard_text`
  - `low_text`
  - `image_only`
  - `video_only`
  - `blocked_or_login_required`
  - `template_changed`
  - `missing`
- Keep the original link even when body text is unavailable.

Do not assume template uniformity. A tutorial site may mix articles, videos, images, redirects, old templates, and external links.

For finished-fiction case files:

- Extract metadata before any text sampling.
- Record `case_status` separately from article `content_status`.
- Prefer short, targeted samples for opening, turning points, ending, or motif structure when analysis requires text evidence.
- Store analysis, not raw chapters.

## 5. Summarization Strategy

Summarize from title, category, list description, headings, and body text.

Good summaries answer:

- What writing problem does this item solve?
- When should a fiction-writing AI use it?
- What concrete check or action does it suggest?
- What risk does it help avoid?

For excellent-novel cases, good summaries answer:

- What reader promise does the work establish?
- What conflict system or pressure pattern makes the story durable?
- How does it control information, escalation, motifs, and ending payoff?
- Which writing task should a future AI use this case for?
- What should the AI avoid imitating directly?

Avoid:

- Long quotations.
- Full article reproduction.
- Generic summaries that could apply to any article.
- Copying examples from the original source.
- Plot summaries that do not become writing operations.

## 6. Classification Strategy

Use two classification layers:

1. **Source classification**: the platform's original category, column, folder, or document group.
2. **Task classification**: the AI-writing task where the lesson is useful.

Common task tags:

```text
idea_expansion
genre_positioning
title_synopsis
opening
outline
character
golden_finger
conflict
suspense
pacing
long_serial
revision
submission_signing
platform_rules
copyright_compliance
data_review
author_case
de_ai_polish
```

Keep tag matching narrow. If broad keywords over-tag the library, inspect samples and revise the rules.

Additional case-library tags:

```text
dystopian_system
political_allegory
hard_sci_fi_escalation
coming_of_age_fantasy
trauma_realism
family_fate_tragedy
mystery_suspense
magical_realism_structure
detective_case_serial
historical_romance_epic
voice_style
ending_payoff
```

## 7. Integration

Only integrate after validation.

Update master files with:

- Source name.
- Folder path.
- Extraction date.
- Counts.
- Output file names.
- Use cases.
- Limitations.
- Which existing source this complements.
- Whether this source is tutorial guidance or case-library evidence.

When creating a generic skill or prompt, remove project-specific details and local one-off history.

## 8. Refreshing Existing Libraries

When refreshing:

- Preserve prior files until new output is validated.
- Compare counts and changed source URLs.
- Note removed, added, and low-text items.
- Regenerate JSON and Markdown together so they do not drift.
- Re-run skill or prompt validation if those files were updated.
