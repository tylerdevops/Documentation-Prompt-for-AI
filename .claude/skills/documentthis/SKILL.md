---
name: documentthis
description: >
  Apply Tyler's documentation-first standard to a web project (HTML/CSS/JS/framework/CMS
  site). Use whenever Tyler invokes /documentthis, or asks to "document this project",
  "document this website", "add full documentation to this site", or similar, for any
  front-end/web project he's working on. Produces native source comments, a complete
  README, an exact asset map, accessibility/security notes, a testing checklist, and
  future theme-distribution guidance — always preceded by an inspection + preview step
  that requires his explicit approval before anything is written.
---

# Document This (Tyler's Web Project Documentation Standard)

This skill packages Tyler's standing documentation prompt (source:
github.com/tylerdevops/Documentation-Prompt-for-AI) so it can be invoked with
`/documentthis` instead of pasting the prompt/link into every project.

Act as a senior front-end engineer, technical writer, accessibility reviewer, and
theme-maintenance specialist. Tyler is documentation-focused — treat comprehensive
source documentation as a standing requirement for this project.

If you have persistent memory available, remember (once, not per-project) that Tyler
prefers web projects to include clearly organized native source comments, a complete
README, an exact asset-directory map, customization instructions, accessibility notes,
testing guidance, and future theme-distribution guidance. Never store project secrets,
credentials, private keys, personal contact data, or sensitive server information in
memory.

## 1. Get project information

If `args` passed to the skill already answers these, use them. Otherwise ask Tyler
briefly (one message, not one question at a time) for whatever is missing — don't
block on fields that are obvious from the repo itself (e.g. technology can usually be
detected):

- Project name
- Website/domain (or local project name if not deployed)
- Project purpose (portfolio / business site / landing page / web app / other)
- Technology (HTML / CSS / JavaScript / framework / CMS)
- Hosting target (Nginx / GitHub Pages / Vercel / Cloudflare / other)
- Intended audience (owner / developers / customers / contributors)
- Possible future distribution (private / free theme / paid theme / unknown)

## 2. Primary objective

Inspect the actual project files and produce documentation that explains how the
website works, how its files connect, how to customize it safely, and how to test and
deploy it. Documentation must match the current source exactly — do not invent
components, paths, dependencies, commands, or features.

## 3. Approval gate — required before editing anything

1. Inspect the current source and directory structure.
2. Identify the main components, behaviors, dependencies, data flow, assets,
   accessibility features, metadata, and deployment assumptions.
3. Show Tyler a documentation preview containing:
   - Proposed comment style
   - Example comments for each source language present
   - README table of contents
   - Exact asset-tree preview
   - Files you plan to modify or add
4. Wait for his explicit approval before proceeding.

Do not rewrite, reorganize, rename, minify, refactor, or change behavior during the
preview stage.

## 4. Source-comment requirements

Use valid native comment syntax per file type:

- HTML: `<!-- ... -->`
- CSS/SCSS: `/* ... */`
- JavaScript/TypeScript: `//`, `/* ... */`, `/** ... */`
- PHP: `//`, `#`, `/* ... */`, PHPDoc where appropriate
- JSX/TSX: `{/* ... */}` inside markup, normal JS/TS comments elsewhere
- YAML: `# ...`
- Shell: `# ...`
- Nginx: `# ...`

Add comments at logical boundaries, not on every obvious line. Comments should explain:
what the component/block does, why it exists, which other files or selectors depend on
it, important state/data attributes/classes/IDs/custom properties, accessibility
relationships and keyboard behavior, fallback and error handling, privacy or security
implications, what a future maintainer can safely customize, and what must stay
synchronized when names or paths change.

Add a concise documented-source header to each primary source file. Use section banners
for major components and JSDoc/PHPDoc for complex functions. Do not add comments that
are incorrect, redundant, speculative, or likely to go stale immediately.

## 5. README requirements

Create or expand `README.md` into a complete owner/developer/theme-user guide. Include
the sections that apply:

1. Project overview
2. Features
3. Technology and third-party dependencies
4. Architecture and file relationships
5. Project directory tree
6. Complete assets directory tree
7. Page or application loading sequence
8. HTML/template/component guide
9. CSS architecture and design tokens
10. JavaScript/application behavior
11. State and storage keys
12. Interactive feature guide
13. Accessibility
14. SEO, metadata, and structured data
15. Privacy and security behavior
16. Complete customization guide
17. Asset naming, dimensions, formats, and optimization
18. Local development
19. Build process, if one exists
20. Deployment and hosting
21. Testing checklist
22. Browser or runtime support
23. Troubleshooting
24. Future reusable-theme preparation
25. Licensing and third-party asset checklist
26. Versioning and changelog recommendations

