# Excellent Novel Case Library Analysis

Use this reference when the source is a folder of novels, EPUBs, classic works, benchmark web novels, or other finished fiction used as writing cases.

Case libraries are not tutorials. Treat them as evidence of how fiction works in practice: reader promises, structure, character pressure, suspense, motif control, emotional payoff, and style choices. The output should help future AI writers learn transferable craft patterns without copying prose, scenes, or plot specifics.

## Core Principle

Separate three layers:

1. **Inventory**: what works exist, with title, author, file type, language, size, and parsing status.
2. **Case analysis**: what craft mechanism each work demonstrates.
3. **Reusable writing operation**: how an AI writer should apply that mechanism in planning, drafting, revising, or polishing.

Never turn a case library into a raw-text mirror. For copyrighted works, store metadata, concise analysis, short non-verbatim summaries, and operational lessons only.

## Discovery Workflow

1. List files by type before reading content.
2. For EPUBs, parse package metadata with a structured parser when possible:
   - title
   - creator/author/translator
   - language
   - spine/order if needed
   - file size
   - parsing errors
3. Record a `case_status` field:
   - `metadata_only`
   - `parsed_text_sample`
   - `chapter_map_available`
   - `image_or_scan_heavy`
   - `metadata_error`
   - `unsupported_format`
4. Do not load full novels into the context window. Use targeted sampling only when needed:
   - opening pages/chapters for promise and hook analysis
   - turning-point chapters for conflict escalation
   - ending pages/chapters for payoff and thematic closure
   - repeated motifs or chapter structures when the user asks for style or structure analysis

## Analysis Axes

For each case, extract craft observations along these axes:

| Axis | What To Look For | AI-Writing Use |
|---|---|---|
| Opening promise | What kind of pleasure, danger, mystery, wound, or question is promised early | Design chapter 1 hooks and reader expectations |
| Protagonist pressure | What the protagonist wants, fears, lacks, hides, or misunderstands | Build durable motivation and inner conflict |
| Conflict system | Social, moral, survival, romantic, ideological, procedural, or cosmic pressure | Prevent episodic plots from feeling random |
| Escalation rhythm | How stakes, revelations, losses, reversals, and choices intensify | Plan long-serial pacing and chapter ends |
| Information control | What the reader knows, does not know, suspects, or misunderstands | Create suspense, mystery, irony, and reread value |
| Character web | How side characters mirror, tempt, oppose, or expose the protagonist | Give supporting cast structural purpose |
| Motifs and symbols | Repeated objects, phrases, settings, rituals, or images | Add thematic unity without exposition |
| Scene economy | How scenes combine plot movement, emotion, world detail, and character change | Revise scenes that only do one job |
| Style and voice | Sentence density, narration distance, humor, restraint, lyricism, or plainness | Match prose texture to genre and emotional intent |
| Ending logic | How the ending pays off premise, theme, plot, and character arc | Avoid arbitrary endings or flat resolutions |

## Case Type Map

Classify case works by the main craft value they offer. A single work can have multiple tags, but keep the primary tag clear.

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
social_morality
voice_style
long_serial_architecture
ending_payoff
```

## Example Corpus Pattern

When a folder contains a broad set of famous novels or benchmark fiction cases, summarize it by craft coverage rather than by plot. For example, a 10-work mixed corpus can be described as covering:

- **System pressure and ideological worldbuilding**: useful for stories where the world itself is the antagonist.
- **Allegorical compression**: useful for turning abstract power relations into concrete dramatic situations.
- **Large-scale speculative escalation**: useful for moving from personal stakes to civilizational stakes while preserving wonder.
- **Coming-of-age series architecture**: useful for long arcs, recurring cast management, school/team structures, and installment payoffs.
- **Trauma realism and moral discomfort**: useful for writing wounds, silence, shame, and social complicity with restraint.
- **Plainspoken fate tragedy**: useful for high emotional impact without ornate prose.
- **Mystery and information asymmetry**: useful for suspense, delayed revelation, dual timelines, and emotional reversal.
- **Mythic family or generational structure**: useful for time, repetition, inheritance, and motif-driven storytelling.
- **Detective case serial design**: useful for modular cases, clues, reasoning scenes, and recurring protagonist charisma.
- **Historical-romantic epic scale**: useful for combining personal desire with social upheaval, war, class, and survival.

This kind of summary is usually more useful to AI writers than a title-by-title book report.

## Output Fields For Case Records

Each case record should include:

```text
source_name
source_path_or_url
extraction_date
file_name
file_type
title
author_or_creator
translator_or_editor if available
language
file_size
case_status
primary_case_type
secondary_tags
craft_summary
transferable_lessons
best_used_for
risks_when_imitating
copyright_note
limitations
```

## Recommended Markdown Outputs

For a case library, produce:

```text
CaseLibrary/
├─ 00_Overview.md
├─ 01_Case_Index.md
├─ 02_Craft_Patterns.md
├─ 03_AI_Usage_Map.md
└─ case_index.json
```

The overview should answer:

- What kinds of fiction cases are present?
- Which writing problems can this case library help solve?
- Which cases are best for opening, structure, character, conflict, suspense, style, and ending?
- What should an AI avoid copying?
- What parsing limitations exist?

## AI Usage Map

Map cases to writing tasks:

| Writing Task | Use Case Library For | Avoid |
|---|---|---|
| Concept expansion | Find the pressure system and reader promise behind successful works | Copying premise shells |
| Outline design | Study escalation rhythm, reversals, and act/volume turns | Reusing exact plot order |
| Chapter drafting | Borrow scene functions: hook, pressure, revelation, reversal, payoff | Pastiche of prose voice |
| Character design | Analyze desire, wound, contradiction, and relationship mirrors | Flattening characters into traits |
| Suspense | Study delayed information, misdirection, and clue placement | Withholding information randomly |
| Revision | Check whether each scene moves plot, emotion, and theme together | Adding decorative literary analysis |
| De-AI polishing | Use prose-density and voice observations as diagnosis, not imitation | Mimicking distinctive copyrighted style |

## Quality Checks

Pass only when:

- All source files are counted.
- Metadata extraction successes and failures are known.
- No full novel text is stored.
- Case tags are craft-specific, not vague praise tags.
- Each case has at least one concrete AI-writing use.
- Imitation risks are explicit.
- The case library is integrated into master prompts or skills as a source type distinct from tutorials.

Failure signs:

- The output is mostly plot summary.
- Every work receives generic tags like `classic`, `good`, or `literary`.
- The analysis tells AI to "write like" a specific author without guardrails.
- The case library is mixed with tutorial articles without identifying it as a different source type.
