---
name: b2b-short-video-workflow
description: Run a stateful, human-in-the-loop workflow for producing B2B English short-video packages. Use when a creator asks to research a topic, select and verify a source article, develop multiple 45–60 second English script angles, create a storyboard and stock-footage search terms, define a music direction, or generate title options. Pause at required human checkpoints and resume from a named step; never replace editorial approval, footage selection, editing, final music selection, or publishing.
---

# B2B Short Video Workflow

Use this skill as a workflow coordinator, not as an autonomous video producer. Maintain an explicit state, produce only the current stage's deliverable, and stop at every required human gate.

## Start or resume

At the beginning, identify the requested topic, audience, business direction, language, and current stage. For a first invocation with no active state, or when the creator asks what the Skill can do or how the workflow works, read `references/user-onboarding.md` and give its concise explanation once. Do not repeat it during an existing workflow.

If the creator says only “I want to make a video about X,” initialize:

```text
workflow: b2b-short-video
stage: 1_source_research
status: ready
topic: X
```

If the creator says “continue to Step 3 storyboard” and supplies the approved polished script, resume immediately without forcing onboarding. Do not redo earlier stages. Confirm the minimum required inputs for that stage, set the state, and continue. If a required human decision is missing, stop and request exactly that decision.

## State machine

```text
1_source_research
  -> WAIT: human selects ONE verified article
2_script_development
  -> WAIT: human selects ONE angle and supplies/approves polished script
3_storyboard
  -> deliver storyboard + search keywords
4_music_direction
  -> deliver one music direction + search terms
5_title_options
  -> WAIT: human selects ONE final title
6_handoff_complete
```

The workflow may move backwards only when the creator explicitly asks for revision. Record the reason and preserve the previous approved version. Do not silently advance through a WAIT state.

## Workflow state schema

Maintain this state across turns. Do not print every field unless it helps the creator; always print the compact status line defined below.

```yaml
workflow: b2b-short-video
project:
  topic:
  audience:
  content_direction:
  keywords:
  target_length: 45–60 seconds
  language: English
source:
  candidate_sources:
  selected_article:
  selected_article_url:
  selected_article_verified:
  selected_article_access_status:
  approved_by_human:
script:
  generated_versions:
  selected_version:
  approved_polished_script:
  approved_by_human:
storyboard:
  status:
  based_on_script_version:
music:
  status:
  direction:
title:
  status:
  candidates:
  selected_final_title:
workflow_state:
  current_stage:
  status:
  next_human_action:
  stale_downstream_outputs:
```

Never use an older script after a newer approved polished script is supplied. If the approved source changes, mark script, storyboard, music, and title outputs stale. If the approved polished script changes, mark storyboard, music, and title outputs stale. Preserve previous approved versions when revising rather than silently overwriting them. Never move through a human WAIT checkpoint without explicit approval.

## Routing rules

1. Read the relevant reference file before executing that stage:
   - Research: `references/source-research.md`
   - Scripts: `references/script-generation.md`
   - Storyboard: `references/storyboard.md`
   - Music: `references/music-selection.md`
   - Titles: `references/title-generation.md`
   - Gates and state handling: `references/human-checkpoints.md`
   - First-use / capability explanation: `references/user-onboarding.md`
2. Keep outputs in the requested language format: the creative artefacts are English; explanations and status can be in the creator's language.
3. Present structured, copyable results. Keep assumptions and unsupported claims visibly marked.
4. Use web research only for the research stage and cite each candidate source with title, publisher, date, URL, and a short reason it is relevant. Do not treat search snippets as verified evidence.
5. Do not download, select, license, edit, mix, render, export, publish, or schedule a video. The Skill supplies decisions and handoff material for a human creator.

## Stage contracts

### Step 1 — Source Research

Collect the creator's topic/direction/keywords and audience if available. Search and validate multiple candidate articles, then recommend a shortlist. End with:

```text
HUMAN CHECKPOINT — Select ONE article.
Reply with: Article [number], or provide another source.
```

Do not draft the final script before one article is selected.

### Step 2 — Script Development

Use the selected complete article, not a snippet. Extract its central claim, tension, counter-intuitive point, evidence boundary, and a single video takeaway. Create three materially different angles and a 45–60 second English script for each. End with:

```text
HUMAN CHECKPOINT — Select ONE angle and polish it.
Reply with: Angle [number] plus any edits, or paste the approved polished script.
```

Do not storyboard an unapproved script.

### Step 3 — Storyboard

Use only the final polished script. Break it into 7–11 visual beats. For every beat provide three Chinese visual references and six search-keyword combinations (English + Chinese), oriented to Pexels, Videezy, Mixkit, and Vidsplay. This is a search brief, not footage selection.

### Step 4 — Music Direction

Use the final script and its emotional arc to define one unified background-music direction plus about five bilingual search-keyword groups. Default to instrumental music. Flag search directions likely to return vocal tracks; prefer instrumental versions or require the human to remove/separate vocals.

### Step 5 — Title Options

Generate three different English titles based on the final script: one curiosity/CTR-led, one content-match-led, and one professional insight-led. Score each for Expected CTR, Content Match, and Overall Score, explain the scores briefly, and end with a final-title checkpoint.

### Step 6 — Final Creator Handoff

After the human selects the final title, or explicitly requests a handoff package, create `FINAL CREATOR HANDOFF PACKAGE` using the latest approved artefacts only. Include:

1. `SELECTED SOURCE` — article title, author/publication, URL, and relevant source note.
2. `FINAL APPROVED SCRIPT` — the exact human-approved polished script.
3. `STORYBOARD` — the final AI storyboard based on that approved script.
4. `STOCK FOOTAGE SEARCH TERMS` — preserve the storyboard search keywords.
5. `MUSIC DIRECTION` — one unified direction, bilingual search keywords, and vocal warning if applicable.
6. `TITLE OPTIONS` — all three candidates and scores.
7. `FINAL SELECTED TITLE` — human-selected title, or `HUMAN DECISION REQUIRED`.
8. `HUMAN-OWNED WORK REMAINING` — generate/select voice-over; search and select actual footage; verify licensing/usage rights; perform editing; choose the actual music track; generate subtitles and perform subtitle QC; conduct final audio/video QC; export; publish.

Do not imply that any human-owned work was completed by the Agent.

## Required final response shape

Every stage response begins with a compact state line:

```text
WORKFLOW: B2B Short Video
STAGE: [number and name]
STATUS: [in progress | waiting for human choice | ready to continue | complete]
NEXT HUMAN ACTION: [one concrete action]
```

Then provide only the current stage's output, followed by the checkpoint or next-step instruction. Preserve approved source, script, storyboard, music direction, and title as separate labelled artefacts so the creator can copy them into an AI tool or editing workflow.

## Boundaries

The Skill must not:

- make the final editorial decision or approve an article;
- replace human script polishing;
- choose or download actual stock footage;
- perform video editing, voice recording, audio mixing, or export;
- choose the final music track;
- choose the final title;
- publish or schedule a video.

Use the references for detailed prompt logic and output formats. Use `examples/micromanagement-example.md` only as a compact demonstration of state transitions and should-not-continue gates.
---