Use tables where exact mappings are helpful. Use a compact Mermaid diagram when it
materially clarifies how HTML/templates, CSS, JavaScript, assets, storage, and external
services connect. (Note: Tyler dislikes Mermaid Chart's default rendering for
flowcharts/diagrams he'll look at directly — this README-embedded Mermaid code block is
fine since it's documentation source, not a rendered diagram deliverable. If he also
wants a rendered diagram, use Miro instead.)

## 6. Asset documentation requirements

Inspect the real asset folders and references in source files. Document the exact
directory levels, filenames, and extensions. For each folder explain: which component
uses it, where its path is configured, whether JavaScript rotates or preloads it,
recommended dimensions/aspect ratio, cropping/focal-point guidance, file-format and
compression guidance, steps for adding/removing/replacing an asset, and any HTML
width/height, alt text, metadata, or configuration that must change.

Do not infer missing files solely from a naming pattern. Clearly label optional or
recommended files that do not currently exist.

## 7. Accessibility documentation requirements

Explain applicable semantics and accessibility behavior: landmarks and heading
hierarchy, skip links, keyboard navigation, focus styles and focus restoration, ARIA
labels/state/relationships, dialogs/menus/accordions/tabs/filters/live regions, image
alt text, video captions and controls, reduced-motion behavior, color contrast
considerations.

Flag accessibility problems separately. Do not silently fix behavior unless Tyler
approved implementation changes beyond documentation.

## 8. Security and privacy documentation requirements

Document applicable behavior: forms and validation, email exposure or obfuscation,
browser storage, geolocation, analytics and third-party requests, external links,
authentication or authorization, Content Security Policy and hosting headers, secrets
and environment variables.

Never place real secrets or credentials in source comments, examples, README content,
screenshots, output logs, or reusable prompts.

## 9. Future theme-distribution requirements

If the project may become a free or paid theme, explain how to: separate
personal/demo content from reusable code, centralize brand and content settings,
replace personal assets with distributable placeholders, document supported
environments, create a clean installation experience, maintain source and optimized
production editions, add version numbers and a changelog, audit third-party dependency
and asset licenses, and choose/document appropriate distribution terms.

Do not provide definitive legal advice. Identify items that require a rights or license
review.

## 10. Behavior-preservation rule

Unless Tyler explicitly authorizes functional changes: preserve rendered content and
behavior, selectors/IDs/data attributes/URLs/paths/load order, accessibility state
management, responsive behavior, public APIs and configuration names. Do not add
dependencies. Do not reformat unrelated code. Documentation-only changes should produce
no intentional runtime differences.

## 11. Validation requirements (after approval and implementation)

1. Validate HTML/template syntax.
2. Validate CSS syntax.
3. Validate JavaScript/TypeScript syntax.
4. Confirm source comments do not break parsing or rendering.
5. Compare functional source before and after with comments removed where practical.
6. Check internal asset references and anchor targets.
7. Confirm ARIA ID relationships remain valid.
8. Confirm no secret or personal data was newly exposed.
9. Check README links, headings, tables, code fences, and Mermaid syntax.
10. List the final archive contents and verify the ZIP.

## 12. Deliverables

After Tyler approves the preview, provide: documented primary source files, updated
`README.md`, this reusable documentation standard adapted to the project if
appropriate, an optional `CHANGELOG.md` or `LICENSE` (only after approval), a concise
summary of what was documented, validation results, and a recommended next step for
source control or deployment.

If the project is already connected to Git, preserve its history and unrelated
changes. Do not commit, push, publish, or deploy unless Tyler explicitly requests it.

## Short version

If the full standard above is already established in the conversation and Tyler just
wants a quick re-run, this is equivalent:

> Document this web project using our documentation-first standard. Inspect the real
> source and assets, preview the documentation plan, and wait for approval. Then add
> native comments to every primary source file, expand README.md into a complete
> architecture/customization/deployment guide, include the exact asset tree,
> accessibility and privacy behavior, testing and troubleshooting, and future
> free/paid-theme guidance. Preserve functionality and validate everything before
> delivering a ZIP. Never expose or remember secrets.
