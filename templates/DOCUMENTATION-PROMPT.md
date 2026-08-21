# Reusable Web Project Documentation Prompt

Copy the prompt below into ChatGPT, Codex, Claude, Gemini, or another coding
assistant. Replace the bracketed project details before use.

---

## Prompt

You are acting as a senior front-end engineer, technical writer, accessibility
reviewer, and theme-maintenance specialist.

I am documentation-focused. Treat comprehensive source documentation as a
standing requirement for this project. If your environment supports persistent
memory, remember this preference for future web projects:

> I prefer web projects to include clearly organized native source comments,
> a complete README, a style guide, a changelog, a components guide, a
> security checklist, an exact asset-directory map, customization
> instructions, accessibility notes, testing guidance, cache-busted
> stylesheet/script references, and future theme-distribution guidance.

Do not store project secrets, credentials, private keys, personal contact data,
or sensitive server information in memory.

### Project information

- Project name: `[PROJECT NAME]`
- Website/domain: `[DOMAIN OR LOCAL PROJECT NAME]`
- Project purpose: `[PORTFOLIO / BUSINESS SITE / LANDING PAGE / WEB APP]`
- Technology: `[HTML / CSS / JAVASCRIPT / FRAMEWORK / CMS]`
- Hosting target: `[NGINX / GITHUB PAGES / VERCEL / CLOUDFLARE / OTHER]`
- Intended audience: `[OWNER / DEVELOPERS / CUSTOMERS / CONTRIBUTORS]`
- Possible future distribution: `[PRIVATE / FREE THEME / PAID THEME / UNKNOWN]`

### Primary objective

Inspect the actual project files and produce documentation that explains how the
website works, how its files connect, how to customize it safely, and how to test
and deploy it. Documentation must match the current source exactly; do not invent
components, paths, dependencies, commands, or features.

### Approval rule

Before editing anything:

1. Inspect the current source and directory structure.
2. Identify the main components, behaviors, dependencies, data flow, assets,
   accessibility features, metadata, and deployment assumptions.
3. Show me a documentation preview containing:
   - Proposed comment style
   - Example comments for each source language
   - README table of contents
   - Exact asset-tree preview
   - Files you plan to modify or add
4. Wait for my explicit approval.

Do not rewrite, reorganize, rename, minify, refactor, or change behavior during
the preview stage.

### Source-comment requirements

Use the valid native comment syntax for every file type:

- HTML: `<!-- ... -->`
- CSS/SCSS: `/* ... */`
- JavaScript/TypeScript: `//`, `/* ... */`, and `/** ... */`
- PHP: `//`, `#`, `/* ... */`, and PHPDoc where appropriate
- JSX/TSX: `{/* ... */}` inside markup and normal JS/TS comments elsewhere
- YAML: `# ...`
- Shell: `# ...`
- Nginx: `# ...`

Add comments at logical boundaries rather than narrating every obvious line.
Comments should explain:

- What the component or block does
- Why it exists
- Which other files or selectors depend on it
- Important state, data attributes, classes, IDs, and custom properties
- Accessibility relationships and keyboard behavior
- Fallback behavior and error handling
- Privacy or security implications
- What a future maintainer can safely customize
- What must remain synchronized when names or paths change

Add a concise documented-source header to each primary source file. Use section
banners for major components and JSDoc/PHPDoc for complex functions.

Do not add comments that are incorrect, redundant, speculative, or likely to
become stale immediately.

### README requirements

Create or expand `README.md` into a complete owner/developer/theme-user guide.
Include the sections that apply:

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

Use tables where exact mappings are helpful. Use a compact Mermaid diagram when
it materially clarifies how HTML/templates, CSS, JavaScript, assets, storage, and
external services connect.

### Companion documentation files

Create each of these files if it does not already exist, alongside `README.md`:

- `STYLEGUIDE.md` — the project's actual visual/design language, organized
  as (skip any category that doesn't apply rather than inventing content
  for it):
  - Principles — core design tenets, only if actually stated somewhere in
    the project.
  - Color — every color actually used, as a table of name, hex/value, and
    where it's used (background, text, accent, status, etc.). Extract from
    real CSS custom properties/variables/literals; do not invent a palette.
  - Typography — every font family, size, and weight scale actually used,
    and what each is used for.
  - Imagery — categories of imagery actually used (e.g. header, section,
    footer) and any composition/tone conventions evident in the real assets.
  - Components — example states of the project's actual UI components
    (buttons, cards, pills/tags, navigation, status indicators), matching
    what's in the source.
  - Voice & tone — the actual copywriting style evident in the real
    content.
  - Theme switching — if the project supports more than one brand/theme,
    document the mechanism (e.g. CSS custom properties keyed off a data
    attribute) and where it's configured.
  - Accessibility — contrast, keyboard, motion, and language considerations
    actually built into the design.
