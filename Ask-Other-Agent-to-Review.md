# Ask Another Agent to Review

A copy-paste prompt for getting an independent second opinion on this
repo's documentation from a different AI agent than the one that wrote
it — Claude Sonnet 5 (Claude Code), in this repo's case so far. The point
is a genuinely different model catching a different set of blind spots,
not the same model re-reading its own reasoning and agreeing with itself.

## Which agent to use

Pick one that is **not** the agent/session that produced the documentation
you're reviewing:

- **OpenAI Codex** (CLI or IDE extension)
- **Claude Code**, but a fresh session with no memory of the original
  conversation — reusing the same session just re-confirms its own earlier
  reasoning
- **Google Antigravity**, running Gemini or Grok as the underlying model

## The review prompt

Copy everything below into the other agent, after replacing the bracketed
project path:

---

You are performing an independent review of documentation written by a
different AI agent for the project at `[PROJECT PATH OR REPO URL]`. Do not
assume anything in it is correct — verify every claim against the actual
source files before trusting it.

Check specifically for:

1. **Invented content** — any component, path, dependency, command, or
   feature mentioned in the docs that does not actually exist in the
   source.
2. **Cross-file drift** — companion files (e.g. README, STYLEGUIDE,
   CHANGELOG, COMPONENTS, SECURITYCHECK, DASHBOARD, Repo-Hygiene-Check)
   that disagree with each other or with the real source.
3. **Missed secrets or credentials** — anything sensitive left in
   comments, examples, config, or logs.
4. **Naming/convention violations** — filenames, headings, or structure
   that don't match the project's own documented style guide.
5. **Accessibility and security gaps** the original pass may have glossed
   over, or marked "Pass" without actually checking.
6. **Stale content** — anything describing behavior, versions, or
   structure that no longer matches the current source.

Report findings as a list: what's wrong, which file and line, and why it
matters. Do not fix anything yourself — flag it for a human decision, the
same way this project's own documentation standard requires an approval
gate before edits.

---

## First attempt — limits of this pass

This file is the reusable prompt itself; actually running it isn't
something this session can do end-to-end. This session is Claude Code
(Claude Sonnet 5) with no connector to Codex, Gemini, or Grok, so it
cannot hand this prompt to another agent and get a response back itself.
To use it for real, paste the prompt above into one of the agents listed
above yourself.

A ready starting point once you do: this repo's own
[`Repo-Hygiene-Check.md`](Repo-Hygiene-Check.md) has no open items as of
2026-08-21 — a good first test of whether a different agent agrees, or
surfaces something this session missed entirely.
