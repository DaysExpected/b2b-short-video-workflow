# B2B Short Video Workflow Skill

This folder is a standalone Agent Skill for a human-guided B2B English short-video workflow. It starts with source research and ends with structured storyboard, music-direction, and title outputs. It intentionally pauses for human decisions and does not edit, download, license, render, publish, or schedule videos.

## Quick Start

Give the Skill to an Agent and say:

> I want to make a B2B English short video about [topic].

To resume from the middle, say for example:

> Continue to Step 3 storyboard. Here is the approved polished script: [script].

The Skill is human-guided: it intentionally pauses at editorial checkpoints for source selection, script approval and polish, actual footage/music selection, and final-title choice. The Agent should preserve the state and ask only for a missing required human decision or input.

## Installation

### Codex

Install the Skill from the GitHub repository or Skill directory using the available Skill installer.

Example usage after installation:

> Use $b2b-short-video-workflow to make a B2B English short video about [topic].

If the Skill environment requires a restart or reload after installation, follow that environment's normal Skill-loading process.

### ChatGPT

Where custom Skill upload is supported:

1. Download the Skill package from GitHub.
2. Upload the complete Skill package through the Skills interface.
3. Start with:

> I want to make a B2B English short video about [topic].

### Compatible Agent Environments

For Agent environments that support the Agent Skills directory format, install or copy the complete `b2b-short-video-workflow/` directory without removing its:

- `SKILL.md`
- `references/`
- `agents/`
- `examples/`
- `LICENSE`
- `README.md`

Do not claim universal compatibility with every AI product.

## Contents

- `SKILL.md` — state machine, routing rules, stage contracts, and boundaries.
- `references/` — detailed stage prompts, output formats, and checkpoint rules.
- `examples/micromanagement-example.md` — compact end-to-end routing example.
- `agents/openai.yaml` — UI metadata for Skill discovery.
