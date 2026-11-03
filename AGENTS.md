# Repository Guidelines

## Project Structure & Module Organization

This repository currently contains `SPEC.md`, the implementation and acceptance specification for the VERTI static website. No source code, assets, package manifest, or test framework exists yet. Read `SPEC.md` before implementation; keep scope limited to the supplied header and About VERTI hero.

Deliver semantic HTML, source CSS, compiled CSS, local assets, and a `README.md`. Group images and licensed fonts under clearly named asset directories. Record design measurements and token mappings in `docs/design-measurements.md`, and screenshot comparisons and resolutions in `docs/visual-review.md`.

## Build, Test, and Development Commands

No build, development, or test commands are configured yet. Use the simplest practical Tailwind CSS 4 compilation workflow and document exact installation, compilation, and local viewing commands in `README.md` when tooling is introduced. Do not describe unconfigured commands such as `npm test` as available.

Build-time tooling is allowed; application JavaScript, React, runtime component libraries, and backend services are outside scope.

## General Working Rules

- Keep the workflow focused on local development and viewing through localhost. Do not add a build requirement as part of these general rules.
- Keep changes focused on the requested task. Preserve existing conventions and avoid unrelated refactoring or new dependencies unless needed to complete the task.
- Format every changed file before finishing. Use the project's formatter configuration when available; otherwise, follow the file's existing formatting and check it manually. Avoid reformatting unrelated files.
- After HTML or CSS changes, validate syntax using available project tools and fix errors introduced by the changes. If no validator is available, manually inspect the changed markup and styles and report that limitation. Do not install validation tools without a task-related need.
- Use semantic HTML, appropriate image alternatives, labels for form controls when present, and clearly visible keyboard focus. Preserve native keyboard behavior.
- Formatting and HTML/CSS syntax validation are allowed and are separate from the automated test suite and cross-browser campaign excluded below.
- At completion, state what changed, which checks actually ran, and any checks that could not be performed. Never claim a check passed unless it was performed.

## Coding Style & Naming Conventions

Use semantic HTML and Tailwind utilities. Define named design tokens through Tailwind 4’s CSS-first theme configuration; prefer token-backed utilities and `@apply` for reusable CSS where practical. Use descriptive, consistent names for assets and tokens.

Follow existing indentation once source files exist, and keep formatting consistent. No formatter or linter is currently configured. Use a root font size of `100%`, convert typography using 16px = 1rem, and change typography discretely at the specified breakpoints.

## Verification Guidelines

Before implementation, inspect all six Figma reference frames and record their measurement matrix. Review screenshot overlays at 360, 768, 992, 1280, 1440, and 1920px; also inspect below-the-fold mobile content, intermediate widths, and overflow.

Per `SPEC.md`, do not run an automated test suite or an AI-led cross-browser campaign. Manual browser acceptance belongs to the user. Document actual visual-review coverage and provide a manual checklist in the README.

## Commit & Pull Request Guidelines

History contains short descriptive subjects, including `docs: clarify Figma measurements, hero sizing, and interaction states`; no strict convention is established. Prefer concise, imperative subjects with a scope prefix where useful.

Pull requests should describe changes, reference relevant specification sections or issues, and include screenshots for visual changes. State verification coverage and unresolved discrepancies accurately. Record explicit user approval for additional deviations from Figma in `docs/visual-review.md`.
