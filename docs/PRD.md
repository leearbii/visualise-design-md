# Visualise Design MD PRD

## 1. Executive Summary

We are building **Visualise Design MD**, a static browser tool that helps product builders, designers, and engineers review `design.md` files without installing dependencies or uploading private content. Users will open `design-viewer.html`, drag in a Markdown design document, and immediately see a structured review workspace with rendered content, a heading outline, checklist verification, table previews, issue detection, browser-native search, and raw Markdown for comparison. The goal is to make design documents easier to inspect before implementation, reducing missed requirements, unchecked acceptance criteria, and ambiguous handoff quality.

## 2. Problem Statement

### Who Has This Problem?

Teams that use Markdown design documents as the source of truth for product design, implementation planning, or AI-assisted coding workflows.

Primary affected roles:

- Product managers writing implementation-ready product/design specs.
- Designers documenting screens, components, states, interactions, and design tokens.
- Engineers reviewing whether a design document is complete enough to build from.
- Solo builders using `design.md` files as a lightweight alternative to heavier design tooling.

### What Is The Problem?

Markdown is easy to write but difficult to audit consistently. As design documents grow, important implementation details become buried across sections, unchecked tasks are easy to miss, tables are hard to scan in raw form, and duplicate or empty headings can create false confidence that a topic has been covered.

### Why Is It Painful?

- Reviewers must manually scan long Markdown files to find gaps.
- Checklists and acceptance criteria can remain incomplete without visibility.
- Raw Markdown tables are difficult to read during review.
- AI/code-agent workflows often depend on document structure, so weak headings or missing sections reduce implementation quality.
- Teams need local/private review because design docs may contain unreleased product details.

### Evidence And Assumptions

Current evidence is based on the user's stated workflow:

- The tool is intended for reviewing `design.md` files before fixing and reloading them.
- The requested workflow requires local parsing, rendered review, raw comparison, checklist summaries, and issue flags.
- The project should be shareable, GitHub-ready, and deployable to Vercel later.

Assumption: the first users are internal builders/reviewers who value speed, privacy, and portability more than full Markdown-spec completeness.

## 3. Target Users & Personas

### Primary Persona: Product Builder

- **Role:** Founder, PM, or solo builder preparing a design Markdown file for implementation.
- **Goals:** Quickly see whether the design document is complete, structured, and ready to build from.
- **Pain points:** Does not want to install tooling; needs a quick visual review loop; may use AI coding tools that depend on clear specs.
- **Current behavior:** Opens raw Markdown in an editor, manually scans headings/checklists/tables, fixes the file, and repeats.

### Secondary Persona: Design Reviewer

- **Role:** Designer, design engineer, or frontend reviewer.
- **Goals:** Confirm screens, components, states, interactions, tokens, and accessibility notes are documented.
- **Pain points:** Design details are scattered; raw Markdown makes visual hierarchy hard to inspect.
- **Current behavior:** Reviews the Markdown file alongside Figma or product context and leaves comments manually.

### Secondary Persona: Implementation Engineer

- **Role:** Engineer using a `design.md` document as build input.
- **Goals:** Understand scope, identify incomplete acceptance criteria, and avoid starting from an under-specified design.
- **Pain points:** Missing sections cause rework; unchecked tasks can be interpreted as done; tables are hard to parse quickly.
- **Current behavior:** Reads raw Markdown, asks clarifying questions, or starts implementation with partial context.

### Jobs To Be Done

- When I receive a `design.md`, I want to inspect its structure quickly so I can decide whether it is ready for implementation.
- When I review acceptance criteria, I want unchecked items surfaced automatically so I do not miss incomplete requirements.
- When I see tables in Markdown, I want them rendered cleanly so I can understand design tokens, screen specs, and data requirements.
- When I refine a design doc, I want to compare rendered output with raw Markdown so I can fix formatting and content gaps.

## 4. Strategic Context

### Product Goal

Create a lightweight local-first review tool for design Markdown files that can later become a static GitHub/Vercel project.

### Why Now?

The team is establishing a workflow around `design.md` files and wants a review layer before pushing the project to GitHub and deploying to Vercel. Starting with a static single-file tool keeps the first release small, portable, and easy to validate.

### Business Or Workflow Value

- Improves design document quality before implementation.
- Reduces review time by making document issues visible.
- Supports local/private review with no upload step.
- Creates a foundation for later schema validation and report export.

### Competitive And Alternative Approaches

Alternatives include Markdown previewers, editor plugins, GitHub rendering, static documentation sites, and full design systems. These are useful but do not focus on design-handoff verification. Visualise Design MD is intentionally narrower: it renders Markdown while extracting review-specific signals like unchecked criteria, expected sections, duplicate headings, and table summaries.

