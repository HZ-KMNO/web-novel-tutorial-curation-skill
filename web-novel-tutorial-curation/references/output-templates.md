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
