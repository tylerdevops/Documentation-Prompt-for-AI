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

## 2026-08-20

- Scaffolded the project: moved `DOCUMENTATION-PROMPT.md` into
  `templates/`, added a root `README.md`, initialized git.
