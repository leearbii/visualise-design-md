# Visualise Design MD Design Direction

## 1. Design Thesis

Visualise Design MD should feel like a modern studio review surface: warm, editorial, and focused on the document. It should not feel like an issue tracker, admin dashboard, or Jira-style board.

The rendered Markdown is the main object. Raw Markdown is useful for debugging, but it should be a secondary mode inside the same document canvas. Verification details, components, tables, checks, and outline are supporting instrumentation around that object.

## 2. Scene

A product builder is reviewing a design Markdown file on a laptop in a bright workspace before handing it to an implementation agent. They need clarity and speed, but the tool should still feel contemporary and crafted.

## 3. Visual Register

- Editorial studio tool.
- Light, warm, and calm.
- Fewer heavy borders.
- More whitespace around the document canvas.
- Top command bar instead of a permanent admin sidebar.
- Compact status rail for document stats.
- Right inspector with tabs for review details.

## 4. Color Strategy

Use warm editorial neutrals with one fresh accent and semantic severity colors.

| Token | Value | Usage |
| --- | --- | --- |
| `--bg` | `oklch(97% 0.012 78)` | Warm page base |
| `--surface` | `oklch(99% 0.006 78)` | Canvas and main surfaces |
| `--surface-muted` | `oklch(94% 0.014 78)` | Inspector backgrounds |
| `--line` | `oklch(86% 0.018 78)` | Dividers and table borders |
| `--text` | `oklch(19% 0.025 70)` | Main text |
| `--text-muted` | `oklch(48% 0.025 70)` | Secondary text |
| `--accent` | `oklch(62% 0.13 32)` | Active state, primary action |
| `--info` | `oklch(58% 0.13 235)` | Info severity |
| `--warning` | `oklch(72% 0.15 80)` | Warning severity |
| `--error` | `oklch(60% 0.18 25)` | Error severity |
| `--success` | `oklch(58% 0.12 155)` | Checked items and positive state |

Rules:

- Use accent for active state and primary actions only.
- Use severity colors with text labels.
- Keep color fills small: badges, swatches, active tabs, focus states.
- Avoid cold grey admin palettes.

## 5. Layout

### Desktop

Use the **Studio Review** structure:

```text
+-------------------------------------------------------------+
| Top command bar: title, file state, search, sample, load     |
+-------------------------------------------------------------+
| Status rail: file metadata, issues, checks, components       |
+-------------------------------------------------------------+
| Document canvas with Rendered/Raw toggle Inspector tabs      |
|                                          Outline             |
|                                          Issues              |
|                                          Checks              |
|                                          Tables              |
|                                          Components          |
|                                          Sections            |
+-------------------------------------------------------------+
```

### Inspector

Use one right-side inspector instead of multiple bottom cards.

Tabs:

- Outline
- Issues
- Checks
- Tables
- Components
- Sections

### Mobile And Narrow Screens

- Keep the same rendered/raw toggle inside the document canvas.
- Stack the inspector below the document canvas.
- Preserve the top command bar and health strip.

## 6. Typography

Use a dependency-free stack with a little more character:

```css
font-family: "Avenir Next", Avenir, ui-sans-serif, system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
```

Use mono only for raw Markdown, code, and line-like data.

Rendered document headings should be larger and more editorial than inspector labels.

## 7. Components

### File Drop Zone

- Large warm surface.
- Dashed border.
- Short, direct copy.
- Strong primary file action.

### Health Strip

- Use a compact status rail, not a large metric block.
- Keep file metadata, issues, unchecked items, components, and tables in one slim row.
- Low visual weight.
- Tabular numbers.
- No heavy card treatment.

### Inspector Tabs

- Segmented pill controls.
- Active tab uses dark fill.
- Panels switch in place.

### Component Previews

Component extraction should render mini style-guide samples:

- Buttons: primary and ghost button previews.
- Chips / pills: neutral, accent, and status examples.
- Cards: compact surface preview.
- Unknown components: generic preview card.

### Rendered Markdown

- Main canvas gets the most space.
- Headings are confident and readable.
- Tables keep borders and color swatches.
- Checklists remain semantic.

### Raw Markdown

- Raw Markdown lives behind a `Rendered / Raw` toggle in the document canvas header.
- Rendered is the default view.
- Raw view reuses the same canvas space rather than appearing as a second equal-weight panel.

## 8. Motion

- Keep transitions between 150ms and 220ms.
- Animate opacity, transform, color, and background only.
- Use motion for tab state, active controls, search highlight, and button press feedback.
- Respect `prefers-reduced-motion`.

## 9. Accessibility

- All controls must be keyboard reachable.
- File picker must have a visible label.
- Severity colors must include text labels, not color alone.
- Focus states should be visible and consistent.
- Tables should render with semantic `table`, `thead`, `tbody`, `th`, and `td` tags.

## 10. Current UI Decisions

- Studio Review layout.
- Warm light theme only.
- Top command bar.
- Compact status rail.
- Right inspector tabs.
- Rendered Markdown as primary canvas.
- Rendered/raw toggle in the document canvas.
- Search highlights matches.
- Color swatches in rendered tables.
- Component previews from `Components` sections.
