# Documentation Prompt for Web Projects with AI

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
├── Repo-Hygiene-Check.md              # point-in-time repo hygiene audit
├── Ask-Other-Agent-to-Review.md       # prompt for an independent second-opinion review
├── LICENSE
├── .claude/
│   └── skills/
│       ├── documentthisweb/SKILL.md    # web/web app/website standard
│       ├── documentthisMacOS/SKILL.md  # native macOS standard
│       ├── documentthisWindows/SKILL.md # native Windows standard
│       └── documentthis/SKILL.md       # deprecated — redirects to documentthisweb
└── templates/
    └── DOCUMENTATION-PROMPT.md         # the reusable prompt (full + short versions)
```

## How to use it

### Claude Code / Cowork: use it as a skill, no copy-paste needed

This repo ships the standard as three ready-to-use Claude Code skills, one
per platform:

- [`.claude/skills/documentthisweb/SKILL.md`](.claude/skills/documentthisweb/SKILL.md) → `/documentthisweb`
- [`.claude/skills/documentthisMacOS/SKILL.md`](.claude/skills/documentthisMacOS/SKILL.md) → `/documentthisMacOS`
- [`.claude/skills/documentthisWindows/SKILL.md`](.claude/skills/documentthisWindows/SKILL.md) → `/documentthisWindows`

There's nothing to download or unzip — Claude Code loads project skills
automatically from those paths. (`.claude/skills/documentthis/` still
exists but only as a deprecated stub pointing to `/documentthisweb`.)

1. Clone this repo (or add it as a subfolder/submodule of the project you
   want documented, or copy just the relevant skill folder(s) into that
   project's own `.claude/skills/`).
2. Open Claude Code in that project.
3. Run the matching command for the project's platform —
   `/documentthisweb`, `/documentthisMacOS`, or `/documentthisWindows`.
   Claude will ask for any project details it can't infer, then follow the
   full standard: inspect the source, show you a preview, wait for your
   approval, then produce documented source files, an expanded
   `README.md`, companion docs (style guide, changelog, components,
   security checklist, dashboard, repo hygiene check, second-opinion
   review prompt), and validation results.

### Any other assistant (ChatGPT, Codex, Gemini, etc.)

1. Open [`templates/DOCUMENTATION-PROMPT.md`](templates/DOCUMENTATION-PROMPT.md).
2. Copy the **Prompt** section into the assistant.
3. Replace the bracketed project details (name, domain, purpose,
   technology, hosting target, audience, distribution plans).

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
- [`Repo-Hygiene-Check.md`](Repo-Hygiene-Check.md) — point-in-time repo
  hygiene audit.
- [`Ask-Other-Agent-to-Review.md`](Ask-Other-Agent-to-Review.md) — prompt
  for an independent second-opinion review from a different AI agent.

Every web project documented with this standard gets its own copies of
these seven files, scoped to that project's real source.

## Notes

- Never let the prompt or its output store secrets, credentials, private
  keys, personal contact data, sensitive server information, or IP
  addresses.
- Adapt the bracketed fields per project; the rest of the prompt is meant
  to stay stable across projects.
