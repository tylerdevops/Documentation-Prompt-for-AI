---
name: documentthisMacOS
description: >
  Apply your team's documentation-first standard to a native macOS project (Swift/
  SwiftUI, Objective-C/AppKit, or a cross-platform framework targeting Mac). Use
  whenever you invoke /documentthisMacOS, or ask to "document this macOS app",
  "document this Mac project", or similar. Produces native source comments, a complete
  README, companion docs (style guide, changelog, components guide, security checklist,
  dashboard, repo hygiene check, second-opinion review prompt), an exact asset-catalog
  map, accessibility/security/entitlements notes, a testing checklist, and distribution
  guidance (Mac App Store vs. notarized direct distribution) — always preceded by an
  inspection + preview step that requires explicit approval before anything is written.
---

# Document This — macOS

This skill packages your team's standing documentation prompt, adapted for native
macOS projects, so it can be invoked with `/documentthisMacOS` instead of pasting a
prompt into every project.

Act as a senior macOS engineer, technical writer, accessibility reviewer, and release
specialist. Treat comprehensive source documentation as a standing requirement for
this project.

If you have persistent memory available, remember (once, not per-project) that your
team prefers macOS projects to include clearly organized native source comments, a
complete README, a style guide, a changelog, a components guide, a security checklist,
a documentation dashboard, a repo hygiene check, a second-opinion review prompt, an
exact asset-catalog map, customization instructions, accessibility notes, testing
guidance, an entitlements/sandbox audit, and distribution guidance. Never store project
secrets, credentials, provisioning-profile contents, or personal contact data in
memory.

## 1. Get project information

If `args` passed to the skill already answers these, use them. Otherwise ask briefly
(one message, not one question at a time) for whatever is missing — don't block on
fields that are obvious from the project itself:

- Project name and bundle identifier
- Project purpose (menu bar utility / productivity app / developer tool / creative
  tool / other)
- Technology (Swift/SwiftUI, Objective-C/AppKit, Catalyst, or a cross-platform
  framework)
- Minimum supported macOS version and Apple Silicon/Intel support
- Distribution target (Mac App Store / direct notarized distribution / internal-only)
- Intended audience (end user / developers / internal team)
- Possible future distribution (open source / commercial / internal tool / unknown)

## 2. Primary objective

Inspect the actual project files and produce documentation that explains how the app
works, how its targets/files connect, how to customize it safely, and how to test,
build, and distribute it. Documentation must match the current source exactly — do not
invent components, paths, dependencies, commands, entitlements, or features.

## 3. Approval gate — required before editing anything

1. Inspect the current source, project/workspace structure, targets, and schemes.
2. Identify the main components, behaviors, dependencies, data flow, asset catalogs,
   accessibility features, entitlements, Info.plist metadata, and distribution
   assumptions.
3. Show a documentation preview containing:
   - Proposed comment style
   - Example comments for each source language present
   - README table of contents
   - Exact asset-catalog tree preview
   - Files you plan to modify or add
4. Wait for explicit approval before proceeding.

Do not rewrite, reorganize, rename, minify, refactor, or change behavior during the
preview stage.

## 4. Source-comment requirements

Use valid native comment syntax per file type:

- Swift: `//`, `/* ... */`, and `///` doc comments for public API
- Objective-C/Objective-C++: `//`, `/* ... */`, `/** ... */`
- Storyboard/XIB and other XML resources: `<!-- ... -->`
- Bash/shell scripts (build phases, fastlane, CI, install/uninstall scripts): `# ...`
- Perl scripts (legacy build phases, system-administration/automation tooling): `# ...`
  for line comments, `=pod ... =cut` POD blocks for documentation of subroutines
- `Package.swift`: standard Swift comments

Bash and Perl scripts turn up in macOS projects as build-phase scripts, installer/
uninstaller helpers, and admin/automation tooling (e.g. scripts under `Scripts/`, Xcode
Run Script build phases, or a `postinstall` in a `.pkg`). Document them with the same
rigor as application source: what the script does, why it exists, what it assumes
about the environment (shell, PATH, permissions, whether it needs `sudo`), and what
breaks if it's moved or renamed.

Info.plist and `.entitlements` files are XML but many tools strip comments on save —
document their keys in the README instead of relying on inline comments surviving.

Add comments at logical boundaries, not on every obvious line. Comments should explain:
what the component/block does, why it exists, which other files or types depend on it,
important state/published properties/notifications/delegate relationships,
accessibility relationships and keyboard behavior, fallback and error handling,
privacy or security implications (entitlements, Keychain, sandbox), what a future
maintainer can safely customize, and what must stay synchronized (bundle identifier,
entitlement names, Info.plist keys) when names change.

Add a concise documented-source header to each primary source file. Use section
banners for major components and doc-comments for complex functions/types. Do not add
comments that are incorrect, redundant, speculative, or likely to go stale immediately.

