# Redesign Suggestions

## Current Diagnosis

The current interface works, but the visual language feels too formal and issue-tracker-like.

Specific weak points:

- Left sidebar plus panel grid reads like an admin dashboard.
- Many bordered boxes create a Jira/Linear issue-board feel.
- The palette is restrained but too cool and procedural.
- The first screen is useful, but not memorable.
- Component previews are helpful, but they sit inside generic review cards.
- The hierarchy gives equal weight to everything, so the document itself does not feel like the hero.

## Recommended Direction: Editorial Studio Tool

Make the viewer feel like a modern design review canvas rather than a management dashboard.

The design should feel:

- Minimal but warmer.
- More editorial than enterprise.
- More like a creative inspection table than a ticket tracker.
- Spacious, calm, and premium.
- Still practical and fast.

## Layout Changes

### Replace The Permanent Sidebar

Move away from the heavy left rail. Use:

- A slim top command bar.
- A compact document status rail.
- A floating outline drawer or compact outline column that can collapse.
- Main content as the dominant surface.

Suggested desktop structure:

```text
+-----------------------------------------------------------+
| Visualise Design MD    Search...       Load / Sample      |
+-----------------------------------------------------------+
| Status rail: file | issues | unchecked | components | tables |
+-----------------------------------------------------------+
|                                                           |
| Rendered document canvas          Raw / Checks / Tables    |
| large editorial surface           segmented side panel     |
|                                                           |
+-----------------------------------------------------------+
```

### Make Rendered Content The Hero

The rendered document should feel like the primary object:

- Larger canvas.
- Softer page-like surface.
- Better heading rhythm.
- More whitespace around the Markdown.
- Raw Markdown becomes a secondary mode inside the document canvas. Extracted review items become supporting inspector panels.

### Use Segmented Panels Instead Of Many Cards

Instead of separate bottom cards for unchecked items, tables, components, and sections:

- Use one right-side inspector panel.
- Add tabs: `Issues`, `Checks`, `Tables`, `Components`, `Sections`.
- Keep the inspector compact and contextual.

This reduces visual noise and makes the tool feel more intentional.

## Visual Style

### Palette

Switch from cool admin neutrals to warm editorial neutrals with one fresh accent.

Suggested tokens:

| Token | Value | Usage |
| --- | --- | --- |
| Background | `oklch(97% 0.012 78)` | Warm page base |
| Canvas | `oklch(99% 0.006 78)` | Rendered document surface |
| Ink | `oklch(19% 0.025 70)` | Main text |
| Muted | `oklch(48% 0.025 70)` | Secondary text |
| Line | `oklch(86% 0.018 78)` | Dividers |
| Accent | `oklch(62% 0.13 32)` | Active state, primary action |
| Info | `oklch(58% 0.12 230)` | Info severity |
| Warning | `oklch(72% 0.14 82)` | Warning severity |
| Error | `oklch(60% 0.17 28)` | Error severity |

This keeps the UI modern but less corporate.

### Texture

Add a subtle fixed noise layer or paper grain effect. Very low opacity. The goal is to reduce sterile flatness, not add decoration.

### Borders

Use fewer borders:

- Keep table borders.
- Keep inspector dividers.
- Remove most outer panel boxes.
- Use tonal backgrounds and spacing to separate areas.

## Typography

Replace the generic product-tool feel with a little more character.

Recommended:

- Headings: `Outfit`, `Satoshi`, or `Geist` at heavier weights.
- UI/body: `Geist` or system sans.
- Raw Markdown/code: existing mono stack.

If staying dependency-free, use system font but improve hierarchy:

- Larger app title.
- More confident section headings.
- Slightly tighter rendered headings.
- Tabular numbers for metrics.

## Component Preview Direction

Component previews should look more like a mini style guide:

- Show actual primary/ghost button states.
- Show chip rows with neutral/accent/status variants.
- Show card previews as small surface examples.
- Let previews sit on a canvas, not inside heavy cards.
- Add small labels like `default`, `hover`, `accent`, `disabled` where useful.

## Interaction Changes

- Use segmented controls for inspector tabs.
- Add pressed states on buttons.
- Add subtle fade/slide when switching inspector tabs.
- Keep transitions around 180ms.
- Avoid decorative page-load animations.

## Suggested V2 UI Concept

Name: **Studio Review**

Core idea:

The design document appears as a clean editorial canvas. Verification data floats around it as lightweight instrumentation.

First screen:

- Top command bar.
- Warm background.
- Big drop zone that becomes a health strip after file load.
- Main document canvas centered-left.
- Inspector panel on the right with tabs.
- Outline available as a compact popover/drawer, not a permanent Jira sidebar.

## Implementation Priority

Implemented in the current `design-viewer.html`:

- Replaced sidebar and bottom review cards with a compact status rail and right inspector tabs.
- Warmed up the palette and reduced the admin feel.
- Made the rendered Markdown canvas larger and more editorial.
- Upgraded component previews into mini style-guide samples.
- Added subtle background texture.
- Polished spacing and typography.

## Keep From Current Version

- Local-only file parsing.
- Static single-file app.
- Sample file loading.
- Table color swatches.
- Issue severity labels.
- Search highlighting.
- Rendered/raw document toggle.
- Existing parser behavior.
