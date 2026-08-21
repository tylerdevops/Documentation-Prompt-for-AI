---
name: documentthisWindows
description: >
  Apply your team's documentation-first standard to a native Windows project (.NET/C#
  WPF, WinForms, UWP/WinUI, or native C++/Win32). Use whenever you invoke
  /documentthisWindows, or ask to "document this Windows app", "document this Windows
  project", or similar. Produces native source comments, a complete README, companion
  docs (style guide, changelog, components guide, security checklist, dashboard, repo
  hygiene check, second-opinion review prompt), an exact resource-file map,
  accessibility/security/registry notes, a testing checklist, and distribution
  guidance (Microsoft Store vs. MSI/MSIX installer) — always preceded by an inspection
  + preview step that requires explicit approval before anything is written.
---

# Document This — Windows

This skill packages your team's standing documentation prompt, adapted for native
Windows projects, so it can be invoked with `/documentthisWindows` instead of pasting a
prompt into every project.

Act as a senior Windows engineer, technical writer, accessibility reviewer, and release
specialist. Treat comprehensive source documentation as a standing requirement for
this project.

If you have persistent memory available, remember (once, not per-project) that your
team prefers Windows projects to include clearly organized native source comments, a
complete README, a style guide, a changelog, a components guide, a security checklist,
a documentation dashboard, a repo hygiene check, a second-opinion review prompt, an
exact resource-file map, customization instructions, accessibility notes, testing
guidance, a registry/installer footprint audit, and distribution guidance. Never store
project secrets, credentials, signing-certificate material, or personal contact data
in memory.

## 1. Get project information

If `args` passed to the skill already answers these, use them. Otherwise ask briefly
(one message, not one question at a time) for whatever is missing — don't block on
fields that are obvious from the project itself:

