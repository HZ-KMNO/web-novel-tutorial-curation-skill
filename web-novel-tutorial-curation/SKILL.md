---
name: web-novel-tutorial-curation
description: Use this skill when an AI agent must extract, summarize, classify, validate, and integrate web-novel or fiction-writing tutorial materials from websites, documents, or local folders into reusable knowledge files. It is designed for Chinese web novel / online fiction workflows, but the extraction and quality-control process is general enough for any AI agent handling writing-course curation.
---

# Web Novel Tutorial Curation

Use this skill when the task is to turn writing tutorials, author lessons, platform articles, course pages, videos, PDFs, EPUBs, or local notes into a clean AI-usable knowledge base for web-novel / fiction writing.

The goal is not to copy tutorials. The goal is to produce structured, searchable, source-linked craft knowledge that future AI agents can use while planning, drafting, revising, and polishing fiction.

## Core Rule

Always separate four things:

1. **Source extraction**: what exists at the source.
2. **Summarization**: what the source teaches.
3. **Operational use**: when an AI writer should apply it.
4. **Validation**: proof that counts, files, links, JSON, and references are correct.

Do not merge these phases casually. Most mistakes happen when an agent scrapes first, summarizes too early, or updates master files before validating the extracted library.

## Quick Workflow

1. **Clarify the scope**
   - Source URL or folder.
   - Page range, filters, sort order, categories, or file types.
   - Output folder.
   - Whether to update existing master prompts, skills, or project guides.

2. **Discover the data surface**
   - Inspect the page in a browser if needed.
   - Check whether data comes from server HTML, rendered DOM, JSON APIs, script state, or document files.
   - Prefer stable APIs or server HTML when available.
   - Record the exact source URL, filters, and extraction date.

3. **Extract lists before details**
   - Fetch all requested pages or files.
   - Parse article title, link, id, category/column, date, counters, and short description.
   - Deduplicate by stable id or canonical URL.
   - Validate list counts before fetching details.

4. **Fetch details conservatively**
   - Fetch detail pages or document text.
   - Detect missing, blocked, image-only, video-only, or non-standard templates.
   - Keep a content-status field such as `standard_text`, `low_text`, `video`, `image_only`, or `template_changed`.
   - Do not fail the whole job when some detail pages have little text; summarize those from title/list metadata and mark the limitation.

5. **Summarize without copying**
   - Do not store full copyrighted article bodies unless the user explicitly owns the source and asks for it.
   - Save concise summaries, key lessons, tags, use cases, and original links.
   - Keep short headings or metadata only when useful.
   - Convert examples into general principles rather than reproducing long original passages.

6. **Classify for AI use**
   - Classify by source category/column.
   - Classify by writing task themes, such as opening, outline, character, conflict, pacing, signing, genre, revision, copyright, or de-AI polishing.
   - Build both human-readable Markdown and machine-readable JSON.

7. **Validate before integration**
   - Check file existence and sizes.
   - Parse JSON.
   - Confirm article counts by category/theme.
   - Inspect several sample rows for bad tags, broken summaries, mojibake, duplicated items, or over-broad matching.
   - Regenerate if the output looks mechanically wrong.

8. **Integrate into master files**
   - Update source registries, prompts, skills, and workflow guides only after the extracted library passes validation.
   - Add a short description of the new source, counts, file paths, use cases, and limitations.
   - Remove stale or project-specific references from generic prompt files.

## When To Read References

- Read [references/extraction-workflow.md](references/extraction-workflow.md) for the full extraction and integration process.
- Read [references/output-templates.md](references/output-templates.md) when creating Markdown or JSON outputs.
- Read [references/quality-gates.md](references/quality-gates.md) before finalizing or when the output seems noisy, over-tagged, stale, or inconsistent.

## Output Standard

At minimum, produce:

- `00_Overview.md` or localized equivalent.
- A complete article index in Markdown.
- A category/column summary.
- A theme/tag summary.
- A JSON index with stable metadata.

Each article record should include:

```text
source
source_url
extraction_date
rank/page/order if applicable
title
canonical link
category or column
date
available counters
content_status
tags
summary
usable_experience
limitations
```

## Common Mistakes To Avoid

- Treating rendered page text as the only source without checking APIs or server HTML.
- Assuming all detail pages share the same template.
- Storing full copyrighted tutorials when summaries are enough.
- Letting broad keywords create bad tags.
- Updating master prompts before validating extracted files.
- Leaving project-specific material inside a generic skill or prompt.
- Forgetting exact counts, page ranges, filter parameters, or low-text page counts.
- Using destructive cleanup commands while reorganizing files.

## Safety And File Hygiene

- Do not batch delete user files or folders.
- Do not overwrite original tutorial sources unless explicitly asked.
- When generating Chinese Markdown or TXT in a Windows-oriented workflow, prefer UTF-8 with BOM if the surrounding project already uses it.
- Keep JSON UTF-8 without BOM for easier machine parsing.
- Preserve source links and extraction metadata so future agents can verify or refresh the library.

## Final Response Checklist

Tell the user:

- What source was processed.
- How many pages/files and unique articles/items were extracted.
- Which files were created.
- Whether any pages had low text or non-standard templates.
- Which master files or skills were updated.
- Which validations passed.
- Any remaining limitation.
