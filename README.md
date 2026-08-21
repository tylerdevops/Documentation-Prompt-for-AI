# Documentation Prompt for AI

A reusable toolkit for applying a documentation-first standard to web
projects (HTML/CSS/JS, frameworks, or CMS sites) with any AI coding
assistant.

## What this is

This project is not a web project itself — it's a template you reuse
*against* other web projects. It captures a standing preference:

> Web projects should include clearly organized native source comments, a
> complete README, a style guide, a changelog, a components guide, a
> security checklist, a documentation dashboard, an exact asset-directory
> map, customization instructions, accessibility notes, testing guidance,
> cache-busted stylesheet/script references, and future theme-distribution
> guidance.

## Structure

```
.
├── README.md                          # this file
├── DASHBOARD.md                       # documentation hub/index for this repo
├── STYLEGUIDE.md                      # writing/structure conventions used in this toolkit
├── CHANGELOG.md                       # dated history of this repo
├── COMPONENTS.md                      # the toolkit's reusable pieces
├── SECURITYCHECK.md                   # security/privacy checklist for this repo
└── templates/
    └── DOCUMENTATION-PROMPT.md         # the reusable prompt (full + short versions)
```

## How to use it

1. Open [`templates/DOCUMENTATION-PROMPT.md`](templates/DOCUMENTATION-PROMPT.md).
2. Copy the **Prompt** section into ChatGPT, Codex, Claude, Gemini, or
   another coding assistant.
3. Replace the bracketed project details (name, domain, purpose,
   technology, hosting target, audience, distribution plans).
4. The assistant will inspect the target project, show a documentation
   preview, wait for your approval, then produce documented source files,
   an expanded README, companion docs (style guide, changelog, components,
   security checklist, dashboard), and a validation pass — packaged as a
   ZIP.

Once an assistant already has the full standard in context (e.g. later in
the same conversation), use the **Short version** at the bottom of the
same file instead of re-pasting the whole prompt.

## Companion documentation

- [`DASHBOARD.md`](DASHBOARD.md) — documentation hub/index for this repo.
- [`STYLEGUIDE.md`](STYLEGUIDE.md) — conventions this toolkit itself
  follows.
- [`CHANGELOG.md`](CHANGELOG.md) — dated history of this repo.
- [`COMPONENTS.md`](COMPONENTS.md) — the toolkit's reusable pieces.
- [`SECURITYCHECK.md`](SECURITYCHECK.md) — security/privacy checklist for
  this repo.

Every web project documented with this standard gets its own copies of
these five files, scoped to that project's real source.

## Claude Code shortcut

If you're using Claude Code, the same standard is also available as the
`documentthis` skill — invoke `/documentthis` (or ask to "document this
project") inside any web project's directory instead of copy-pasting the
prompt.

## Notes

- Never let the prompt or its output store secrets, credentials, private
  keys, personal contact data, or sensitive server information, IP Address, root@
- Adapt the bracketed fields per project; the rest of the prompt is meant
  to stay stable across projects.
