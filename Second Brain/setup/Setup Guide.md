---
type: guide
status: current
up: "[[Home]]"
created: 2026-11-13
updated: 2026-11-13
---

# Setup Guide

Up: [[Home]]

One-time setup to make everything in this vault work exactly as designed.
Your remote control lives outside the vault too: **Mission Control** —
<https://claude.ai/artifact/Fm5cAZKSJhxSfrLMK3BpNj> — has one-click vault
and upload buttons, the agent commands ready to copy, and this checklist.

## 1. Open the vault

Obsidian → **Open folder as vault** → select the `Second Brain` folder (the
folder itself, not the repository root). Keep the vault named **Second
Brain** — the Mission Control deep links target that name.

## 2. Enable the look (CSS snippets)

Settings → **Appearance** → scroll to **CSS snippets** → press the reload
icon → toggle on:

- `sb-identity` — the vault's colors and custom callouts (`[!map]`, `[!sop]`,
  `[!risk]`, `[!decision]`, `[!idea]`, `[!conflict]`)
- `sb-columns` — the multi-column layout [[Home]] uses

Both ship with the vault in `.obsidian/snippets/`. No plugins required.

## 3. Check core plugins

Settings → **Core plugins**:

- **Bases** — on (powers every live table, register and kanban). The kanban
  boards (decision pipeline, risk status, Greenhouse beds) need **Obsidian
  1.14 or later** — update the app if they don't render.
- **Templates** — on, then in its options set **Template folder location** to
  `templates`
- **Bookmarks** — on (optional but recommended: bookmark Home and the maps
  into groups mirroring your business areas)
- **Daily notes** — optional; not required by this vault

## 4. Open Home properly

Open [[Home]], switch to **Reading view** (Ctrl/Cmd + E) — the map columns
render there — and **pin the tab** (right-click the tab → Pin) so other notes
open beside it instead of replacing it; Obsidian restores your tabs on
restart either way. Recommended: Settings → **Editor** → **Default view for
new tabs** → Reading view, so the dashboard always opens laid out.
Optional: an OS shortcut to `obsidian://open?vault=Second%20Brain&file=Home`
opens it from anywhere.

## 5. Configure Obsidian Web Clipper

1. Install the **Obsidian Web Clipper** browser extension.
2. Extension → Settings (cog) → **General → Vaults** → type `Second Brain`
   and press Enter (must match the vault name exactly).
3. Open any template → **Import** (top right) → choose
   `setup/Second Brain Clipping-clipper.json` from this vault (or drag the
   file onto the templates list).
4. In the imported **Second Brain Clipping** template, set its **Vault**
   dropdown to `Second Brain`, and drag the template to the **top** of the
   list so it is the default.

Every clip now lands in `clippings/` with `status: inbox` and appears in
Home's **Clippings inbox** until the agent ingests it.

## 6. Decide how the vault syncs

The agent works on GitHub branch
`claude/obsidian-second-brain-setup-9x1xpd` of `alsubitm/Claude-skills`.
Two directions, both needed:

- **Agent → you:** clone the repository and `git pull` after the agent
  pushes (easiest without a terminal: **GitHub Desktop** — on the GitHub
  page, Code → Open with GitHub Desktop — then its Fetch/Pull button).
- **You → agent:** anything created on this computer — **web clippings
  especially** — only reaches the agent after you commit and push it (in
  GitHub Desktop: write a short summary → Commit → Push). A clip sitting in
  your local inbox is invisible to the agent until pushed. Documents can
  also go up without git through the Mission Control upload buttons.

## Troubleshooting

- **Mission Control buttons do nothing** → open Obsidian once first (registers
  the `obsidian://` handler), and confirm the vault is named `Second Brain`.
- **Home shows plain bullets instead of columns** → you are in editing view or
  the snippets are off; switch to Reading view and re-check step 2.
- **Live tables look stale after switching views** → a known Obsidian quirk;
  reopen the note and it refreshes.
- **A table shows nothing** → normal while the wiki is empty; views fill as
  pages are ingested.
