# Visualise Design MD

A static browser tool for reviewing `design.md` files locally.

The first version is planned as a single-file app, `design-viewer.html`, with no install step and no server requirement. Users can open the file directly in a browser, drag in a Markdown design document, and inspect rendered sections, checklists, tables, detected issues, and raw Markdown side by side.

## Project Status

Planning started in `docs/PRD.md`.

## Intended Use

1. Open `design-viewer.html` in a browser.
2. Drag and drop a `design.md` file or select one from disk.
3. Review the rendered design content, verification summary, extracted tables, detected issues, and raw Markdown.
4. Fix the source `design.md`.
5. Reload or drag the file again to verify.

## Deployment

The app should work as static HTML. It can later be pushed to GitHub and deployed to Vercel as a static site without a build step.