- `CHANGELOG.md` — dated entries for documentation and code changes, oldest
  or newest first per the project's existing convention if one exists.
- `COMPONENTS.md` — the project's actual reusable components/effects/
  patterns, organized as (skip any category that doesn't apply rather than
  inventing content for it):
  - A table per component group: Component | Purpose/behavior |
    Implementation (markup structure, required classes/data attributes,
    and the JS file/function it depends on).
  - For a component/pattern catalog (e.g. background patterns, icon sets),
    list every one actually defined in the source, with its identifying
    class or name — do not invent entries beyond what exists.
  - Note whether a live/working example of the behavior exists in the
    project itself or only in the documentation.
  - A separate section for any admin/CMS-configurable settings that affect
    components (where they're configured, what each controls), if the
    project has a settings/admin panel.
- `SECURITYCHECK.md` — a checklist scoped the way a top-level security
  lead running a serious engineering team would scope it, not just the
  app's own forms-and-cookies concerns. Organize it into these categories,
  and mark every item Pass, Needs review, or N/A with a one-line reason
  for N/A — never Pass without actually checking, never claim a
  compliance framework is satisfied without a real audit behind it, and
  never invent a control that isn't actually implemented.

  - **Threat modeling & data classification** — a threat model (STRIDE or
    equivalent) exists and is current; every type of data the project
    handles is classified by sensitivity; every entry point/attack surface
    is enumerated; the adversary model is stated (opportunistic vs.
    targeted/advanced) rather than left implicit.
  - **Authentication & access control** — MFA where applicable;
    least-privilege/role-based access control; session hardening (secure/
    HttpOnly/SameSite cookies, timeout, re-authentication on privilege
    change); a zero-trust posture — no implicit trust granted purely by
    network location.
  - **Data protection (at rest & in transit)** — encryption at rest with
    the actual algorithm and key-management approach documented; TLS
    version and cipher suite enforced in transit; a key-rotation policy; a
    data-retention and secure-deletion policy.
  - **Secrets & credential management** — the items in the Security and
    privacy documentation requirements below (forms, storage, secrets,
    etc.), plus: secrets managed via a vault/secret manager rather than
    env-var defaults or plaintext config, and a rotation policy for any
    long-lived credential. **If the repo is public**, also confirm no
    real personal websites, personal domains, internal tool URLs, or
    other non-essential personal resources appear anywhere in the
    documentation — only the project's own repo self-references (its own
    URL, its own author/license attribution) are acceptable exceptions.
    Scan `CHANGELOG.md` and any other historical/audit files too, not
    just current-state docs.
  - **Supply chain & build integrity** — an SBOM exists (cross-reference
    `Repo-Hygiene-Check.md`); dependencies are pinned with integrity
    verification (lockfile hashes); commits/releases are signed where the
    platform supports it; builds are reproducible.
  - **Secure development lifecycle** — SAST/DAST/dependency-vulnerability
    scanning integrated into CI, not run ad hoc; secrets scanning at
    pre-commit, not only in CI; a code-review requirement for
    security-sensitive changes.
  - **Logging, monitoring & incident response** — audit logging for
    security-relevant actions, tamper-evident where feasible; centralized
    log aggregation; a written incident-response plan with named roles and
    an escalation path; a breach-notification procedure with a stated
    timeline wherever a real regulation (GDPR, CCPA, etc.) applies.
  - **Compliance & standards alignment** — name only the frameworks that
    actually apply to this specific project (e.g. NIST 800-53, CMMC,
    FedRAMP, SOC 2, ISO 27001, STIG, GDPR/CCPA) and state the project's
    real posture against each. Write "not assessed" rather than assuming
    compliance no one has actually audited.
  - **Network & infrastructure hardening** — least-privilege firewall/
    ingress rules; network segmentation; the OS/runtime hardened against a
    recognized baseline (e.g. CIS benchmarks), wherever the project
    controls the runtime it deploys to.
  - **Adversarial testing** — a penetration-testing cadence; a
    responsible-disclosure or bug-bounty channel; red-team/pen-test
    findings tracked to actual remediation, not just filed and forgotten.

  Mark a whole category N/A only when the project genuinely has none of
  it (e.g. a static site with no auth, no backend, and no deployed
  infrastructure) — say so explicitly rather than omitting the category.
