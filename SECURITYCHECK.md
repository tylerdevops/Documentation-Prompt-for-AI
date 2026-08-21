# Security Check

Checklist against the "Security and privacy documentation requirements" in
`templates/DOCUMENTATION-PROMPT.md`. This repo is a markdown prompt toolkit
with no application code, so most items are not applicable.

| Item | Status | Notes |
|---|---|---|
| Forms and validation | N/A | No forms in this repo. |
| Email exposure or obfuscation | N/A | No email addresses in tracked files. |
| Browser storage | N/A | No client-side code. |
| Geolocation | N/A | Not used. |
| Analytics and third-party requests | N/A | None. |
| External links | Pass | README references third-party assistants (ChatGPT, Codex, Claude, Gemini) and two example sites by name/URL only; no forms or embeds. |
| Authentication or authorization | N/A | Not applicable. |
| Content Security Policy / hosting headers | N/A | Repo is not deployed or hosted. |
| Secrets and environment variables | **Needs review** | `README.md` line 51 contains "...sensitive server information, IP Address, root@" — the trailing `root@` reads as a truncated edit (possibly a partial credential/SSH reference). Left as-is per the behavior-preservation rule; confirm intent and complete or remove it. |
