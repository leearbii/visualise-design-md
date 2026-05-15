# Visualise Design MD

A static browser tool for reviewing `design.md` files locally — no install, no upload, no account.

## Why We Built This

Design documents written in Markdown are easy to draft but surprisingly hard to audit. As a spec grows, important details get buried across sections, unchecked acceptance criteria quietly blend in with completed ones, tables become difficult to scan in raw form, and empty or duplicate headings create false confidence that a topic has been covered.

Most tools solve the *writing* problem. We needed something that solves the *reviewing* problem.

We built Visualise Design MD for teams and solo builders who use `design.md` files as the source of truth before handing off to implementation — whether that's a human engineer or an AI coding agent. The tool surfaces the things reviewers miss: unchecked tasks, structural gaps, malformed tables, duplicate headings. It does this locally, in the browser, with no setup.

This is particularly useful in AI-assisted workflows where a weak or incomplete design document directly reduces implementation quality. A clean, verified spec means the agent (or the engineer) starts from a clear foundation.

The design principle is simple: drag in a file, see the issues, fix the source, reload to verify.

## Who It Is For

- **Product builders and PMs** preparing implementation-ready specs before handing off to engineering or AI agents.
- **Designers** checking that screens, components, states, interactions, and design tokens are all documented.
- **Engineers** verifying whether a design document is complete enough to build from without asking clarifying questions.
- **Solo builders** using lightweight Markdown specs instead of heavier design tooling.

## How It Works

1. Open `design-viewer.html` in a browser.
2. Drag and drop a `design.md` file, or select one with the file picker.
3. The file is read entirely in your browser — nothing is uploaded.
4. Inspect the rendered document, heading outline, checklist status, table previews, and detected issues.
5. Fix the source file in your editor.
6. Reload or drag the file again to verify improvements.

## Features

- Local `.md` and `.markdown` file loading — no server, no upload
- Rendered Markdown preview with editorial typography
- Raw Markdown view behind a `Rendered / Raw` toggle
- Clickable heading outline
- Checklist summary with unchecked item count
- Markdown table extraction and clean HTML table rendering
- Color swatches for color values inside rendered tables
- Component extraction from `Components` sections with mini previews
- Empty section detection
- Duplicate heading detection
- Issue severity labels: `info`, `warning`, and `error`

## Getting Started

No install step. Open `design-viewer.html` directly in any modern browser, or try it with the included sample:

```
examples/design.md
```

To deploy, push the repo to GitHub and point Vercel at the repository root with no build command.

## What It Is Not

Visualise Design MD is intentionally narrow. Version one does not include:

- Editing or saving Markdown
- Cloud sync, accounts, or collaboration
- Full CommonMark compliance
- Multi-file compare or report export

It is a review bench, not an editor.
