---
name: hydracept-sheet
description: Produce cohesive sprite, icon, glyph, and VFX families as one Sheet & Slice job over image.generate.v1, including rows, columns, animation frame order, and freshly sliced transparent PNG frames. Use when the user wants a consistent set of sprites or animation frames rather than unrelated single images.
license: Proprietary
---

# Hydracept Sheet

Cohesive sprite, icon, glyph, and VFX families via Sheet & Slice.

## Capability

Use `image.generate.v1` with sheet options — not a separate fictional capability.

## Sheet options

- `sheet.slice`: true when individual frames are needed
- `sheet.rows` and `sheet.columns` for contact-sheet layout
- `sheet.animation` when frame order matters
- `requestTransparentOutput: true` for game-ready PNG frames

## Workflow

1. Define the family: style, count, and intended in-game use
2. Submit one sheet job with consistent prompt and sheet metadata
3. Poll the job and download the sheet plus sliced frames when available
4. Prefer one cohesive sheet over many unrelated single-image jobs
5. Summarize artifact paths and receipt details for the team
