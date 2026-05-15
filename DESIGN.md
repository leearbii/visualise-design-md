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
- Compact plain-text status rail for document stats.
- Right annotation rail with three tabs for review details.
- No decorative grid or glow background.

## 4. Color Strategy

Use a cheerful pastel studio palette with one coral primary accent and soft semantic colors.

| Token | Value | Usage |
| --- | --- | --- |
| `--bg` | `oklch(97% 0.022 305)` | Pastel lavender page base |
| `--surface` | `oklch(99% 0.01 310)` | Canvas and main surfaces |
| `--surface-muted` | `oklch(94.5% 0.025 292)` | Inspector backgrounds |
| `--line` | `oklch(86% 0.028 292)` | Dividers and table borders |
| `--text` | `oklch(20% 0.035 282)` | Main text |
| `--text-muted` | `oklch(47% 0.035 286)` | Secondary text |
| `--accent` | `oklch(64% 0.16 18)` | Active state, primary action |
| `--info` | `oklch(68% 0.105 225)` | Info severity |
| `--warning` | `oklch(82% 0.13 88)` | Warning severity |
| `--error` | `oklch(68% 0.135 18)` | Error severity |
| `--success` | `oklch(72% 0.12 155)` | Checked items and positive state |

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
| Top command bar: title, file state, sample, load             |
+-------------------------------------------------------------+
| Status rail: file metadata, issues, checks, components       |
+-------------------------------------------------------------+
| Document canvas with Rendered/Raw toggle Inspector tabs      |
|                                          Review              |
|                                          Components          |
|                                          Outline             |
+-------------------------------------------------------------+
```

### Inspector

Use one right-side annotation rail instead of multiple bottom cards.

Tabs:

- Review: issues, unchecked items, tables, and detected sections
- Components: component previews
- Outline

### Mobile And Narrow Screens

- Keep the same rendered/raw toggle inside the document canvas.
- Stack the inspector below the document canvas.
- Preserve the top command bar and compact status rail.

## 6. Typography

Use separate typography for the app shell and the rendered document.

App shell:

```css
font-family: "Geist", "Satoshi", "Helvetica Neue", ui-sans-serif, system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
```

Rendered document body:

```css
font-family: "Iowan Old Style", "New York", Charter, "Bitstream Charter", Georgia, ui-serif, serif;
```

Rendered document headings use the app sans stack for structure. Body copy uses the reader stack so the document feels like a designed page instead of a code preview.

Use mono only for raw Markdown, code, and line-like data.

Rendered document headings should be larger and more editorial than inspector labels.

## 7. Components

### Empty Document Canvas

- The document canvas is the pre-load drag target.
- Use a centered empty state with a small animated SVG.
- Keep copy short, warm, and specific to `design.md`.
- Keep file actions in the header so the empty state does not become a second hero.

### Health Strip

- Use a compact plain-text status rail, not a metric block.
- Keep file metadata, issues, unchecked items, components, and tables in one slim row.
- Low visual weight.
- Tabular numbers.
- No pills unless severity needs attention.

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
- Body copy uses the reader/editorial stack.
- Tables keep borders and color swatches.
- Checklists remain semantic.

### Raw Markdown

- Raw Markdown lives behind a `Rendered / Raw` toggle in the document canvas header.
- Rendered is the default view.
- Raw view reuses the same canvas space rather than appearing as a second equal-weight panel.

## 8. Motion

- Keep transitions between 150ms and 220ms.
- Animate opacity, transform, color, and background only.
- Use motion for tab state, active controls, empty-state illustration, and button press feedback.
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
- Rounded command shelf without a custom search control.
- Compact plain-text status rail.
- Right annotation rail with `Review`, `Components`, and `Outline`.
- Rendered Markdown as primary canvas.
- Rendered/raw toggle in the document canvas.
- Search highlights matches.
- Color swatches in rendered tables.
- Component previews from `Components` sections.