## 5. README requirements

Create or expand `README.md` into a complete owner/developer guide. Include the
sections that apply:

1. Project overview
2. Features
3. Technology and third-party dependencies (SPM/CocoaPods/Carthage)
4. Architecture and file/target relationships
5. Project directory tree
6. Complete asset-catalog tree (`Assets.xcassets`: app icon set, image sets, color
   sets)
7. App launch sequence (App/Scene lifecycle or AppDelegate/SceneDelegate)
8. View/Storyboard/SwiftUI view guide
9. Design tokens and Human Interface Guidelines adherence (colors, SF Symbols, Dynamic
   Type)
10. Application/business logic behavior
11. State and persistence (UserDefaults keys, Core Data/SwiftData model, Keychain
    items)
12. Interactive feature guide (menus, toolbars, context menus, drag & drop)
13. Accessibility
14. Metadata (Info.plist keys, usage-description strings, App Store metadata)
15. Privacy and security behavior
16. Complete customization guide
17. Asset naming, dimensions (1x/2x/3x or vector, icon sizes), formats
18. Local development (Xcode version, scheme, minimum deployment target)
19. Build process (xcodebuild, fastlane, CI) and any Bash/Perl automation
    scripts involved (build-phase scripts, installer/uninstaller helpers) —
    what each does, how it's invoked, and what environment it assumes
20. Distribution (Mac App Store submission vs. notarized DMG/pkg, code-signing
    identity)
21. Testing checklist (XCTest, XCUITest)
22. macOS version/hardware support (Apple Silicon vs. Intel)
23. Troubleshooting
24. Future reusable-template preparation, if applicable
25. Licensing and third-party dependency checklist
26. Versioning and changelog recommendations (`CFBundleShortVersionString`/
    `CFBundleVersion`)

Use tables where exact mappings are helpful. Use a compact Mermaid diagram when it
materially clarifies how targets, views, state, and services connect.

## 5a. Companion documentation files

