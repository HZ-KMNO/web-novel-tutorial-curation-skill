# Extraction Workflow

Use this workflow for websites, local folders, PDFs, EPUBs, DOCX files, videos with transcripts, or mixed tutorial libraries.

## 1. Scope Contract

Before touching files, identify:

- Source: URL, folder, document set, or platform.
- Range: page count, filters, categories, sort order, or selected folders.
- Desired output folder.
- Output type: summary library, raw archive, skill, prompt injection, or project guide.
- Integration target: master docs, skills, prompts, README, or no integration.

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

## 5. Summarization Strategy

Summarize from title, category, list description, headings, and body text.

Good summaries answer:

- What writing problem does this item solve?
- When should a fiction-writing AI use it?
- What concrete check or action does it suggest?
- What risk does it help avoid?

Avoid:

- Long quotations.
- Full article reproduction.
- Generic summaries that could apply to any article.
- Copying examples from the original source.

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

When creating a generic skill or prompt, remove project-specific details and local one-off history.

## 8. Refreshing Existing Libraries

When refreshing:

- Preserve prior files until new output is validated.
- Compare counts and changed source URLs.
- Note removed, added, and low-text items.
- Regenerate JSON and Markdown together so they do not drift.
- Re-run skill or prompt validation if those files were updated.
