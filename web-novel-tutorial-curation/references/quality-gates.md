# Quality Gates

Use these gates before telling the user the task is complete.

## Gate 1: Source Scope

Pass when:

- Exact source URL/folder is recorded.
- Page range, filters, categories, or file selection are recorded.
- Extraction date is recorded.
- Item count is known.

Failure signs:

- "I extracted the site" without page range or filter.
- No count per category/page.
- No distinction between list pages and detail pages.

## Gate 2: List Integrity

Pass when:

- Parsed count matches expected page/file count.
- Duplicates are detected and handled.
- First, middle, and last samples look correct.
- Links are absolute or canonical.

Failure signs:

- The same article appears multiple times.
- Link text from navigation is mistaken for article title.
- Category or column text includes sidebar descriptions.

Fix:

- Parse from item containers, not all links.
- Deduplicate by article id or canonical URL.
- Sample multiple pages, not only page 1.

## Gate 3: Detail Integrity

Pass when:

- Detail fetch success/failure count is known.
- Non-standard templates are classified.
- Low-text items are marked instead of silently dropped.
- Text extraction does not include footers, related articles, nav bars, or scripts.

Failure signs:

- Many items have identical boilerplate text.
- A detail page body includes "recommended articles" or footer text.
- Old pages return a different template and are counted as failures.

Fix:

- Locate content start/end markers.
- Use source-specific fallback to list descriptions.
- Add `content_status`.

## Gate 4: Copyright And Ethics

Pass when:

- Output stores summaries and source links.
- Full original bodies are not copied by default.
- Long examples are paraphrased into principles.
- Any quoted text is short and necessary.
- Finished-fiction case libraries store metadata, craft analysis, and transferable lessons instead of full chapters, scenes, or distinctive prose imitation.

Failure signs:

- Local output is a full mirror of the tutorial site.
- Summaries reproduce entire paragraphs.
- README advertises copied course content rather than a curated index.
- Case-library notes become plot retellings or "write like this author" instructions without imitation guardrails.

Fix:

- Remove raw bodies.
- Keep headings and brief excerpts only when essential.
- Convert source lessons into checklists and usable experience.

## Gate 5: Tag And Summary Quality

Pass when:

- Tags are specific enough to guide AI use.
- Summaries mention the writing problem and application stage.
- Several samples from different pages/categories make sense.
- For excellent-novel cases, each record identifies craft value, best-used-for writing tasks, and risks when imitating.

Failure signs:

- One broad tag appears on almost every item.
- Tags are triggered by boilerplate words.
- Summaries are generic and interchangeable.
- Every case gets vague praise tags such as `classic`, `famous`, or `good_story` without operational craft use.

Fix:

- Score title and category higher than body text.
- Remove over-broad keywords.
- Require stronger evidence for platform-wide tags.
- Regenerate and re-sample.

## Gate 6: File Integrity

Pass when:

- All expected files exist.
- Markdown files open correctly.
- JSON parses successfully.
- File sizes are plausible.
- Chinese Windows-oriented Markdown/TXT uses the project's expected encoding.

Failure signs:

- Mojibake in terminal or README.
- JSON starts with BOM and fails strict parsers.
- Markdown table breaks because of unescaped pipes.

Fix:

- Escape table pipes.
- Use UTF-8 with BOM for Chinese MD/TXT when the project expects it.
- Use UTF-8 without BOM for JSON.
- Parse JSON in a script before finalizing.

## Gate 7: Master Integration

Pass when:

- Source registry is updated.
- Prompt files mention the new source.
- Skills or agent instructions mention when to use it.
- Case libraries are identified as a distinct source type from tutorials.
- Generic files contain no project-specific leftovers.
- Old typos and stale paths found during the update are fixed.

Failure signs:

- Extracted library exists but master AI prompts do not know about it.
- Generic prompt still contains a specific project premise.
- Skill documentation mentions outdated counts or paths.

Fix:

- Search all managed files for the new source name.
- Search for stale project names or placeholders.
- Validate skills after edits.

## Gate 8: Repository Publishing

Pass when:

- Local git status is clean after commit.
- README explains purpose, installation, structure, and usage.
- A localized README exists when required.
- Logo/assets render with relative paths.
- GitHub repository is public if requested.
- Topics and description are set.

Failure signs:

- README links to local absolute paths.
- Asset missing from repository.
- Repo is private when the user requested public.
- Topics are absent or too generic.

Fix:

- Use relative repository paths.
- Verify with `gh repo view`.
- Check README rendering assumptions before final response.

## Final Sanity Script Ideas

Use code to check:

- File existence.
- JSON parse and item count.
- Markdown BOM policy.
- Source-name presence in master docs.
- Skill validator result.
- Git status.
- GitHub visibility and topics.
