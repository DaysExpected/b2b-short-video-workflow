# Example: Micromanagement

This is a compact routing example, not a completed production package.

## Start

Creator: “I want to make a B2B English short video about micromanagement.”

Agent state:

```text
STAGE: 1_source_research
STATUS: in progress
```

The agent asks for audience/direction if needed, researches and verifies candidate articles, then stops:

```text
HUMAN CHECKPOINT — Select ONE article.
```

## After source approval

Creator: “Use Article 2. Continue to scripts.”

The agent reads the selected article, writes three distinct 45–60 second English angles, and stops:

```text
STAGE: 2_script_development
STATUS: waiting for human choice
HUMAN CHECKPOINT — Select ONE angle and polish it.
```

It must not produce a storyboard yet.

## After final script

Creator: “Use Angle 1. Here is my polished final script: [text]. Continue to Step 3 storyboard.”

The agent creates 7–11 beats with three Chinese visual references and six bilingual search-keyword groups per beat, then hands off the actual footage search and selection to the creator. Music direction and titles can follow only from this final script, each with its own human selection reminder.
