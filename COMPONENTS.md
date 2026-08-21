# Components

This toolkit has six reusable pieces. Table format follows the
`COMPONENTS.md` template (see
[`templates/DOCUMENTATION-PROMPT.md`](templates/DOCUMENTATION-PROMPT.md)).
There is no component/pattern catalog or admin-configurable settings panel
in this repo, so those sections are omitted.

| Component | Purpose | Location | Depends on |
|---|---|---|---|
| Full prompt | Copy-paste prompt establishing the full documentation-first standard for a target web project | `templates/DOCUMENTATION-PROMPT.md`, `## Prompt` section | Bracketed placeholders (`[PROJECT NAME]`, etc.) filled in per project |
| Short-form re-prompt | Compact re-invocation for a conversation where the assistant already has the full standard in context | `templates/DOCUMENTATION-PROMPT.md`, `## Short version` section | Full prompt already established earlier in the same conversation |
| `documentthisweb` skill | Wraps the web standard as a `/documentthisweb` slash command so it doesn't need to be copy-pasted per project | `.claude/skills/documentthisweb/SKILL.md` (this repo, mirrored to `~/.claude/skills/` for actual use) | Staying in sync with `templates/DOCUMENTATION-PROMPT.md` |
| `documentthisMacOS` skill | Same standard adapted for native macOS projects (Swift/SwiftUI, Objective-C/AppKit) — entitlements/sandbox audit, asset catalogs, Mac App Store vs. notarized distribution | `.claude/skills/documentthisMacOS/SKILL.md` (this repo, mirrored to `~/.claude/skills/`) | Same seven companion-doc requirements as the web skill |
| `documentthisWindows` skill | Same standard adapted for native Windows projects (.NET/C# WPF/WinForms/WinUI, or native C++) — registry/installer footprint audit, resource files, Microsoft Store vs. MSI/MSIX distribution | `.claude/skills/documentthisWindows/SKILL.md` (this repo, mirrored to `~/.claude/skills/`) | Same seven companion-doc requirements as the web skill |
| `documentthis` skill (deprecated) | Legacy unified web skill, kept only as a redirect stub pointing to `/documentthisweb` | `.claude/skills/documentthis/SKILL.md` (this repo, mirrored to `~/.claude/skills/`) | Superseded by `documentthisweb` |

## Live examples

The three prompt/skill pieces are documentation/prompt text, not executable
code — there is no "live demo" distinct from reading the file itself.

## Sync note

As of 2026-08-21 the three platform skills (`documentthisweb`,
`documentthisMacOS`, `documentthisWindows`) carry the full standard,
including the seven companion-doc requirements and the standing checks
that were previously only in the global skill copy (asset cache-busting
for web, and a third-party dependency license audit for all three
platforms). `templates/DOCUMENTATION-PROMPT.md` still only covers the web
case directly — it doesn't have macOS/Windows variants of its own, since
it's meant for pasting into assistants without Claude Code skill support.
