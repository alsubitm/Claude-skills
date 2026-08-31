# Second Brain — Operating Manual

This file is the permanent operating manual for this Second Brain. Every interaction with this vault — ingestion, query, analysis, comparison, audit, or maintenance — must follow the rules in this file. If an instruction in a conversation conflicts with this manual, ask the owner which should govern before acting.

## Purpose

This Second Brain stores, organizes, connects, and improves the knowledge, SOPs, workflows, policies, processes, external research, and operational lessons of the owner's business. It is an Obsidian-compatible vault: plain Markdown files, wiki-style `[[internal links]]`, YAML frontmatter.

It is optimized to answer four kinds of questions:

1. **"How do we do X here?"** — fast retrieval of the current, governing SOP, policy, or process.
2. **Business and start-up decisions** — comparing options, capturing decision rationale, tracking what was decided and why.
3. **Ideas and creative development** — capturing marketing ideas, design concepts, and out-of-the-box thinking so they mature over time instead of getting lost.
4. **Risks, lessons, and compliance** — what could go wrong, what went wrong before, what controls exist, and what external research recommends.

## Business Context

Recorded from the owner interview on 2026-08-31. Update this section only when the owner says the business has changed.

- The owner runs **general business operations** — a broad, entrepreneurial scope, not a single specialty.
- The Second Brain must cover these **business areas**: design; business start-up operations; marketing and ideas; creativity and out-of-the-box thinking; business management; security and emergency response; operations and service delivery; HR, training and administration; finance, procurement and contracts.
- The owner will provide: SOPs, policies and plans; meeting notes and internal memos; business and financial documents (business plans, contracts, RFPs, budgets, KPI reports); and web articles and external research captured through Obsidian Web Clipper.
- Information is categorized **by business area first**, with knowledge type secondary (see Business-Area Taxonomy below).

## Folder Structure and Purpose

```
Second Brain/
├── CLAUDE.md        ← this operating manual (edit only on owner instruction)
├── index.md         ← master index of every wiki page, by business area
├── log.md           ← append-only operations log
├── raw/             ← original internal documents — SOURCE OF TRUTH, read-only
│   ├── business-documents/   ← business plans, contracts, RFPs, budgets, KPI reports
│   ├── sops/                 ← original SOP documents
│   ├── policies/             ← original policy and plan documents
│   ├── meeting-notes/        ← meeting minutes, memos, internal correspondence
│   └── assets/               ← images, diagrams, spreadsheets, and other binary attachments
├── clippings/       ← external articles and research captured via Obsidian Web Clipper — preserved as captured
└── wiki/            ← knowledge generated and maintained by the agent
    ├── sources/         ← one summary page per ingested raw document or clipping
    ├── sops/            ← distilled SOP pages (one per procedure)
    ├── processes/       ← business process pages (how work flows end-to-end)
    ├── people/          ← one page per person (roles, responsibilities, contacts)
    ├── organizations/   ← one page per company, vendor, client, or authority
    ├── tools/           ← one page per tool, system, or platform the business uses
    ├── concepts/        ← definitions, frameworks, ideas, creative concepts
    ├── risks/           ← one page per identified risk, with its controls
    ├── decisions/       ← one page per significant decision, with rationale and evidence
    └── analyses/        ← saved analyses, comparisons, and research conclusions
```

### Folder rules

1. **`raw/` is the source of truth.** Never edit, rename, move, or delete anything in `raw/` unless the owner explicitly authorizes that specific action in that conversation. Blanket permission does not exist.
2. **`clippings/` preserves originals.** Files captured by Obsidian Web Clipper stay exactly as captured. Do not edit their content. Summarize and interpret them in `wiki/`, never in place.
3. **`wiki/` is the agent's workspace.** The agent creates, updates, cross-references, and maintains these pages. Every wiki page must trace its facts back to `raw/` or `clippings/` sources.
4. **`CLAUDE.md`** changes only when the owner asks for a rule change, and the change is recorded in `log.md`.
5. **`index.md`** is updated in the same operation as any wiki page creation, rename, or significant update.
6. **`log.md`** is append-only. Never edit or delete existing entries. Corrections are new entries.

## Business-Area Taxonomy

Every wiki page carries one or more `area` values in its frontmatter. The canonical areas and tags:

| Area | Tag | Covers |
|---|---|---|
| Design & Brand | `design` | Visual design, brand, product/service design |
| Start-up & Strategy | `startup` | Business start-up operations, strategy, new ventures |
| Marketing & Ideas | `marketing` | Marketing plans, campaigns, marketing ideas |
| Creativity & Innovation | `ideas` | Out-of-the-box thinking, creative concepts not yet assigned to an area |
| Business Management | `management` | General management, planning, governance, KPIs |
| Security & Emergency | `security` | Security operations, incident and emergency response, HSSE |
| Operations & Service Delivery | `operations` | Core operational processes, service delivery, facilities, logistics |
| HR, Training & Administration | `hr` | People, recruitment, training, competency, admin |
| Finance, Procurement & Contracts | `finance` | Budgets, purchasing, vendors, contracts, RFPs and bids |

Add a new area only when the owner introduces one; record the taxonomy change in `log.md` and update this table.

## Naming Conventions

- **Wiki pages**: Title Case, the subject itself as the file name, no prefixes, no dates in the name. Examples: `Incident Management.md`, `Emergency Response SOP.md`, `Ahmed Al-Qahtani.md`. The file name is the link text — `[[Incident Management]]` must resolve.
- **Source-summary pages** (`wiki/sources/`): the human-readable title of the original document, e.g. `raw/sops/ERP-v2_final(3).docx` → `wiki/sources/Emergency Response Plan v2.md`. The page's frontmatter records the exact original path.
- **Raw files**: keep their original names — never rename. When the owner drops in a new file, a `YYYY-MM-DD` prefix is recommended but never required and never applied retroactively.
- **Clippings**: keep the name Obsidian Web Clipper assigns.
- **One subject per page.** If a page starts covering two subjects, split it and cross-link the halves.
- Avoid characters that break Obsidian links in file names: `[ ] # ^ | \ / :`.

## Markdown and YAML Formatting Rules

Every wiki page starts with YAML frontmatter:

```yaml
---
type: source | sop | process | person | organization | tool | concept | risk | decision | analysis
area: [security, operations]        # one or more taxonomy tags
created: YYYY-MM-DD
updated: YYYY-MM-DD                 # bump on every content change
sources:                            # the raw files / clippings the page's facts come from
  - "raw/sops/ERP-v2_final(3).docx"
  - "clippings/Some Article.md"
status: current                     # current | draft | conflicted | superseded
---
```

Additional required frontmatter by type:

- **`sop`**: `owner:` (who owns the procedure), `approved:` (approval date), `review-due:` (next review date). If the source document does not state one of these, write `unknown` — do not guess. `unknown` values are audit findings, not placeholders to fill creatively.
- **`risk`**: `controls:` (list of existing controls; `none identified` is a valid, reportable value).
- **`decision`**: `decided:` (date), `decided-by:`, `evidence:` (links to supporting pages/sources).
- **`source`**: `original:` (exact path of the raw file or clipping), `ingested:` (date).

Body rules:

- One `# H1` matching the file name, then `##` sections. Keep hierarchy shallow.
- Use `[[Wiki Links]]` for every mention of another subject that has (or deserves) a page. Link on first mention in each section.
- Use `[[Page Name#Section]]` links when pointing at a specific section, and `[[Page Name|display text]]` when the sentence needs different wording.
- Bullet lists for facts, tables for structured comparisons, `> [!note]` / `> [!warning]` Obsidian callouts for caveats and conflicts.
- Embed assets with `![[image.png]]` referring to files in `raw/assets/`.
- Dates always `YYYY-MM-DD`.

## Source-Citation Requirements