## 5. Solution Overview

Visualise Design MD will be delivered first as a single static file: `design-viewer.html`.

The user opens the file in a browser, drops or selects a `.md` file, and the tool parses the content locally. The interface shows a review dashboard with document stats, detected issues, checklist status, extracted tables, a navigation outline, rendered Markdown, and raw Markdown side by side.

### Core Experience

1. User opens `design-viewer.html`.
2. User drags in or selects a `design.md` file.
3. Tool reads the file locally with browser APIs.
4. Tool parses headings, sections, checklists, tables, and common Markdown patterns.
5. Tool displays:
   - Document summary.
   - Issue summary.
   - Heading navigation.
   - Rendered design document.
   - Raw Markdown toggle.
   - Checklist and table review panels.
6. User fixes the original Markdown file outside the tool.
7. User reloads or drops the file again to verify improvements.

### Key Features

- Static browser app with no install step.
- Drag/drop and file picker input.
- Local Markdown parsing.
- Rendered Markdown preview.
- Raw Markdown view behind a `Rendered / Raw` toggle.
- Clickable heading outline.
- Highlighted design sections.
- Checklist extraction and status counts.
- Markdown table extraction and clean rendering.
- Empty-section detection.
- Duplicate-heading detection.
- Issue severity levels: `info`, `warning`, and `error`, each represented with distinct colors.
- Search/filter across extracted review items.
- Sample `examples/design.md` based on the structure of the user's lab portfolio design document.

## 6. Success Metrics

### Primary Metric

**Design document review completion time**

- Target for version one: a reviewer can inspect structure, checklist status, tables, and issues for a typical `design.md` in under 3 minutes.

### Secondary Metrics

- **Detection usefulness:** Users can identify unchecked checklist items without manually scanning the full document.
- **Document coverage:** Users can confirm whether key design sections exist.
- **Portability:** Tool works by opening `design-viewer.html` directly in a modern browser.
- **Deployment readiness:** Tool can be served as a static Vercel site without build configuration.

### Guardrail Metrics

- No file content leaves the user's browser.
- No package install or build step is required for version one.
- The interface remains usable on common laptop and desktop viewports.
- Large documents should remain responsive enough for review.

## 7. User Stories & Requirements

### Epic Hypothesis

We believe that a local static viewer for `design.md` files will improve design handoff quality because reviewers can quickly see structure, incomplete checklist items, tables, and document issues before implementation begins. We will validate this by confirming that users can load a file, review key verification signals, and identify obvious gaps without reading the entire raw Markdown manually.

### Story 1: Load A Markdown File

As a reviewer, I want to drag/drop or select a `.md` file so I can inspect it without installing tooling.

Acceptance criteria:

- [ ] The document canvas provides a visible empty state and accepts drag/drop.
- [ ] The page provides a file picker.
- [ ] The tool accepts `.md` and `.markdown` files.
- [ ] The tool rejects unsupported file types with a clear message.
- [ ] File content is read locally in the browser.

### Story 2: View Rendered And Raw Content

As a reviewer, I want to switch between rendered Markdown and raw Markdown so I can compare the document's meaning with the source formatting without splitting attention by default.

Acceptance criteria:

- [ ] Rendered output shows headings, paragraphs, lists, links, inline code, code blocks, blockquotes, checklists, and tables.
- [ ] Raw Markdown is available through a `Rendered / Raw` toggle in the document canvas.
- [ ] Rendered is the default view.
- [ ] Rendered and raw views remain readable without horizontal overflow.

### Story 3: Navigate The Document Outline

As a reviewer, I want a heading outline so I can jump to important sections quickly.

Acceptance criteria:

- [ ] The tool extracts all Markdown headings.
- [ ] The outline preserves heading hierarchy visually.
- [ ] Clicking an outline item scrolls to the rendered section.
- [ ] Duplicate heading names are flagged in the issue panel.

### Story 4: Review Checklist Status

As a reviewer, I want checklist items summarized so I can see what remains incomplete.

Acceptance criteria:

- [ ] The tool detects checked checklist items.
- [ ] The tool detects unchecked checklist items.
- [ ] The summary shows checked, unchecked, and total counts.
- [ ] Unchecked items appear in a review panel.
- [ ] Checklist items retain enough surrounding context to understand where they came from.

### Story 5: Inspect Tables

As a reviewer, I want Markdown tables rendered cleanly so I can inspect tokens, screen matrices, and acceptance criteria.

Acceptance criteria:

