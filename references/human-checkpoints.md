# Human Checkpoints and State Handling

## Non-negotiable gates

| Gate | Required human action | Agent must not do |
|---|---|---|
| Source | Select ONE article | select the final article |
| Script | Select ONE angle and polish/approve the final script | treat a draft as final |
| Footage | Choose actual footage and verify usage rights | choose or download footage |
| Editing | Assemble and revise the video | edit, render, or export |
| Music | Choose the actual track and resolve vocals/licensing | choose the final track |
| Title | Select ONE final title | publish or pick the final title |

## Pause protocol

When a gate is reached:

1. label the state `waiting for human choice`;
2. show the options needed for the decision;
3. ask for one concrete reply;
4. stop. Do not produce downstream stages in the same response.

## Resume protocol

Accept natural commands such as:

- “Article 2 is approved; continue to scripts.”
- “Use angle 1. I polished the script below; continue to storyboard.”
- “Continue to Step 3 storyboard.”
- “Regenerate titles from the approved script.”

Before resuming, verify the corresponding artefact exists. If it does not, ask for it rather than recreating it silently.

## Revision protocol

If the human rejects an output, keep the state at the same stage, summarize the requested change, and regenerate only that stage. If the approved source changes, mark script/storyboard/music/title outputs stale and require regeneration. If the approved polished script changes, mark storyboard/music/title outputs stale and require regeneration. Preserve the earlier approved artefact as a prior version rather than silently overwriting it.

## Handoff checklist

After the human selects the final title, or explicitly requests a handoff package, produce the Stage 6 `FINAL CREATOR HANDOFF PACKAGE` from the latest approved artefacts only. Before declaring the workflow complete, show:

- approved article;
- approved polished script;
- storyboard/search brief;
- music direction and human selection reminder;
- selected final title, if supplied;
- explicit list of work still owned by the human: voice-over, footage, licensing, editing, final music, subtitles and subtitle QC, final audio/video QC, export, publication.