- **Every important factual statement must identify the document or clipping that supports it.** Cite inline at the end of the statement or bullet: `(source: [[Emergency Response Plan v2]])` — linking to the source-summary page, which in turn records the exact original file path.
- A page's frontmatter `sources:` list must include every original file cited anywhere in the page.
- Analyses and conclusions must separate **evidence** (cited) from **interpretation** (marked as the agent's reasoning, e.g. "Assessment:").
- If a statement cannot be traced to a source, it does not belong in the wiki — flag the gap instead.

## Rules Against Inventing Information

1. Never write business facts, figures, names, dates, procedures, or responsibilities that do not come from an ingested source or directly from the owner.
2. Never fill gaps with plausible-sounding content. State plainly: "The knowledge base does not contain this."
3. Never infer approval status, ownership, or currency of an SOP — if the document doesn't say, record `unknown`.
4. Clearly label anything that is the agent's own analysis, suggestion, or synthesis as such, and keep it out of pages that present facts unless clearly separated.
5. **Never silently replace conflicting information.** When new information contradicts existing pages:
   - Keep both versions visible on the affected page under a `> [!warning] Conflict` callout.
   - Identify the competing sources and their dates.
   - Set the page's `status: conflicted`.
   - Record the conflict in `log.md`.
   - Ask the owner which information governs the current process. Only after the owner rules: mark the losing information as superseded (keep it, struck through or in a "History" section), restore `status: current`, and log the resolution.

## Ingestion Workflow

When the owner asks to ingest a source (a file in `raw/` or `clippings/`):

1. Read `index.md` and `log.md` first to know current state and avoid re-ingesting.
2. Identify the new or unprocessed files (compare folder contents against source pages and log entries).
3. Read every selected source completely — no skimming, no partial reads.
4. Summarize the important facts, requirements, responsibilities, risks, decisions, and processes.
5. Create a source-summary page in `wiki/sources/` (type `source`, frontmatter `original:` pointing at the exact file).
6. Create or update the relevant SOP, process, person, organization, tool, risk, concept, and decision pages, citing the source.
7. Add internal links between all related pages, in both directions.
8. Check for conflicts with existing pages; handle per the conflict rule above.
9. Update `index.md` (add/update entries under the correct business area).
10. Append the operation to `log.md`.
11. Report to the owner: files created, files updated, conflicts found, and anything requiring review (e.g. SOPs with `unknown` owners or dates).

## Query Workflow

When the owner asks a question:

1. Read `index.md` first to locate relevant pages.
2. Open the relevant wiki pages.
3. Follow their `[[links]]` when additional context is required.
4. Answer from the knowledge base, identifying the supporting pages (and through them, the original sources).
5. State clearly when the knowledge base does not contain enough evidence to answer.
6. Do not fill gaps with invented information — offer to ingest a source that would cover the gap instead.
7. Offer to save valuable conclusions or analyses back into `wiki/analyses/` (then update `index.md` and `log.md`).

## Comparison Workflow

When the owner asks to compare external knowledge (a clipping or article) against an existing SOP or process:

1. Ingest the external source first if it isn't already in the wiki.
2. Read the current SOP/process page and its original source.
3. Produce a comparison in `wiki/analyses/`: point-by-point table (our practice vs. external recommendation), gaps, and clearly-labeled improvement suggestions.
4. Do not change the SOP page itself — recommendations only become SOP changes when the owner approves and provides/authorizes an updated source document.
5. Update `index.md`, append to `log.md`.

## Wiki-Audit Workflow

When the owner requests an audit, check for:

- Broken internal links (links to pages that don't exist).
- Orphan pages (no links in, not listed in `index.md`).
- Duplicate pages (two pages covering one subject).
- Contradictory information between pages or within a page.
- Unsupported claims (statements without source citations).
- Outdated or superseded procedures still marked `current`.
- Important subjects mentioned repeatedly but without dedicated pages.
- SOPs with `unknown` or missing owners, approval dates, or review dates — and SOPs past their `review-due` date.
- Risks without controls.
- Decisions without supporting evidence.
- Files in `raw/` or `clippings/` not yet ingested.

**The first audit — and any audit unless the owner says otherwise — is a dry run**: report findings and proposed changes, get approval, then apply. Log both the audit and the approved fixes in `log.md`.

## index.md Rules

- Lists **every** wiki page, organized **by business area first** (the taxonomy above), with knowledge type as a secondary label on each entry.
- Every entry: an Obsidian link to the page, a one-sentence description, the date last updated, and the supporting source(s).
- Pages spanning multiple areas are listed under each area they carry (full entry under the primary area; short cross-reference under the others).
- Source-summary pages are listed in the Source Library section at the bottom.
- Update `index.md` in the same operation that creates or changes a page — an index that lags the wiki is an audit finding.

## log.md Rules

- Append-only. New entries go at the **end** of the file. Never edit or delete existing entries; correct mistakes with a new `correction` entry.
- Record every ingestion, significant query, analysis, comparison, audit, structural change, conflict, and rule change.
- Entry format:

  ```markdown
  ## [YYYY-MM-DD] operation | Subject
  - What was done, files created/updated, conflicts found, owner decisions.
  ```

- Operation vocabulary: `setup`, `ingest`, `query`, `analysis`, `comparison`, `audit`, `audit-fix`, `conflict`, `resolution`, `structure`, `rule-change`, `correction`.

## Commands Quick Reference

| Owner says | Agent runs |
|---|---|
| "Ingest `raw/sops/<file>`" or "Ingest all new files in raw/" | Ingestion workflow |
| "Ingest the new clippings" | Ingestion workflow over `clippings/` |
| "Query: <question>" (or just asks a question about the business) | Query workflow |
| "Compare [[<article/clipping>]] against [[<SOP>]]" | Comparison workflow |
| "Run a wiki audit (dry run)" | Audit workflow, report-only |
| "Apply the approved audit fixes" | Audit fixes, logged |
