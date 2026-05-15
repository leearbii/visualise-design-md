# Implementation Plan

## Step-by-Step Plan

1. Create the project skeleton.
   - Add `README.md`.
   - Add `docs/PRD.md`.
   - Add this implementation plan.

2. Build `design-viewer.html`.
   - Use one static HTML file.
   - Include embedded CSS and JavaScript.
   - Avoid build tools and package installation.

3. Add local file loading.
   - Support drag and drop.
   - Support file picker selection.
   - Reject non-Markdown files with a clear message.

4. Parse Markdown locally.
   - Extract headings, checklists, tables, code blocks, paragraphs, lists, and blockquotes.
   - Keep the parser pragmatic and scoped to design document review.

5. Render the review interface.
   - Use the Studio Review layout: top command bar, compact status rail, document canvas, and right inspector tabs.
   - Show a heading outline in the inspector.
   - Show rendered Markdown.
   - Show raw Markdown as a secondary mode behind a `Rendered / Raw` toggle in the document canvas.
   - Show highlighted design sections.

6. Add verification helpers.
   - Count checked and unchecked checklist items.
   - Flag empty sections.
   - Flag duplicate headings.
   - Display issue severity as `info`, `warning`, and `error` with distinct colors.
   - Summarize tables.
   - Render color swatches for color values in tables.
   - Render component previews from `Components` sections.
   - Add search that highlights matching rendered sections.

7. Add sample data and manual QA.
   - Create a sample `examples/design.md`.
   - Base the sample on the lab portfolio design document structure.
   - Test loading, rendering, outline navigation, checklist counts, tables, and issue detection.

8. Prepare for GitHub and Vercel.
   - Keep the repo static.
   - Add clear Vercel-focused usage instructions.
   - Confirm the app works from direct file open and from a static server.

## Version One Deliverables

- `design-viewer.html`
- `README.md`
- `docs/PRD.md`
- `docs/implementation-plan.md`
- `examples/design.md`

## Later Deliverables

- `design-viewer.config.json`
- HTML/JSON verification report export
- Multi-file support
- Document comparison mode
