# Documentation Prompt for AI

A reusable toolkit for applying a documentation-first standard to web
projects (HTML/CSS/JS, frameworks, or CMS sites) with any AI coding
assistant.

## What this is

This project is not a web project itself — it's a template you reuse
*against* other web projects. It captures a standing preference:

> Web projects should include clearly organized native source comments, a
> complete README, an exact asset-directory map, customization
> instructions, accessibility notes, testing guidance, and future
> theme-distribution guidance.

## Structure

```
.
├── README.md                          # this file
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
   an expanded README, and a validation pass — packaged as a ZIP.

Once an assistant already has the full standard in context (e.g. later in
the same conversation), use the **Short version** at the bottom of the
same file instead of re-pasting the whole prompt.

## Claude Code shortcut

If you're using Claude Code, the same standard is also available as the
`documentthis` skill — invoke `/documentthis` (or ask to "document this
project") inside any web project's directory instead of copy-pasting the
prompt.

## Notes

- Never let the prompt or its output store secrets, credentials, private
  keys, personal contact data, or sensitive server information.
- Adapt the bracketed fields per project; the rest of the prompt is meant
  to stay stable across projects.
