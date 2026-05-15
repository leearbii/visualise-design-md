# Visualise Design MD

A static browser tool for reviewing `design.md` files locally.

The first version is a single-file app, `design-viewer.html`, with no install step and no build step. Users can open the file directly in a browser, drag in a Markdown design document, and inspect rendered sections, checklists, tables, detected issues, and raw Markdown side by side.

## Intended Use

1. Open `design-viewer.html` in a browser.
2. Drag and drop a `design.md` file or select one from disk.
3. Review the rendered design content, verification summary, extracted tables, detected issues, and raw Markdown.
4. Fix the source `design.md`.
5. Reload or drag the file again to verify.

## Features

- Local `.md` and `.markdown` file loading.
- Rendered Markdown preview.
- Raw Markdown view behind a `Rendered / Raw` toggle.
- Heading outline.
- Checklist summary with unchecked item count.
- Markdown table extraction and clean HTML table rendering.
- Color swatches for color values inside rendered tables.
- Component extraction from `Components` sections.
- Mini component previews for buttons, chips, cards, and fallback components.
- Empty section detection.
- Duplicate heading detection.
- Issue severity labels: `info`, `warning`, and `error`.
- Search that highlights matching content.
- Single document canvas with rendered/raw toggle.
- Built-in sample based on `examples/design.md`.

## Files

- `design-viewer.html`: static app.
- `examples/design.md`: sample design document for testing.
- `docs/PRD.md`: product requirements.
- `docs/implementation-plan.md`: build plan.
- `PRODUCT.md`: product context.
- `DESIGN.md`: design direction.

## Deployment

The app works as static HTML. It can be pushed to GitHub and deployed to Vercel as a static site without a build step.

For Vercel, use the repository root as the project root and leave the build command empty.
