# Style Guide

This repo is a markdown prompt/template toolkit — it has no rendered UI,
CSS, or visual assets of its own. So unlike a real web project's style
guide, most visual categories below are marked not applicable. The section
shape follows the standard's `STYLEGUIDE.md` template (see
[`templates/DOCUMENTATION-PROMPT.md`](templates/DOCUMENTATION-PROMPT.md)),
calibrated against two real examples: [360dna.com/style-guide](https://360dna.com/style-guide/)
and [ecards.magnolia365.com](https://ecards.magnolia365.com/?pg=3).

## Principles

- Documentation is a standing requirement, not an afterthought.
- Match reality exactly — never invent components, paths, or features.
- Each companion file stays in its own lane and cross-references instead of
  duplicating content.

## Voice & tone

- Second person, imperative mood, addressed to the AI assistant carrying
  out the prompt ("Inspect...", "Create...", "Do not...").
- Precise and directive rather than conversational — the prompt is itself
  an instruction set.
- Bracketed placeholders like `[PROJECT NAME]` mark fields the human
  operator fills in per project.

## Structure conventions

- ALL-CAPS filenames for standing deliverable docs: `README.md`,
  `STYLEGUIDE.md`, `CHANGELOG.md`, `COMPONENTS.md`, `SECURITYCHECK.md`.
- `###`-level headings mark one discrete requirement category; `##` marks a
  major phase (`Prompt`, `Short version`).
- Blockquote (`>`) is reserved for the persistent-memory preference
  statement and the short-version summary — nowhere else.
- Numbered lists for sequential/required steps (approval gate, validation);
  bullet lists for unordered requirement sets.

## Color / Typography / Imagery

Not applicable — no rendered UI or visual assets exist in this repo.

## Components

See [`COMPONENTS.md`](COMPONENTS.md) for the toolkit's reusable pieces (the
full prompt, the short-form re-prompt, and the `documentthis` skill
wrapper) and how they relate.

## Theme switching

Not applicable.

## Accessibility

Not applicable to this repo directly — accessibility documentation is
something this prompt requires of *other* projects (see "Accessibility
documentation requirements" in `templates/DOCUMENTATION-PROMPT.md`).