- Project name and root namespace/assembly name
- Project purpose (desktop utility / productivity app / developer tool / other)
- Technology (.NET/C# with WPF, WinForms, or WinUI/UWP; or native C++/Win32)
- Minimum supported Windows version and architecture (x64/ARM64)
- Distribution target (Microsoft Store / MSI or MSIX installer / ClickOnce /
  internal-only)
- Intended audience (end user / developers / internal team)
- Possible future distribution (open source / commercial / internal tool / unknown)

## 2. Primary objective

Inspect the actual project files and produce documentation that explains how the app
works, how its projects/files connect, how to customize it safely, and how to test,
build, and distribute it. Documentation must match the current source exactly — do not
invent components, paths, dependencies, commands, registry keys, or features.

## 3. Approval gate — required before editing anything

1. Inspect the current source, solution/project structure, and target framework(s).
2. Identify the main components, behaviors, dependencies, data flow, resource files,
   accessibility features, registry/app-manifest usage, and deployment assumptions.
3. Show a documentation preview containing:
   - Proposed comment style
   - Example comments for each source language present
   - README table of contents
   - Exact resource-file tree preview
   - Files you plan to modify or add
4. Wait for explicit approval before proceeding.

Do not rewrite, reorganize, rename, minify, refactor, or change behavior during the
preview stage.

## 4. Source-comment requirements

Use valid native comment syntax per file type:

- C#: `//`, `/* ... */`, and `/// ` XML doc comments for public API
- C++/C: `//`, `/* ... */`
- XAML: `<!-- ... -->`
- PowerShell (`.ps1`) scripts: `# ...` for line comments, `<# ... #>` for block
  comments and comment-based help (`.SYNOPSIS`/`.DESCRIPTION`/`.PARAMETER`)
- Batch files (`.bat`/`.cmd`): `REM ...` or `:: ...`
- Registry `.reg` files: `; ...`

PowerShell and batch/terminal scripts turn up in Windows projects as build/publish
automation, installer pre/post-install actions, and dev-environment setup (e.g. a
`build.ps1`, a `scripts/` folder, or a WiX/MSIX post-build step). Document them with
the same rigor as application source: what the script does, why it exists, what
execution policy or elevation (`RunAs`/UAC) it requires, what environment/PATH
assumptions it makes, and what breaks if it's moved or renamed. Use PowerShell's
comment-based help block for any script meant to be run directly by a developer.

Add comments at logical boundaries, not on every obvious line. Comments should
explain: what the component/block does, why it exists, which other files or types
depend on it, important state/dependency-property/event relationships, accessibility
relationships and keyboard behavior, fallback and error handling, privacy or security
implications (registry keys, credential storage), what a future maintainer can safely
customize, and what must stay synchronized (namespace, assembly name, registry key
names) when names change.

Add a concise documented-source header to each primary source file. Use section
banners for major components and XML doc comments for complex members. Do not add
comments that are incorrect, redundant, speculative, or likely to go stale
immediately.

## 5. README requirements

Create or expand `README.md` into a complete owner/developer guide. Include the
sections that apply:

1. Project overview
2. Features
3. Technology and third-party dependencies (NuGet packages)
4. Architecture and project/solution relationships
5. Project directory tree
6. Complete resource-file tree (`.resx`, icons, images)
7. Application startup sequence (`Main`/`App.xaml` startup, DI container
   initialization)
8. View/XAML/WinForms-form guide
9. Design tokens (WPF styles/resource dictionaries, Fluent Design, WinUI theming)
10. Application/business logic behavior
11. State and persistence (app settings, registry keys used, isolated storage)
12. Interactive feature guide (menus, context menus, drag & drop, keyboard shortcuts)
13. Accessibility
14. Metadata (assembly info, app manifest, package manifest)
15. Privacy and security behavior
16. Complete customization guide
17. Asset naming, dimensions, formats (icon sizes, DPI-scale variants)
18. Local development (Visual Studio version, .NET version/target framework)
19. Build process (MSBuild, CI) and any PowerShell/batch automation scripts
    involved (build/publish scripts, installer pre/post-install actions) —
    what each does, how it's invoked, and what execution policy/elevation
    it requires
20. Deployment (Microsoft Store / MSI/MSIX installer / ClickOnce, code signing)
21. Testing checklist (MSTest/NUnit/xUnit, UI automation tests)
22. Windows version/architecture support (x64/ARM64, minimum OS build)
23. Troubleshooting
24. Future reusable-template preparation, if applicable
25. Licensing and third-party dependency checklist
26. Versioning and changelog recommendations (assembly/file/package version)

Use tables where exact mappings are helpful. Use a compact Mermaid diagram when it
materially clarifies how views, state, and services connect.

## 5a. Companion documentation files

Create each of these if it does not already exist, alongside `README.md` (skip a
category within a file that doesn't apply rather than inventing content for it):

- `STYLEGUIDE.md` — Principles, Color, Typography, Imagery, Components, Voice & tone,
  Theme switching (light/dark, Fluent accent color), Accessibility — extracted from
  the real resource dictionaries, styles, and UI copy, never invented.
- `CHANGELOG.md` — dated entries, newest first.
- `COMPONENTS.md` — a Component | Purpose/behavior | Implementation table for every
  reusable view/control/user-control actually in the source, plus any
  user-configurable settings that affect them.
- `SECURITYCHECK.md` — a checklist scoped the way a top-level security lead running a
  serious engineering team would scope it, not just registry-and-UAC concerns.
  Organize it into these categories, and mark every item Pass, Needs review, or N/A
  with a one-line reason for N/A — never Pass without actually checking, never claim
  a compliance framework is satisfied without a real audit behind it, and never
  invent a control that isn't actually implemented.

  - **Threat modeling & data classification** — a threat model exists and is
    current; every type of data the app handles is classified by sensitivity; every
    entry point (network, IPC, file association, registry-triggered launch) is
    enumerated; the adversary model is stated rather than left implicit.
  - **Authentication & access control** — for any app with accounts: MFA where
    applicable, least-privilege on any backend roles, session/token hardening, no
    implicit trust by network location.
  - **Data protection (at rest & in transit)** — Windows Credential Manager or DPAPI
    (not plaintext config/registry) for credentials/tokens; TLS enforced for any
    network calls; a data-retention and deletion policy for local user data.
  - **Secrets & credential management** — the items in the Security and privacy
    documentation requirements below (registry, isolated storage, manifest), plus:
    no API keys or signing-certificate material committed to source.
  - **Supply chain & build integrity** — the dependency license audit (section 8a)
    plus: NuGet dependencies pinned to exact versions with a lockfile, code-signing/
    Authenticode identity actually verified before distribution.
  - **Secure development lifecycle** — static analysis (Roslyn analyzers or a
    third-party SAST) run before release; secrets scanning at pre-commit.
  - **Logging, monitoring & incident response** — telemetry/crash reporting
    documented; an incident-response plan for a bad release (rollback via a previous
    installer/MSIX package) or a compromised dependency.
  - **Compliance & standards alignment** — name only the frameworks that actually
    apply (e.g. Microsoft Store policy requirements, GDPR/CCPA if there's an EU/CA
    user base, FedRAMP/CMMC if targeting government customers) and state real posture
    against each. Write "not assessed" rather than assuming compliance no one has
    audited.
  - **Network & infrastructure hardening** — the registry/installer footprint audit
    (section 6a) plus least-privilege on any backend infrastructure the app depends
    on.
  - **Adversarial testing** — N/A for most single-developer apps; note it explicitly
    if there's no penetration-testing cadence or disclosure channel, rather than
    omitting the category.

  Mark a whole category N/A only when the app genuinely has none of it (e.g. a
  local-only utility with no accounts, no network calls, and no backend) — say so
  explicitly rather than omitting the category.
- `DASHBOARD.md` — a documentation hub: last-updated date and author, navigation links
  to each of the project's own doc files with a one-line description, and quick links
  to real, already-configured external tools (Git remote, Partner Center, crash
  reporting) — say "not configured" rather than inventing a URL.
- `Repo-Hygiene-Check.md` — a point-in-time audit table (Check | Status | Notes),
  scoped the way a senior/staff-level system design engineer would scope it: not just
  doc hygiene, but whether the project is actually healthy as an engineered system.
  Organize it into these categories, and mark every item Pass, Needs review, or N/A
  with a one-line reason for N/A — never Pass without actually checking, and never
  silently drop a category because it's inconvenient. Re-run and update the table in
  place rather than appending a new one each time.

  - **Version control & workflow hygiene** — working-tree cleanliness; branch hygiene
    (stale branches, merged-but-undeleted branches, branch protection); `.gitignore`
    coverage (`bin/`, `obj/`, `.vs/`, secrets-shaped files); commit message quality;
    tag/release hygiene; git history size (no accidentally committed binaries,
    signing certificates, or credentials).
  - **Documentation & architecture currency** — README/architecture docs vs. actual
    project/solution structure (cross-file drift); Architecture Decision Records
    present for major decisions and not stale; diagrams match the current app;
    filename/naming convention consistency; internal link integrity.
  - **Dependency & supply-chain health** — NuGet lockfile (`packages.lock.json`) in
    sync with package references; how far outdated dependencies are; known-
    vulnerability scan; license compliance (see the dependency license audit, section
    8a); an SBOM present or generatable.
  - **Build, CI/CD & release pipeline** — CI (Azure DevOps, GitHub Actions) exists
    and its last run is green; build reproducibility (pinned .NET SDK/toolchain
    version); test-suite coverage trend and flaky-test detection; versioning/release
    process documented; a rollback/hotfix procedure that's actually been exercised.
  - **Infrastructure & deployment** — any backend/API the app depends on matches
    what's actually deployed; environment parity (dev/staging/prod endpoint
    differences documented); secrets management via Windows Credential Manager or a
    secret manager, not committed plaintext; feature flags/remote config documented
    and not orphaned.
  - **API & interface contracts** — for an app with a backend: schema/contract
    matches actual implemented endpoints; versioning and backward-compatibility
    policy documented; a deprecation policy for old contract/app versions.
  - **Observability & operations** — crash reporting/telemetry instrumentation
    present and documented; alerting maps to real failure modes; a runbook for known
    operational scenarios (e.g. a bad release needing rollback); ownership
    documented.
  - **Security posture** — secrets/credentials scan extended to CI logs and build
    artifacts, not just source; the registry/installer footprint audit (section 6a);
    static analysis integrated into CI; a threat model reflecting the current app, if
    one is warranted.
  - **Reliability & scalability** — documented usage/load assumptions if there's a
    backend; known single points of failure documented with a mitigation or explicit
    acceptance; backup/restore for any user data, tested not just written; crash-
    free-rate or similar quality targets defined and monitored.
  - **Repo structure & ownership** — project/assembly boundaries respected (no
    circular references); a `CODEOWNERS` file (or equivalent) present and accurate if
    multiple maintainers exist; solution-wide consistency across projects; repo
    size/bloat (no unnecessary binaries, vendored dependencies, or generated
    artifacts committed).

  Mark a whole category N/A only when the project genuinely has none of it (e.g. a
  small single-developer utility with no CI/CD and no backend) — say so explicitly
  rather than omitting the category from the table.
- `Ask-Other-Agent-to-Review.md` — a copy-paste prompt for having a different AI agent
  (not the one that wrote the documentation) independently verify it. Name a specific
  alternate agent (e.g. OpenAI Codex, a separate Claude Code session, Google Antigravity
  with Gemini or Grok) each time — the point is a genuinely different model, not the
  same one re-checking its own work. If you have no connector to the alternate agent,
  say so explicitly rather than simulating the review yourself.

Do not duplicate content wholesale across files — cross-reference between `README.md`
and these companion files instead of repeating full sections.

## 6. Resource/asset documentation requirements

Inspect the real `.resx` files, icon (`.ico`) assets, image assets, and DPI-scale
variants (100%/150%/200%, or `.scale-100`/`.scale-200` for packaged apps). Document
the exact structure: which project/assembly uses which resource file, where asset
paths are configured (pack URIs for WPF, `ms-appx://` for UWP/WinUI), and icon-size
requirements for the app manifest.

Do not infer missing files solely from a naming pattern. Clearly label optional or
recommended files that do not currently exist. Never reproduce actual signing
certificates or their passwords — reference them by name/location only.

## 6a. Registry & installer footprint minimalism (standing check, all projects)

Check whether the app writes only the registry keys it actually needs, and whether
the installer (MSI/MSIX) or app package manifest requests only the capabilities it
actually uses — an over-broad capability declaration or orphaned registry key is a
common review blocker and a real attack-surface increase, not just a style nit.

- List every registry key the app reads or writes, and for each, find the source code
  that actually uses it.
- List every capability declared in the app package manifest (e.g.
  `broadFileSystemAccess`, `internetClient`) and confirm real usage in source.
- Flag any registry key or capability present with no corresponding usage as
  **remove or justify** — do not silently drop it yourself unless implementation
  changes were approved.
- Note the app's data storage location (isolated storage, `%LocalAppData%`, or
  registry) since this affects both review and user-visible data-persistence
  behavior.

