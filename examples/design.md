---
name: sample-lab-portfolio
description: Sample design document adapted from the lab portfolio structure for testing Visualise Design MD.
colors:
  accent: "#da7d91"
  bg: "#faf9f7"
  surface: "#f3f1ee"
  fg: "#111110"
typography:
  display: "Bricolage Grotesque"
  body: "Geist"
  label: "JetBrains Mono"
---

# Design System: Sample Lab Portfolio

## 1. Overview

**Creative North Star:** The Warm Studio.

This sample represents a warm, editorial portfolio experience. It uses soft neutral surfaces, a single rose accent, careful typography, and restrained motion. The goal is to make the page feel personal and deliberate without relying on generic developer-portfolio patterns.

### Verification Checklist

- [x] Define creative direction
- [x] Document color palette
- [ ] Confirm final responsive behavior
- [ ] Review accessibility states

## 2. Colors: Rose-Warm Palette

| Token | Value | Usage |
| --- | --- | --- |
| Studio Rose | `#da7d91` | Accent, active pills, availability indicator |
| Warm Cream | `#faf9f7` | Page background |
| Linen | `#f3f1ee` | Raised surfaces |
| Charcoal Warm | `#111110` | Primary text |

### Color Rules

- [x] Use the accent on less than 10% of the screen.
- [x] Avoid pure black and pure white.
- [ ] Validate contrast ratios for accent text.

## 3. Typography

| Role | Font | Notes |
| --- | --- | --- |
| Display | Bricolage Grotesque | Hero name and large section headings |
| Body | Geist | Paragraph copy and supporting text |
| Label | JetBrains Mono | Chips, status text, metadata |

The display type should feel expressive but not loud. Body copy should stay readable with comfortable line length.

## 4. Components

### Buttons

- Primary buttons use a dark fill and warm background text.
- Ghost buttons use the raised surface token and a subtle border.
- Hover uses small translate and opacity changes.

### Chips / Pills

- [x] Use rectangular pills with 3px to 4px radius.
- [ ] Confirm chip wrapping on mobile.

### Cards

Cards use tonal layering and borders instead of shadows.

## 5. Screens

| Screen | Purpose | Status |
| --- | --- | --- |
| Hero | Introduce the person and tone | Ready |
| Projects | Show selected work | Needs copy pass |
| Contact | Provide next action | Draft |

## 6. States

### Hover

Hover states should be subtle and limited to opacity or transform.

### Focus

Focus states must remain visible for keyboard users.

### Empty

## 7. Interactions

- Avatar images may crossfade every few seconds.
- Reduced motion should freeze decorative animation.
- Navigation appears after the user scrolls past the hero.

## 8. Acceptance Criteria

- [x] Design document includes colors, typography, components, states, and interactions.
- [ ] Viewer flags the intentionally empty `Empty` state section.
- [ ] Viewer detects this unchecked acceptance item.
- [ ] Viewer renders all tables as clean HTML tables.

## 8. Acceptance Criteria

This duplicate heading is intentional so the viewer can test duplicate heading warnings.