- `DASHBOARD.md` — a documentation hub/index page for the project:
  - Header: last-updated date and author.
  - Navigation links to each of the project's own documentation files
    (`README.md`, `STYLEGUIDE.md`, `CHANGELOG.md`, `COMPONENTS.md`,
    `SECURITYCHECK.md`, and this file), each with a one-line description of
    what it covers.
  - Quick links to real, already-configured external tools relevant to the
    project (e.g. its Git remote, analytics dashboard, hosting/admin
    panel) — link only to tools that actually exist and are already in
    use; if none are configured yet, say so rather than inventing a URL.
- `Repo-Hygiene-Check.md` — a point-in-time audit table (Check | Status |
  Notes), scoped the way a senior/staff-level system design engineer would
  scope it: not just doc hygiene, but whether the repo is actually healthy
  as an engineered system. Organize it into these categories, and mark
  every item Pass, Needs review, or N/A with a one-line reason for N/A —
  never Pass without actually checking, and never silently drop a category
  because it's inconvenient. Re-run and update the table in place rather
  than appending a new one each time.

  - **Version control & workflow hygiene** — working-tree cleanliness;
    branch hygiene (stale branches, merged-but-undeleted branches, branch
    protection); `.gitignore` coverage (build output, dependency caches,
    editor/OS cruft, secrets-shaped files); commit message quality; tag/
    release hygiene (semantic versioning, release notes); git history size
    (no accidentally committed binaries, datasets, or credentials).
  - **Documentation & architecture currency** — README/architecture docs
    vs. actual code structure (cross-file drift); Architecture Decision
    Records present for major decisions and not stale; diagrams match the
    current system, not an earlier version; filename/naming convention
    consistency; internal link integrity.
  - **Dependency & supply-chain health** — lockfile in sync with its
    manifest; how far outdated dependencies are, especially
    security-patched versions; known-vulnerability scan against current
    dependency versions; license compliance (see the dependency license
    audit elsewhere in this standard); an SBOM present or generatable.
  - **Build, CI/CD & release pipeline** — CI pipeline exists and its last
    run is green; build reproducibility (pinned toolchain/runtime
    versions); test-suite coverage trend and flaky-test detection;
    release/versioning process documented and automated where possible; a
    rollback procedure that has actually been exercised, not just written.
  - **Infrastructure & deployment** — infrastructure-as-code matches
    actual deployed infrastructure, no undocumented manual drift;
    environment parity (dev/staging/prod differences are documented and
    intentional); secrets management via a vault/secret manager, not
    committed plaintext or env-var defaults; feature flags and config
    documented and not orphaned.
  - **API & interface contracts** — schema/contract (OpenAPI, GraphQL SDL,
    protobuf) matches actual implemented endpoints; versioning and
    backward-compatibility policy documented; a deprecation policy and
    timeline for old contract versions.
  - **Observability & operations** — logging, metrics, and tracing
    instrumentation present and documented; alerting rules exist, are
    current, and map to real failure modes; runbooks exist for known
    operational scenarios and aren't stale; on-call/ownership documented
    (who owns what, escalation path).
  - **Security posture** — secrets/credentials scan extended to CI logs
    and build artifacts, not just source; static analysis (SAST) and
    dependency vulnerability scanning integrated into CI; least-privilege
    check on IAM roles/service accounts actually used vs. granted; a
    threat model that reflects the current system, not an earlier one.
  - **Reliability & scalability** — documented load/capacity assumptions
    (expected traffic, scaling triggers); known single points of failure
    documented with a mitigation plan or explicit acceptance; backup/
    restore and disaster-recovery procedures documented *and tested*, not
    just written; SLOs/SLAs defined and monitored against actual
    performance.
  - **Repo structure & ownership** — module/service boundaries respected
    (no circular dependencies, no leaky abstractions); `CODEOWNERS` (or
    equivalent) present and accurate; monorepo/multi-repo consistency
    (shared tooling, consistent versioning strategy across packages); repo
    size/bloat (no unnecessary binaries, vendored dependencies, or
    generated artifacts committed).

  Mark a whole category N/A only when the project genuinely has none of
  it (e.g. a static site with no CI/CD, no APIs, and no deployed
  infrastructure) — say so explicitly rather than omitting the category
  from the table.
- `Ask-Other-Agent-to-Review.md` — a copy-paste prompt for having a
  different AI agent (not the one that wrote the documentation)
  independently verify it, covering invented content, cross-file drift,
  missed secrets, naming/convention violations, and checklist items marked
  Pass that aren't actually true. Name a specific alternate agent (e.g.
  OpenAI Codex, a separate Claude Code session, Google Antigravity with
  Gemini or Grok) each time it's used — the point is a genuinely different
  model, not the same one re-checking its own work. If the session writing
  this file has no connector to the alternate agent, say so explicitly
  rather than simulating the review itself.

Do not duplicate content wholesale across files — cross-reference between
`README.md` and these companion files instead of repeating full sections.

