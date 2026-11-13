# Second Brain Log

Append-only operations log. New entries go at the end. Never edit or delete existing entries — corrections are new `correction` entries. Format and operation vocabulary are defined in [[CLAUDE|CLAUDE.md]].

---

## [2026-08-31] setup | Second Brain initialized
- Conducted the owner interview (business scope, coverage areas, document types, categorization preference, decision priorities); answers recorded in the Business Context section of CLAUDE.md.
- Created the folder structure: raw/ (business-documents, sops, policies, meeting-notes, assets), clippings/, wiki/ (sources, sops, processes, people, organizations, tools, concepts, risks, decisions, analyses).
- Wrote CLAUDE.md (permanent operating manual), initialized index.md (empty index, organized by business area) and this log.
- No documents ingested yet; wiki contains no knowledge pages.

## [2026-08-31] ingest | raw/ scan — no files found
- Owner requested ingestion of the raw folder. Checked index.md and log.md, pulled the latest branch state, and scanned raw/ (all five subfolders), clippings/, every branch of the repository, and the session workspace.
- Result: zero documents present. No wiki pages created, index.md unchanged. Reported to owner with instructions for adding documents.

## [2026-11-13] structure | Vault redesign v2 (owner-requested)
- Owner asked for a research-driven redesign with a special access page. Ran a deep-research pass (11 agents: PKM methodologies, Obsidian Bases/callout/CSS/URI/Web Clipper verification, AI-vault patterns, inspiration sweep) and rebuilt the structure on it.
- Added the navigation layer: Home.md dashboard, wiki/maps/ with nine business-area maps + the Greenhouse (idea incubator over new folder wiki/ideas/).
- Added bases/ (dashboard, sops, risks, decisions, ideas, wiki .base files — live registers), templates/ (13 typed note templates locking the frontmatter schemas), setup/ (Setup Guide + importable Web Clipper template), .obsidian/snippets/ (sb-identity.css, sb-columns.css), and .gitignore.
- Rewrote CLAUDE.md as structure v2: prime directives, CODE pipeline, routing table, navigation gardening rules, fixed status vocabularies, stable IDs (SOP-##.##, DEC-YYYY-###), underscore property names, empty-not-guessed rule, Bases authoring rules, new workflows (plant idea, weekly review), extended audit checklist. All v1 hard rules preserved.
- Rule changes vs v1, for owner awareness: (1) the one permitted clipping edit is flipping frontmatter status inbox→ingested at ingestion; (2) unknown SOP governance values are left EMPTY instead of written as "unknown"; (3) the Creativity & Innovation area tag is `creativity` (was `ideas`); (4) multi-word properties use underscores (review_due).
- Rebuilt index.md (Navigation section + area sections). Published the Mission Control access page: https://claude.ai/artifact/Fm5cAZKSJhxSfrLMK3BpNj
- Still zero business documents ingested; wiki contains only navigation pages.

## [2026-11-13] audit-fix | Post-redesign verification fixes
- Ran an adversarial verification pass (three critics: Obsidian-syntax vs official docs, v1-contract compliance, UX coherence) over the redesign, plus a mechanical lint (YAML, Bases schema, link integrity, clipper JSON). All Bases/callout/CSS/URI syntax passed; fixes applied for the findings:
- Contract: restored the v1 comparison rule verbatim in spirit — an SOP page changes only when the owner approves **and provides or authorizes an updated source document** (the redesign had dropped the second condition); reconciled prime directive 1 so raw/ stays the source of captured truth while the wiki states current practice; restored the v1 logging-scope sentence (log every ingestion, significant query, analysis, comparison, audit, structural change, conflict, rule change). With these, the redesign entry's "All v1 hard rules preserved" claim holds.
- Schema: scoped the common-property rule (maps omit sources/confidence; source pages omit confidence; `up: [[Home]]` is a template fallback to be set to the page's map); naming exception for dated periodic analyses (Weekly Review YYYY-MM-DD); quoted all template date placeholders against Live-Preview mangling.
- Views: maps and the Recently-updated feed now exclude navigation pages (no self-rows on area tables).
- Setup Guide and Mission Control (v2 published): kanban boards need Obsidian 1.14+; the sync step now covers both directions explicitly — clippings and local edits must be committed and pushed before the agent can see them (GitHub Desktop recipe added); corrected the pin-tab explanation; added the "Apply the approved audit fixes" follow-up and a fallback for environments that block obsidian:// links.