- [ ] The tool detects basic Markdown pipe tables.
- [ ] Tables render as HTML tables in the document view.
- [ ] The table summary shows total table count.
- [ ] Each detected table reports row and column counts.

### Story 6: Detect Document Issues

As a reviewer, I want obvious structural issues flagged so I can improve the source document.

Acceptance criteria:

- [ ] Empty sections are flagged.
- [ ] Duplicate headings are flagged.
- [ ] Missing expected sections can be supported later through configuration.
- [ ] The issue panel supports `info`, `warning`, and `error` severity levels.
- [ ] Each severity has a distinct visual color treatment.

### Story 7: Browser-Native Search

As a reviewer, I want rendered and raw content to remain searchable with browser find so I can avoid learning a custom search control.

Acceptance criteria:

- [ ] No custom search input is shown in the app chrome.
- [ ] Rendered Markdown remains real DOM text, not canvas or images.
- [ ] Raw Markdown mode remains selectable so browser find can inspect source text.
- [ ] Search has no network dependency.

### Story 8: Use A Realistic Sample Document

As a new user, I want a sample design Markdown file so I can understand what the tool detects before loading my own document.

Acceptance criteria:

- [ ] The repo includes `examples/design.md`.
- [ ] The sample is based on the structure of the lab portfolio design document.
- [ ] The sample includes headings, checklists, tables, highlighted design sections, and at least one issue for verification.

## 8. Out Of Scope

Not included in version one:

- Editing Markdown inside the tool.
- Saving changes back to disk.
- Cloud sync, accounts, collaboration, or comments.
- Server-side Markdown processing.
- Full CommonMark compliance.
- Multi-file compare mode.
- Report export.
- Required-section schema configuration.
- GitHub Pages deployment documentation.
- NPM package, CLI, or build pipeline.

Future consideration:

- Multiple-file loading.
- Side-by-side document comparison.
- HTML and JSON verification report export.
- Optional `design-viewer.config.json` schema.
- Required section validation.
- More complete Markdown parsing if needed.

## 9. Dependencies & Risks

### Technical Dependencies

- Browser File API.
- Modern JavaScript support.
- CSS responsive layout.
- Static hosting compatibility for Vercel.

### External Dependencies

- None for version one.

### Risks And Mitigations

| Risk | Impact | Mitigation |
| --- | --- | --- |
| Handwritten Markdown parser misses edge cases | Some documents render imperfectly | Keep parser scoped to design docs; document known limitations; add examples for expected syntax |
| Large Markdown files slow the page | Poor review experience | Avoid expensive repeated parsing; cap heavy operations if needed |
| Table parsing breaks on escaped pipes or complex multiline tables | Incorrect table rendering | Support simple pipe tables first; preserve raw Markdown for fallback comparison |
| Supporting review panels compete with the document | Poor review focus | Keep rendered content primary; place raw Markdown behind a toggle and review details in a compact annotation rail |
| Users expect editing/saving | Misaligned expectations | Make version-one scope clear in README and UI copy |

## 10. Open Questions

Resolved decisions:

- Version one will include `examples/design.md`.
- The sample file will use the user's lab portfolio `DESIGN.md` as the structural reference.
- Rendered/raw comparison will use a toggle inside the document canvas instead of permanent side-by-side panels.
- Initial deployment documentation will target Vercel only.
- Issue severity will use `info`, `warning`, and `error`, each with distinct colors.
- Search will highlight matching rendered sections in version one instead of hiding non-matching sections.

Deferred decisions:

- Default expected sections for future schema validation will be decided after reviewing the first version in use.

## 11. Release Plan

### Milestone 1: Static Review MVP

Deliverables:

- `design-viewer.html`
- `examples/design.md`
- Updated `README.md`

Capabilities:

- File load.
- Markdown render.
- Outline.
- Checklist summary.
- Table rendering.
- Empty and duplicate heading warnings.
- `info`, `warning`, and `error` issue severity colors.
- Rendered/raw document toggle.

### Milestone 2: Verification Polish

Deliverables:

- Browser-native search behavior.
- Better issue grouping.
- More robust responsive behavior.
- Manual QA checklist.

### Milestone 3: Future Schema Layer

Deliverables:

- Optional `design-viewer.config.json`.
- Required-section validation.
- Exportable verification report.

## 12. Implementation Notes

- Keep version one as plain HTML, CSS, and JavaScript.
- Avoid external CDN dependencies so the file remains portable.
- Use semantic HTML for rendered content and accessible controls.
- Keep parsing functions separated inside the single file for readability.
- Prefer clear issue data structures so later schema validation can reuse them.
- Do not upload or persist file contents.