## 7. Accessibility documentation requirements

Explain applicable semantics and accessibility behavior: UI Automation properties
(`AutomationProperties.Name`, control types), Narrator support, High Contrast theme
support, keyboard navigation and access-key (mnemonic) behavior, focus order and
visualization, and any accessibility-testing findings (Accessibility Insights for
Windows).

Flag accessibility problems separately. Do not silently fix behavior unless
implementation changes beyond documentation were approved.

## 8. Security and privacy documentation requirements

Document applicable behavior: registry usage, isolated storage/app-data folder
contents, the app manifest's `requestedExecutionLevel` (UAC behavior), code-signing
certificate and Authenticode status, Windows Defender SmartScreen reputation
considerations, network calls, and credential storage (Windows Credential Manager vs.
plaintext config).

Never place real secrets, API keys, or signing-certificate material in source
comments, examples, README content, screenshots, or output logs.

## 8a. Third-party dependency license audit (standing check, all projects)

Audit every external NuGet dependency for whether its actual license permits the
project's real use case, on every project going forward, not just ones headed for
public distribution. A package can read as "just a small utility" and still require a
paid commercial license — that's not always obvious from its marketing copy, so check
the primary source:

- List every NuGet dependency actually in use, with its version.
- For each, find its real license from the package's `.nuspec` `license`/
  `licenseUrl` metadata or its own repository — not a marketing page.
