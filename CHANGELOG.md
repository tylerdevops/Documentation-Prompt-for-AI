# Changelog

All notable changes to this repo are documented here, newest first.

## 2026-08-21

- Added `STYLEGUIDE.md`, `CHANGELOG.md`, `COMPONENTS.md`, `SECURITYCHECK.md`,
  and `DASHBOARD.md` as standing companion deliverables.
- Updated `templates/DOCUMENTATION-PROMPT.md` to require all five companion
  files above for every project the prompt is applied to, and to require
  cache-busted stylesheet/script references (e.g. `style.css?=v01`) as the
  one standing exception to the behavior-preservation rule.
- Expanded the `STYLEGUIDE.md` template section into a full Principles /
  Color / Typography / Imagery / Components / Voice / Theme-switching /
  Accessibility structure, calibrated against 360dna.com and
  ecards.magnolia365.com.
- Converted `COMPONENTS.md` to a Component/Purpose/Location/Depends-on
  table format, calibrated against build.ty1er.com/components.
- Added the `DASHBOARD.md` template section (header, doc navigation, quick
  links), calibrated against build.ty1er.com/dashboard.
- Added `.gitignore` for macOS `.DS_Store` files.
- Merged this session's local restructuring with the pre-existing GitHub
  history for this repo (LICENSE, `.claude/skills/documentthis/SKILL.md`,
  earlier README revisions), renamed the local branch to `main` to match,
  and pushed.
- Added `Repo-Hygiene-Check.md` as a sixth standing companion deliverable,
  with a first real audit pass against this repo (3 open items: a
  truncated fragment in README.md, this file's own naming-convention
  deviation, and ZIP-archive drift between the prompt template and the
  packaged skill).
- Added `Ask-Other-Agent-to-Review.md` as a seventh standing companion
  deliverable — a copy-paste prompt for an independent second-opinion
  review from a different AI agent (Codex, a fresh Claude Code session, or
  Google Antigravity with Gemini/Grok). Documented that this session has
  no connector to run it end-to-end itself.
- Updated `STYLEGUIDE.md`'s filename convention to document two
  intentional variants (ALL-CAPS for single/compound-word names,
  Title-Case-hyphenated for multi-word ones), resolving the naming-
  convention item flagged in `Repo-Hygiene-Check.md`.
- Removed the truncated `root@`/"IP Address" fragment from `README.md`'s
  Notes section, on request.
- Dropped every mention of a downloadable ZIP-archive deliverable/
  validation step from `templates/DOCUMENTATION-PROMPT.md` and this
  repo's `.claude/skills/documentthis/SKILL.md`, on request. Updated
  `SECURITYCHECK.md` and `Repo-Hygiene-Check.md` to reflect both fixes.
- Removed the old ZIP mention from the global `~/.claude/skills/documentthis/SKILL.md`
  copy (outside this repo) as well, on request.
- Removed remaining personal-name references ("Tyler"/"Tyler's") from this
  repo's documentation, generalizing to "your team"/second person. Left
  the `LICENSE` copyright holder and the git author identity unchanged,
  since those are attribution/legal fields rather than prose — flagged
  rather than silently changed.
- Split the single `documentthis` skill into three platform-specific
  skills for easier long-term maintenance: `documentthisweb`,
  `documentthisMacOS`, and `documentthisWindows`, each carrying the full
  standard (source-comment conventions, README structure, the seven
  companion docs, a platform-specific standing check, a third-party
  dependency license audit, and distribution guidance) adapted to its
  platform. The old `documentthis` skill is now a deprecated stub
  redirecting to `/documentthisweb`. Mirrored all of this to
  `~/.claude/skills/` so the new slash commands work outside this repo.
- Confirmed on request: `LICENSE`'s copyright holder stays "Tyler" —
  updated `Repo-Hygiene-Check.md` from "needs review" to "resolved,
  intentional".
- Expanded the `Repo-Hygiene-Check.md` scope in `templates/DOCUMENTATION-
  PROMPT.md` and all three platform skills into ten system-design-
  engineer-level categories (version control, documentation/architecture
  currency, dependency/supply-chain, build/CI/CD, infrastructure, API
  contracts, observability, security posture, reliability/scalability,
  repo structure/ownership) instead of the original doc-hygiene-only
  scope. Re-ran this repo's own `Repo-Hygiene-Check.md` under the new
  scope, marking six categories N/A (with reasons) since this repo has no
  code, build, CI/CD, deployed infrastructure, or APIs of its own.
  Mirrored the expanded skills to `~/.claude/skills/`.
- Added Bash and Perl to `documentthisMacOS`'s source-comment requirements
  and build-process README section, covering macOS automation/build-phase
  scripts, on request.
- Added PowerShell (with comment-based help) and batch/terminal scripts to
  `documentthisWindows`'s source-comment requirements and build-process
  README section, on request.
- Re-verified no live requirement text anywhere (templates, all skill
  files, repo and global copies) mentions a ZIP-archive deliverable; only
  historical changelog/audit entries describing the past removal still
  say "ZIP", kept intentionally as the historical record.
- Expanded the `SECURITYCHECK.md` scope in `templates/DOCUMENTATION-
  PROMPT.md` and all three platform skills into ten categories scoped the
  way a top-level security lead would scope it (threat modeling & data
  classification, auth & access control, data protection, secrets &
  credentials, supply chain & build integrity, secure development
  lifecycle, logging/monitoring/incident response, compliance &
  standards, network/infrastructure hardening, adversarial testing) —
  instead of the original forms-and-cookies-only scope. Re-ran this
  repo's own `SECURITYCHECK.md` under the new scope: all ten categories
  N/A or "not assessed" with stated reasons, since this repo has no
  application code, accounts, network calls, or deployed infrastructure.
  Mirrored the expanded skills to `~/.claude/skills/`.

## 2026-08-20

- Scaffolded the project: moved `DOCUMENTATION-PROMPT.md` into
  `templates/`, added a root `README.md`, initialized git.
