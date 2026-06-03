# Web Novel Tutorial Curation Skill

![Web Novel Tutorial Curation logo](assets/logo.png)

A reusable AI-agent skill for extracting, summarizing, classifying, validating, and integrating web-novel / fiction-writing tutorial materials into clean knowledge libraries.

This repository contains a portable `SKILL.md` package designed for AI agents that work with Chinese web-novel, online fiction, genre fiction, and long-form serial-writing resources. The workflow is also useful for any agent that must process tutorial websites, writing-course pages, local documents, or mixed source folders without copying raw copyrighted material.

## What This Skill Solves

AI agents often make avoidable mistakes when processing tutorial sources:

- scraping only visible page text while missing APIs or server-rendered data;
- assuming all article detail pages share one template;
- copying full tutorial bodies instead of producing reusable summaries;
- using broad keyword tags that classify almost every article incorrectly;
- updating master prompts or skills before validating counts and files;
- leaving project-specific details inside generic agent instructions;
- forgetting page ranges, filters, extraction dates, and limitations.

This skill turns those lessons into a repeatable workflow.

## Core Capabilities

- Discover whether tutorial data comes from HTML, rendered DOM, APIs, script state, documents, or mixed templates.
- Extract list pages before detail pages.
- Deduplicate by stable IDs or canonical URLs.
- Detect low-text, image-only, video-only, blocked, or changed-template pages.
- Summarize tutorials into writing principles, not copied articles.
- Build Markdown and JSON knowledge libraries.
- Classify materials by source category and writing task.
- Validate counts, JSON parsing, encodings, links, tags, and master-file integration.
- Update prompts, project guides, or existing skills only after validation.

## Repository Structure

```text
.
├─ README.md
├─ README.zh-CN.md
├─ LICENSE
├─ assets/
│  └─ logo.png
└─ web-novel-tutorial-curation/
   ├─ SKILL.md
   ├─ agents/
   │  └─ openai.yaml
   └─ references/
      ├─ extraction-workflow.md
      ├─ output-templates.md
      └─ quality-gates.md
```

The actual skill package is the `web-novel-tutorial-curation/` folder.

## When To Use

Use this skill when an AI agent is asked to:

- extract writing tutorials from a website;
- summarize fiction-writing courses into a reusable knowledge base;
- process the first N pages of a tutorial list;
- classify author interviews, platform lessons, or genre guides;
- build a local folder of Markdown and JSON summaries;
- update master AI prompts or existing writing skills with a new source;
- validate that extraction results are complete and not stale.

## Typical Output

The skill recommends producing at least:

```text
TutorialLibrary/
├─ 00_Overview.md
├─ 01_All_Items.md
├─ 02_Category_Summary.md
├─ 03_Theme_Index.md
└─ tutorial_index.json
```

Each item should preserve:

- title;
- source link;
- category or column;
- extraction date;
- page/rank/order when relevant;
- available counters;
- content status;
- tags;
- summary;
- usable experience;
- limitations.

## Copyright-Friendly Design

This skill is intentionally designed to avoid mirroring tutorial websites.

Recommended output stores:

- summaries;
- tags;
- source links;
- short headings when useful;
- operational writing advice.

It does not recommend storing full original article bodies by default.

## Installation

Copy the skill folder into your AI agent's skill directory:

```text
web-novel-tutorial-curation/
```

For Codex-style skills, the important file is:

```text
web-novel-tutorial-curation/SKILL.md
```

## Example Prompt

```text
Use $web-novel-tutorial-curation to extract the first 20 pages of this fiction-writing tutorial list, summarize all articles into Markdown and JSON, validate the counts, and update my master writing-agent prompt with the new source.
```

## Quality Gates

Before finalizing, the agent should verify:

- exact source URL, page range, filter, and extraction date;
- list count and duplicate handling;
- detail-page success count and low-text count;
- JSON parse success;
- Markdown readability;
- source links;
- tag quality;
- absence of full copyrighted article bodies;
- master-file updates;
- skill validation when a skill was edited.

See [quality-gates.md](web-novel-tutorial-curation/references/quality-gates.md) for the full checklist.

## Chinese README

中文版说明见 [README.zh-CN.md](README.zh-CN.md).

## License

MIT License.
