# Output Templates

These templates keep tutorial libraries consistent across sources.

## Folder Layout

Use localized names when appropriate, but keep the structure predictable:

```text
TutorialLibrary/
├─ 00_Overview.md
├─ 01_All_Items.md
├─ 02_Category_Summary.md
├─ 03_Theme_Index.md
└─ tutorial_index.json
```

For Chinese projects, localized equivalents are fine:

```text
教程库/
├─ 00_总览与使用说明.md
├─ 01_全部文章.md
├─ 02_栏目分类总结.md
├─ 03_主题索引.md
└─ 教程_文章索引.json
```

## Overview Markdown

Include:

```markdown
# Source Name Tutorial Summary

Source: [source label](source_url)
Extraction date:
Scope:
Item count:
Content status counts:

## Files
- ...

## Main Conclusions
- ...

## AI Usage Order
1. ...

## Limitations
- ...
```

## Full Item Index Markdown

Use a table when items are numerous.

Recommended columns:

```markdown
| Rank | Page/File | Category | Date | Title | Stats | Tags | Summary | Usable Experience | Source |
|---:|---|---|---|---|---|---|---|---|---|
```

Rules:

- Escape `|` in text.
- Keep summaries concise.
- Use source links instead of copying source bodies.
- Include content status if some pages are non-standard.

## Category Summary Markdown

Include:

```markdown
# Category Summary

## Category Overview
| Category | Count | Main Use | Representative Items |

## Category Details
### Category A
- Item 1
- Item 2
```

This helps an AI choose based on source taxonomy.

## Theme Index Markdown

Include:

```markdown
# Theme Index

## Theme Overview
| Theme | Count | Best Used For |

## Theme Details
### Opening Hooks
- ...
```

This helps an AI choose based on writing task.

## JSON Index

Recommended schema:

```json
{
  "source_name": "string",
  "source_url": "string",
  "extraction_date": "YYYY-MM-DD",
  "scope": "string",
  "item_count": 0,
  "content_status_counts": {},
  "categories": {},
  "themes": {},
  "items": [
    {
      "id": "string",
      "rank": 1,
      "page": 1,
      "category": "string",
      "title": "string",
      "date": "string",
      "stats": {},
      "link": "string",
      "content_status": "standard_text",
      "text_length": 0,
      "headings": [],
      "tags": [],
      "summary": "string",
      "usable_experience": "string",
      "limitations": "string"
    }
  ]
}
```

Keep JSON machine-readable:

- UTF-8 without BOM.
- No comments.
- Stable field names.
- No full copyrighted body text unless explicitly allowed.

## Case Library Layout

Use this structure when the source is a folder of novels, EPUB fiction, benchmark works, or excellent-fiction examples:

```text
CaseLibrary/
├─ 00_Overview.md
├─ 01_Case_Index.md
├─ 02_Craft_Patterns.md
├─ 03_AI_Usage_Map.md
└─ case_index.json
```

Recommended case-index columns:

```markdown
| # | File | Title | Author/Creator | Type | Language | Status | Primary Craft Value | Best Used For | Imitation Risk |
|---:|---|---|---|---|---|---|---|---|---|
```

Recommended JSON fields:

```json
{
  "source_name": "string",
  "source_path_or_url": "string",
  "extraction_date": "YYYY-MM-DD",
  "scope": "string",
  "case_count": 0,
  "case_status_counts": {},
  "craft_patterns": {},
  "cases": [
    {
      "id": "string",
      "file_name": "string",
      "file_type": "epub",
      "title": "string",
      "author_or_creator": "string",
      "translator_or_editor": "string",
      "language": "string",
      "file_size": 0,
      "case_status": "metadata_only",
      "primary_case_type": "string",
      "secondary_tags": [],
      "craft_summary": "string",
      "transferable_lessons": [],
      "best_used_for": [],
      "risks_when_imitating": [],
      "copyright_note": "string",
      "limitations": "string"
    }
  ]
}
```

Case-library outputs should emphasize reusable craft mechanisms, not plot retellings or style imitation.

## Master File Update Snippet

When updating a project guide or agent prompt, add a compact source entry:

```text
Source name:
Path:
Extraction date:
Scope:
Counts:
Files:
Best used for:
Limitations:
Relationship to other sources:
Source type: tutorial library, platform article library, excellent-novel case library, or mixed source.
```

Example use-case language:

```text
Use this source for signing/submission, title/synopsis packaging, platform rules, data review, and long-form commercial judgment.
```

## Final User Report

Use this structure:

```text
Processed source:
Extracted:
Created files:
Updated master files:
Validation:
Limitations:
```
