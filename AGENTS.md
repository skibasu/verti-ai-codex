# Repository Guidelines

## Project Structure & Module Organization

This repository currently contains `SPEC.md`, the implementation and acceptance specification for the VERTI static website. No source code, assets, package manifest, or test framework exists yet. Read `SPEC.md` before implementation; keep scope limited to the supplied header and About VERTI hero.

Deliver semantic HTML, source CSS, compiled CSS, local assets, and a `README.md`. Group images and licensed fonts under clearly named asset directories. Record design measurements and token mappings in `docs/design-measurements.md`, and screenshot comparisons and resolutions in `docs/visual-review.md`.

## Build, Test, and Development Commands

No build, development, or test commands are configured yet. Use the simplest practical Tailwind CSS 4 compilation workflow and document exact installation, compilation, and local viewing commands in `README.md` when tooling is introduced. Do not describe unconfigured commands such as `npm test` as available.

Build-time tooling is allowed; application JavaScript, React, runtime component libraries, and backend services are outside scope.

## Coding Style & Naming Conventions

Use semantic HTML and Tailwind utilities. Define named design tokens through Tailwind 4’s CSS-first theme configuration; prefer token-backed utilities and `@apply` for reusable CSS where practical. Use descriptive, consistent names for assets and tokens.

Follow existing indentation once source files exist, and keep formatting consistent. No formatter or linter is currently configured. Use a root font size of `100%`, convert typography using 16px = 1rem, and change typography discretely at the specified breakpoints.

## Verification Guidelines

Before implementation, inspect all six Figma reference frames and record their measurement matrix. Review screenshot overlays at 360, 768, 992, 1280, 1440, and 1920px; also inspect below-the-fold mobile content, intermediate widths, and overflow.

Per `SPEC.md`, do not run an automated test suite or an AI-led cross-browser campaign. Manual browser acceptance belongs to the user. Document actual visual-review coverage and provide a manual checklist in the README.

## Commit & Pull Request Guidelines

History contains short descriptive subjects, including `docs: clarify Figma measurements, hero sizing, and interaction states`; no strict convention is established. Prefer concise, imperative subjects with a scope prefix where useful.

Pull requests should describe changes, reference relevant specification sections or issues, and include screenshots for visual changes. State verification coverage and unresolved discrepancies accurately. Record explicit user approval for additional deviations from Figma in `docs/visual-review.md`.
