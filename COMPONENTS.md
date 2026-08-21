# Components

This toolkit has three reusable pieces. Table format follows the
`COMPONENTS.md` template (see
[`templates/DOCUMENTATION-PROMPT.md`](templates/DOCUMENTATION-PROMPT.md)),
calibrated against a real example: [build.ty1er.com/components](https://build.ty1er.com/components/).
There is no component/pattern catalog or admin-configurable settings panel
in this repo, so those sections are omitted.

| Component | Purpose | Location | Depends on |
|---|---|---|---|
| Full prompt | Copy-paste prompt establishing the full documentation-first standard for a target web project | `templates/DOCUMENTATION-PROMPT.md`, `## Prompt` section | Bracketed placeholders (`[PROJECT NAME]`, etc.) filled in per project |
| Short-form re-prompt | Compact re-invocation for a conversation where the assistant already has the full standard in context | `templates/DOCUMENTATION-PROMPT.md`, `## Short version` section | Full prompt already established earlier in the same conversation |
| `documentthis` skill | Wraps the same standard as a `/documentthis` slash command so it doesn't need to be copy-pasted per project | `~/.claude/skills/documentthis` (outside this repo — a local Claude Code skill, not tracked in this git history) | Staying in sync with `templates/DOCUMENTATION-PROMPT.md` |

## Live examples

All three are documentation/prompt text, not executable code — there is no
"live demo" distinct from reading the file itself.

## Sync note

As of 2026-08-21 the `documentthis` skill copy already includes two
standing checks — asset cache-busting caveats for platforms like Ghost,
and a third-party dependency license audit — that this repo's
`templates/DOCUMENTATION-PROMPT.md` does not yet have written down. Check
whether that gap should be closed the next time either file changes.