Create each of these if it does not already exist, alongside `README.md` (skip a
category within a file that doesn't apply rather than inventing content for it):

- `STYLEGUIDE.md` — Principles, Color, Typography, Imagery, Components, Voice & tone,
  Appearance (light/dark mode) switching, Accessibility — extracted from the real
  asset catalog, SF Symbols usage, and real UI copy, never invented.
- `CHANGELOG.md` — dated entries, newest first.
- `COMPONENTS.md` — a Component | Purpose/behavior | Implementation table for every
  reusable view/control actually in the source, plus any user-configurable
  preferences/settings that affect them.
- `SECURITYCHECK.md` — a checklist scoped the way a top-level security lead running a
  serious engineering team would scope it, not just entitlements-and-Keychain
  concerns. Organize it into these categories, and mark every item Pass, Needs
  review, or N/A with a one-line reason for N/A — never Pass without actually
  checking, never claim a compliance framework is satisfied without a real audit
  behind it, and never invent a control that isn't actually implemented.

  - **Threat modeling & data classification** — a threat model exists and is
    current; every type of data the app handles (user content, credentials, health/
    financial data if any) is classified by sensitivity; every entry point (network,
    IPC, file import, URL scheme/deep link) is enumerated; the adversary model is
    stated rather than left implicit.
  - **Authentication & access control** — for any app with accounts: MFA where
    applicable, least-privilege on any backend roles, session/token hardening, no
    implicit trust by network location.
  - **Data protection (at rest & in transit)** — Keychain (not `UserDefaults` or
    plaintext files) for credentials/tokens; Data Protection API / FileVault reliance
    documented for at-rest sensitive data; TLS enforced for any network calls (App
    Transport Security exceptions justified, not blanket-disabled).
  - **Secrets & credential management** — the items in the Security and privacy
    documentation requirements below (Keychain, entitlements, usage descriptions),
    plus: no API keys or provisioning-profile material committed to source.
  - **Supply chain & build integrity** — the dependency license audit (section 8a)
    plus: SPM/CocoaPods/Carthage dependencies pinned to exact versions, code-signing
    identity and notarization actually verified before distribution.
  - **Secure development lifecycle** — static analysis (Xcode's built-in analyzer or
    a third-party SAST) run before release; secrets scanning at pre-commit.
  - **Logging, monitoring & incident response** — crash reporting documented; an
    incident-response plan for a bad release (expedited-review request, rollback via
    a previous build) or a compromised dependency.
  - **Compliance & standards alignment** — name only the frameworks that actually
    apply (e.g. App Store Review Guidelines' privacy requirements, GDPR/CCPA if
    there's an EU/CA user base, HIPAA if health data is involved) and state real
    posture against each. Write "not assessed" rather than assuming compliance no one
    has audited.
  - **Network & infrastructure hardening** — the entitlements/sandbox audit (section
    6a) plus least-privilege on any backend infrastructure the app depends on.
  - **Adversarial testing** — N/A for most single-developer apps; note it explicitly
    if there's no penetration-testing cadence or disclosure channel, rather than
    omitting the category.

  Mark a whole category N/A only when the app genuinely has none of it (e.g. a
  local-only utility with no accounts, no network calls, and no backend) — say so
  explicitly rather than omitting the category.
- `DASHBOARD.md` — a documentation hub: last-updated date and author, navigation links
  to each of the project's own doc files with a one-line description, and quick links
  to real, already-configured external tools (Git remote, App Store Connect, crash
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
    coverage (build products, `DerivedData`, `.xcuserstate`, secrets-shaped files);
    commit message quality; tag/release hygiene; git history size (no accidentally
    committed binaries, provisioning profiles, or credentials).
  - **Documentation & architecture currency** — README/architecture docs vs. actual
    target/module structure (cross-file drift); Architecture Decision Records present
    for major decisions and not stale; diagrams match the current app; filename/
    naming convention consistency; internal link integrity.
  - **Dependency & supply-chain health** — SPM/CocoaPods/Carthage lockfile in sync
    with its manifest; how far outdated dependencies are; known-vulnerability scan;
    license compliance (see the dependency license audit, section 8a); an SBOM
    present or generatable.
  - **Build, CI/CD & release pipeline** — CI (Xcode Cloud, GitHub Actions, fastlane
    lane) exists and its last run is green; build reproducibility (pinned Xcode/
    Swift toolchain version); test-suite coverage trend and flaky-test detection;
    versioning/release process documented; a rollback/hotfix procedure that's
    actually been exercised.
  - **Infrastructure & deployment** — any backend/API the app depends on matches
    what's actually deployed; environment parity (dev/staging/prod endpoint
    differences documented); secrets management via Keychain or a secret manager, not
    committed plaintext; feature flags/remote config documented and not orphaned.
  - **API & interface contracts** — for an app with a backend: schema/contract
    matches actual implemented endpoints; versioning and backward-compatibility
    policy documented; a deprecation policy for old contract/app versions
    (minimum-supported-app-version enforcement).
  - **Observability & operations** — crash reporting and analytics instrumentation
    present and documented; alerting maps to real failure modes; a runbook for known
    operational scenarios (e.g. a bad build needing expedited review/rollback);
    ownership documented.
  - **Security posture** — secrets/credentials scan extended to CI logs and build
    artifacts, not just source; the entitlements/sandbox audit (section 6a); static
    analysis integrated into CI; a threat model reflecting the current app, if one is
    warranted.
  - **Reliability & scalability** — documented usage/load assumptions if there's a
    backend; known single points of failure documented with a mitigation or explicit
    acceptance; backup/restore for any user data (iCloud/local persistence), tested
    not just written; crash-free-rate or similar quality targets defined and
    monitored.
  - **Repo structure & ownership** — target/module boundaries respected (no circular
    dependencies between frameworks); a `CODEOWNERS` file (or equivalent) present and
    accurate if multiple maintainers exist; monorepo/multi-target consistency; repo
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

## 6. Asset/resource documentation requirements

Inspect the real `Assets.xcassets` catalogs, `Info.plist`, `.entitlements` files, and
localization (`.lproj`/`Localizable.strings`) folders. Document the exact structure:
which target uses which asset catalog, where the App Icon set and image/color sets
live, image-set naming (`@1x`/`@2x`/`@3x` or single vector), color-set light/dark
variants, and SF Symbols usage vs. custom artwork.

Do not infer missing files solely from a naming pattern. Clearly label optional or
recommended files that do not currently exist. Never reproduce actual provisioning
profile contents or signing-certificate material — reference them by name/location
only.

## 6a. Entitlements & sandbox minimalism (standing check, all projects)

Check whether the `.entitlements` file requests only the capabilities the app
actually uses — an over-broad entitlement (e.g. full network access, unused hardened-
runtime exceptions, unused App Sandbox capabilities) is a common review blocker and a
real attack-surface increase, not just a style nit.

- List every entitlement/capability actually declared, and for each, find the source
  code that actually exercises it (e.g. `com.apple.security.device.camera` should map
  to a real `AVCaptureSession` use).
- Flag any entitlement present with no corresponding usage in source as **remove or
  justify** — do not silently drop it yourself unless implementation changes were
  approved.
- Note the App Sandbox container path and any security-scoped bookmarks the app
  relies on, since these affect both review and user-visible file-access behavior.

## 7. Accessibility documentation requirements

Explain applicable semantics and accessibility behavior: VoiceOver labels/traits/
hints, Dynamic Type support, Full Keyboard Access, Reduce Motion and Increase Contrast
handling, focus order, and any Accessibility Inspector audit findings.

Flag accessibility problems separately. Do not silently fix behavior unless
implementation changes beyond documentation were approved.

## 8. Security and privacy documentation requirements

Document applicable behavior: Keychain usage (what's stored, access group), App
Sandbox entitlements and container access, hardened runtime exceptions, privacy
usage-description strings (e.g. `NSCameraUsageDescription`,
`NSMicrophoneUsageDescription`), network calls and any App Transport Security
exceptions, code-signing identity, and notarization/Gatekeeper status.

Never place real secrets, API keys, provisioning-profile UUIDs, or signing
certificates in source comments, examples, README content, screenshots, or output
logs.

## 8a. Third-party dependency license audit (standing check, all projects)

Audit every external dependency (Swift Package Manager, CocoaPods, Carthage) for
whether its actual license permits the project's real use case, on every project
going forward, not just ones headed for public distribution. A library can read as
"just a small utility" and still require a paid commercial license — that's not
always obvious from its marketing copy, so check the primary source:

- List every external dependency actually in use, with its version.
- For each, find its real license from the package's own LICENSE file or its
  `Package.swift`/podspec metadata — not a marketing page.
- If a license would require payment, registration, or open-sourcing the project's
  own code for its actual use case: **do not just note it and move on — build a free
  custom replacement** for the specific slice of functionality actually used, and
  remove the paid-license dependency entirely.
- Document the audit result in the project's README — a table of every dependency,
  its license, and a confirmation of commercial-use compatibility. Leave this note
  even when everything checks out clean.
- Re-run this audit whenever a new dependency is added — it's not a one-time pass.

## 9. Distribution requirements

Explain how to: prepare for Mac App Store submission (sandboxing requirements,
review-guideline compliance) vs. direct distribution (notarization, stapling,
Gatekeeper behavior), separate personal/demo content from reusable code if the project
may become a template, centralize configurable settings, document supported macOS
versions and hardware, maintain a versioning strategy
(`CFBundleShortVersionString`/`CFBundleVersion`), and audit third-party dependency and
asset licenses.

Do not provide definitive legal advice. Identify items that require a rights, license,
or App Review-guideline check.

## 10. Behavior-preservation rule

Unless functional changes are explicitly authorized: preserve rendered UI and
behavior, bundle identifier, target/scheme names, entitlements, public API surface (if
a framework/library target), Info.plist keys, and accessibility state management. Do
not add dependencies. Do not reformat unrelated code. Documentation-only changes
should produce no intentional runtime differences.

## 11. Validation requirements (after approval and implementation)

1. Confirm the project builds cleanly (no new warnings/errors introduced).
2. Confirm source comments do not break compilation.
3. Compare functional source before and after with comments removed where practical.
4. Check asset-catalog references resolve (no missing image/color set referenced in
   code).
5. Confirm accessibility identifiers/labels still match what tests reference.
6. Confirm no secret, provisioning, or personal data was newly exposed.
7. Check README links, headings, tables, code fences, and Mermaid syntax.
8. Confirm the entitlements/sandbox audit per section 6a — no unused entitlement left
   unflagged.
9. Confirm every third-party dependency's license permits the project's actual use,
   per section 8a.
10. Confirm `STYLEGUIDE.md`, `CHANGELOG.md`, `COMPONENTS.md`, `SECURITYCHECK.md`,
    `DASHBOARD.md`, `Repo-Hygiene-Check.md`, and `Ask-Other-Agent-to-Review.md` exist,
    cross-reference correctly, and reflect the current source rather than stale
    claims.

## 12. Deliverables

After the preview is approved, provide: documented primary source files, updated
`README.md`, the seven companion files above (created if missing, updated if present),
this reusable documentation standard adapted to the project if appropriate, an
optional `LICENSE` (only after approval), a concise summary of what was documented,
validation results, and a recommended next step (build/archive, TestFlight-equivalent
distribution, or notarization).

If the project is already connected to Git, preserve its history and unrelated
changes. Do not commit, push, publish, submit for review, or distribute unless
explicitly requested.

## Short version

If the full standard above is already established in the conversation and a quick
re-run is wanted, this is equivalent:

> Document this macOS project using our documentation-first standard. Inspect the real
> source, targets, and assets, preview the documentation plan, and wait for approval.
> Then add native comments to every primary source file, expand README.md into a
> complete architecture/customization/distribution guide, create/update STYLEGUIDE.md,
> CHANGELOG.md, COMPONENTS.md, SECURITYCHECK.md, DASHBOARD.md, Repo-Hygiene-Check.md,
> and Ask-Other-Agent-to-Review.md, include the exact asset-catalog tree, an
> entitlements/sandbox audit, accessibility and privacy behavior, testing and
> troubleshooting, and Mac App Store vs. notarized-distribution guidance. Preserve
> functionality and validate everything before delivering. Never expose or remember
> secrets.
