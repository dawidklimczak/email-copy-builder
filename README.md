# Email Copy Builder

An internal Streamlit app that turns reusable content "blocks" into ready-to-use marketing copy via OpenAI, instead of writing every prompt from scratch.

## Problem

Marketing copy for campaigns is usually briefed the same way every time — a product description, a communication goal, a format/length spec, and a tone of voice — but that brief is rarely reused systematically, so every campaign starts from a blank prompt. This tool turns those four ingredients into standalone, reusable building blocks that can be mixed and matched to generate copy for new campaigns quickly and consistently.

## Solution & Architecture

- **Streamlit** multi-page app with a dedicated "library" section for managing content blocks
- **SQLAlchemy + SQLite** persistence for the block library and its relationships
- **OpenAI API** for generation, taking an uploaded context file (plain text, optionally supplemented with a PDF) plus a selected combination of blocks
- **pypdf** for extracting text from supporting PDF materials before they're fed into the prompt

## Key Product Decisions

- **Composable prompt blocks**: copy briefs are decomposed into four independent categories — Product Bible (what it's about), Task (the business goal and persuasion strategy), Structure (format/length/required sections), and Language (tone and style rules) — so a single well-crafted block can be reused across many campaigns instead of being rewritten each time.
- **Dependency validation**: blocks can't be deleted while still referenced by a saved "set", preventing generation configs from silently breaking.
- **Group-based organization**: sets of blocks are grouped by campaign, so a batch of related copy variants can be generated and reviewed together.
- **Migration path acknowledged explicitly**: the README documents how to migrate data from an earlier NiceGUI-based prototype, showing this was a deliberate rebuild rather than a one-off script.

## Outcome

Replaced ad-hoc, one-off prompt writing with a small internal content-ops system: a growing, reusable library of proven briefing components that can be recombined to produce campaign copy on demand, exportable as Markdown.

## Preview

<!-- screenshot placeholder — added separately -->

## Note

Source code is kept in a private repository; happy to share on request.