- If a license would require payment, registration, or open-sourcing the project's
  own code for its actual use case: **do not just note it and move on — build a free
  custom replacement** for the specific slice of functionality actually used, and
  remove the paid-license dependency entirely.
- Document the audit result in the project's README — a table of every dependency,
  its license, and a confirmation of commercial-use compatibility. Leave this note
  even when everything checks out clean.
- Re-run this audit whenever a new dependency is added — it's not a one-time pass.

## 9. Distribution requirements

Explain how to: prepare for Microsoft Store submission vs. a signed MSI/MSIX
installer or ClickOnce publish, separate personal/demo content from reusable code if
the project may become a template, centralize configurable settings, document
supported Windows versions and architectures, maintain a versioning strategy
(assembly/file/package version), and audit third-party dependency and asset licenses.

Do not provide definitive legal advice. Identify items that require a rights, license,
or Store-policy check.

## 10. Behavior-preservation rule

Unless functional changes are explicitly authorized: preserve rendered UI and
behavior, namespace/assembly name, registry key names, public API surface, app
manifest capabilities, and accessibility state management. Do not add dependencies.
Do not reformat unrelated code. Documentation-only changes should produce no
intentional runtime differences.

## 11. Validation requirements (after approval and implementation)

1. Confirm the project builds cleanly (no new warnings/errors introduced).
2. Confirm source comments do not break compilation.
3. Compare functional source before and after with comments removed where practical.
4. Check resource-file references resolve (`.resx`/pack URIs).
5. Confirm accessibility automation IDs still match what tests reference.
6. Confirm no secret, certificate, or personal data was newly exposed.
7. Check README links, headings, tables, code fences, and Mermaid syntax.
8. Confirm the registry/installer footprint audit per section 6a — no unused
   registry key or capability left unflagged.
