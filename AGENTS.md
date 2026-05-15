# Agent Instructions

## Project

Visualise Design MD is a local-first static browser tool for reviewing `design.md` files. It helps users inspect rendered Markdown, raw Markdown, headings, checklists, tables, design sections, and verification issues without uploading files or installing dependencies.

## Source Of Truth

Read these files before making meaningful product or UI changes:

- `PRODUCT.md`: product intent, users, principles, and anti-references.
- `DESIGN.md`: visual direction, layout rules, tokens, and component behavior.
- `docs/PRD.md`: requirements, user stories, scope, and acceptance criteria.
- `docs/implementation-plan.md`: current build plan.
- `examples/design.md`: sample fixture for manual verification.

## Version One Constraints

- Keep the app static and browser-only.
- Keep version one centered on `design-viewer.html`.
- Do not add Node, npm, bundlers, frameworks, package managers, or build steps unless the project direction changes explicitly.
- Do not upload or persist user file contents.
- Avoid external CDN dependencies.
- Target Vercel static deployment only.
- Preserve direct browser opening as a supported workflow.

## Product Rules

- The first screen is the working tool, not a landing page.
- Prioritize document review speed and clarity over decoration.
- Keep local file loading obvious and always available.
- Rendered Markdown and raw Markdown must remain comparable.
- Raw Markdown should be a secondary mode behind a `Rendered / Raw` toggle in the document canvas, not a second equal-weight panel.
- Search highlights matches instead of hiding non-matching sections.
- Use the Studio Review layout: top command bar, compact plain-text status rail, document canvas, and right annotation rail.

## Verification Rules

Version one should support:

- Drag/drop and file picker for `.md` and `.markdown`.
- Heading outline.
- Checklist extraction and unchecked count.
- Markdown table rendering and table summaries.
- Color swatches for color values inside rendered tables.
- Component extraction from `Components` sections.
- Empty section detection.
- Duplicate heading detection.
- Design section detection.
- Issue severity levels: `info`, `warning`, and `error`.

When changing parser or rendering behavior, verify against:

- Built-in sample button in `design-viewer.html`.
- `examples/design.md`.
- `http://127.0.0.1:8000/design-viewer.html?sample=1` when the local server is running.

At minimum, run a JavaScript syntax check on the embedded script after edits.

## Design Rules

- Follow `DESIGN.md`.
- Use a warm, minimal, modern studio-review interface.
- Use light theme by default.
- Use semantic colors for severity, with text labels so color is not the only signal.
- Keep the rendered Markdown canvas as the primary visual object.
- Keep inspector tabs limited to `Review`, `Components`, and `Outline` unless there is a clear reason to expand.
- Avoid decorative grid/glow backgrounds.
- Avoid permanent admin sidebars, Jira-style issue-board layouts, decorative dashboards, generic SaaS card grids, heavy dark terminal aesthetics, and marketing hero layouts.

## Code Rules

- Prefer plain HTML, CSS, and JavaScript.
- Keep parsing logic readable and grouped by purpose.
- Escape user-provided Markdown content before inserting it into HTML.
- Keep accessibility basics intact: labels, keyboard-reachable controls, visible focus states, semantic tables, and readable contrast.
- Do not introduce unrelated refactors while implementing a focused feature.

## Deployment

The project should remain deployable to Vercel as a static site with no build command.