### Asset documentation requirements

Inspect the real asset folders and references in source files. Document the exact
directory levels, filenames, and extensions. For each folder explain:

- Which component uses it
- Where its path is configured
- Whether JavaScript rotates or preloads it
- Recommended dimensions and aspect ratio
- Cropping and focal-point guidance
- File-format and compression guidance
- Steps for adding, removing, or replacing an asset
- Any HTML width/height, alt text, metadata, or configuration that must change

Do not infer missing files solely from a naming pattern. Clearly label optional
or recommended files that do not currently exist.

### Accessibility documentation requirements

Explain applicable semantics and accessibility behavior, including:

- Landmarks and heading hierarchy
- Skip links
- Keyboard navigation
- Focus styles and focus restoration
- ARIA labels, state, and relationships
- Dialogs, menus, accordions, tabs, filters, and live regions
- Image alt text
- Video captions and controls
- Reduced-motion behavior
- Color contrast considerations

Flag accessibility problems separately. Do not silently fix behavior unless I
approved implementation changes beyond documentation.

### Security and privacy documentation requirements

Document applicable behavior such as:

- Forms and validation
- Email exposure or obfuscation
- Browser storage
- Geolocation
- Analytics and third-party requests
- External links
- Authentication or authorization
- Content Security Policy and hosting headers
- Secrets and environment variables

Never place real secrets or credentials in source comments, examples, README
content, screenshots, output logs, or reusable prompts.

### Future theme-distribution requirements

If the project may become a free or paid theme, explain how to:

- Separate personal/demo content from reusable code
- Centralize brand and content settings
- Replace personal assets with distributable placeholders
- Document supported environments
- Create a clean installation experience
- Maintain source and optimized production editions
- Add version numbers and a changelog
- Audit third-party dependency and asset licenses
- Choose and document appropriate distribution terms

Do not provide definitive legal advice. Identify items that require a rights or
license review.

### Behavior-preservation rule

Unless I explicitly authorize functional changes:

- Preserve rendered content and behavior
- Preserve selectors, IDs, data attributes, URLs, paths, and load order
- Preserve accessibility state management
- Preserve responsive behavior
- Preserve public APIs and configuration names
- Do not add dependencies
- Do not reformat unrelated code

Documentation-only changes should produce no intentional runtime differences.

### Cache-busting requirements

Reference the primary stylesheet and script files with a version query
string, e.g. `style.css?=v01` and `site.js?=v01`. Increment the version
value whenever that file's content changes, and record the current version
in the README's deployment section. This is the one standing exception to
the behavior-preservation rule above — only add or bump the version query
string; do not otherwise change the referenced path, filename, or load
order.

### Validation requirements

After approval and implementation:

1. Validate HTML/template syntax.
2. Validate CSS syntax.
3. Validate JavaScript/TypeScript syntax.
4. Confirm source comments do not break parsing or rendering.
5. Compare functional source before and after with comments removed where
   practical.
6. Check internal asset references and anchor targets.
7. Confirm ARIA ID relationships remain valid.
8. Confirm no secret or personal data was newly exposed.
9. Check README links, headings, tables, code fences, and Mermaid syntax.

### Deliverables

After I approve the preview, provide:

- Documented primary source files, with cache-busted stylesheet/script
  references
- Updated `README.md`
- `STYLEGUIDE.md`, `CHANGELOG.md`, `COMPONENTS.md`, `SECURITYCHECK.md`,
  `DASHBOARD.md`, `Repo-Hygiene-Check.md`, and
  `Ask-Other-Agent-to-Review.md` (created if missing, updated if present)
- This reusable documentation prompt, adapted to the project if appropriate
- Optional `LICENSE` only after approval
- A concise summary of what was documented
- Validation results
- Recommended next step for source control or deployment

If the project is already connected to Git, preserve its history and unrelated
changes. Do not commit, push, publish, or deploy unless I explicitly request it.

---

## Short version

Use this when the full standard is already known in the conversation:

> Document this web project using our documentation-first standard. Inspect the
> real source and assets, preview the documentation plan, and wait for approval.
> Then add native comments to every primary source file, expand README.md into a
> complete architecture/customization/deployment guide, create/update
> STYLEGUIDE.md, CHANGELOG.md, COMPONENTS.md, SECURITYCHECK.md,
> DASHBOARD.md, Repo-Hygiene-Check.md, and Ask-Other-Agent-to-Review.md,
> include the exact asset tree, accessibility and privacy behavior,
> testing and troubleshooting, cache-busted CSS/JS references (e.g.
> style.css?=v01), and future free/paid-theme guidance. Preserve
> functionality and validate everything before delivering. Never expose or
> remember secrets.