9. Confirm every NuGet dependency's license permits the project's actual use, per
   section 8a.
10. Confirm `STYLEGUIDE.md`, `CHANGELOG.md`, `COMPONENTS.md`, `SECURITYCHECK.md`,
    `DASHBOARD.md`, `Repo-Hygiene-Check.md`, and `Ask-Other-Agent-to-Review.md` exist,
    cross-reference correctly, and reflect the current source rather than stale
    claims.

## 12. Deliverables

After the preview is approved, provide: documented primary source files, updated
`README.md`, the seven companion files above (created if missing, updated if
present), this reusable documentation standard adapted to the project if appropriate,
an optional `LICENSE` (only after approval), a concise summary of what was
documented, validation results, and a recommended next step (build/package,
Microsoft Store submission, or signed installer distribution).

If the project is already connected to Git, preserve its history and unrelated
changes. Do not commit, push, publish, submit for review, or distribute unless
explicitly requested.

## Short version

If the full standard above is already established in the conversation and a quick
re-run is wanted, this is equivalent:

> Document this Windows project using our documentation-first standard. Inspect the
> real source and resources, preview the documentation plan, and wait for approval.
> Then add native comments to every primary source file, expand README.md into a
> complete architecture/customization/distribution guide, create/update
> STYLEGUIDE.md, CHANGELOG.md, COMPONENTS.md, SECURITYCHECK.md, DASHBOARD.md,
> Repo-Hygiene-Check.md, and Ask-Other-Agent-to-Review.md, include the exact
> resource-file tree, a registry/installer footprint audit, accessibility and privacy
> behavior, testing and troubleshooting, and Microsoft Store vs. installer
> distribution guidance. Preserve functionality and validate everything before
> delivering. Never expose or remember secrets.
