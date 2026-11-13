# Second Brain — Operating Manual

This file is the permanent operating manual for this Second Brain. Every interaction with this vault — ingestion, query, analysis, comparison, planting ideas, reviews, audits, maintenance — follows the rules here. If an instruction in a conversation conflicts with this manual, ask the owner which should govern before acting. This is structure v2 (redesigned 2026-11-13 on the owner's instruction; see log.md).

## Prime directives

1. **The wiki states current practice; `raw/` holds the proof.** Handbook-first: no decision or SOP change is "real" until it is on a wiki page, and announcements link to the page. `raw/` remains the immutable source of captured documents — every wiki fact traces back to it or to an owner ruling recorded in the log.
2. **NEVER write to `raw/`. This is a hard constraint with no exceptions.** No edits, renames, moves, or deletions unless the owner explicitly authorizes that specific action in that conversation. The same applies to the content of `clippings/` files (one narrow exception: the `status` frontmatter key, see Clippings below).
3. **Never invent business facts.** Names, figures, dates, procedures, responsibilities come only from ingested sources or directly from the owner. When the knowledge base lacks evidence, say so plainly.
4. **Never silently replace conflicting information** — record the conflict, cite both sources with dates, ask the owner which governs (see Conflicts).
5. **Never delete wiki pages.** Outdated pages get `status: superseded` and stay linked from their replacement.
6. **Every write updates `index.md` and appends to `log.md`** in the same operation. An ingest that skips either is incomplete.
7. `log.md` is append-only; `CLAUDE.md` changes only on the owner's instruction, and the change is logged.

## Purpose and business context

Recorded from the owner interview on 2026-08-31; update only when the owner says the business has changed.

- The owner runs **general business operations** — broad, entrepreneurial scope.
- The vault optimizes for four jobs: **"How do we do X here?"** retrieval; **business and start-up decisions** with rationale; **ideas and creative development** that mature instead of getting lost (the [[Greenhouse]]); and **risks, lessons, and compliance**.
- The owner provides: SOPs, policies and plans; meeting notes and memos; business and financial documents; and web clippings via Obsidian Web Clipper.
- Information is categorized **by business area first** (taxonomy below), knowledge type second.

## The pipeline (CODE)

Every piece of inbound material moves through four stages:

| Stage | Where | What happens |
|---|---|---|
| **Capture** | `raw/`, `clippings/` | Originals land, immutable |
| **Organize** | `wiki/sources/` | One source-summary page per document |
| **Distill** | `wiki/` entity pages | Facts become linked, cited entity pages |
| **Express** | `wiki/analyses/`, [[Home]], registers | Answers, comparisons, reviews, dashboards |

## Folder structure

```
Second Brain/
├── CLAUDE.md          ← this manual
├── Home.md            ← dashboard and front door (cssclasses: sb-home)
├── index.md           ← master index by business area (rebuildable cache)
├── log.md             ← append-only operations log
├── raw/               ← SOURCE OF TRUTH — never written
│   ├── business-documents/  sops/  policies/  meeting-notes/  assets/
├── clippings/         ← Web Clipper captures (content preserved as captured)
├── wiki/              ← agent-generated knowledge
│   ├── maps/          ← navigation: 9 area maps + Greenhouse
│   ├── sources/  sops/  processes/  people/  organizations/
│   ├── tools/  concepts/  ideas/  risks/  decisions/  analyses/
├── bases/             ← .base files powering the live views and registers
├── templates/         ← one template per page type (core Templates plugin)
├── setup/             ← one-time setup: guide + Web Clipper template JSON
└── .obsidian/snippets/ ← sb-identity.css, sb-columns.css
```

**Routing table** — where each kind of new knowledge goes:

| Kind of knowledge | Folder | Template |
|---|---|---|
| Ingested document/clipping summary | `wiki/sources/` | Source Template |
| Procedure (how to do one thing) | `wiki/sops/` | SOP Template |
| End-to-end flow across roles | `wiki/processes/` | Process Template |
| A person | `wiki/people/` | Person Template |
| A company, client, vendor, authority | `wiki/organizations/` | Organization Template |
| A tool, system, platform | `wiki/tools/` | Tool Template |
| A definition or framework (≥2 sources engage with it) | `wiki/concepts/` | Concept Template |
| A maturing creative/marketing/venture idea | `wiki/ideas/` | Idea Template |
| A risk | `wiki/risks/` | Risk Template |
| A significant decision | `wiki/decisions/` | Decision Template |
| An analysis, comparison, weekly review | `wiki/analyses/` | Analysis / Weekly Review Template |
| A navigation map | `wiki/maps/` | Map Template |

If the agent needs to infer where something belongs, the structure is too clever — ask the owner.

## Navigation layer

Three levels, zero file moves: **[[Home]] → maps → pages**.

- [[Home]] links to maps (and fixed library pages), never to individual entity pages; it must stay glanceable. Live sections come from `bases/dashboard.base` embeds.
- One map per business area in `wiki/maps/`, plus the [[Greenhouse]]. Maps are curated overlays: grouped links **with a phrase of commentary each**, a live area table, and threads into other maps.
- Gardening rules (mechanical, agent-enforced): add a curated link when a page joins an area; 3–5 links per section before splitting a subsection; a new sub-map is justified by 7–10 loose pages on one topic; a map that no longer fits one screen gets split; every wiki page carries `up` and a `Map:` line pointing to its map.
- Open [[Home]] in **Reading view** for the column layout (CSS targets it). Recommend pinning the Home tab.

## Business-area taxonomy

The `area` property (list) carries one or more of exactly these values:

| Area | Value | Map |
|---|---|---|
| Design & Brand | `design` | [[Design Map]] |
| Start-up & Strategy | `startup` | [[Startup Map]] |
| Marketing & Ideas | `marketing` | [[Marketing Map]] |
| Creativity & Innovation | `creativity` | [[Creativity Map]] |
| Business Management | `management` | [[Management Map]] |
| Security & Emergency | `security` | [[Security Map]] |
| Operations & Service Delivery | `operations` | [[Operations Map]] |
| HR, Training & Administration | `hr` | [[HR Map]] |
| Finance, Procurement & Contracts | `finance` | [[Finance Map]] |

New areas only on the owner's instruction: add the value here, create the map, log the change.

## Page schemas (frontmatter)

Bases reads **only** frontmatter properties and file metadata, so every queryable datum is a property, never inline text. Rules:

- Multi-word property names use **underscores** (`review_due`, `decided_by`) — hyphens break Bases expressions.
- Common to all wiki pages: `type`, `area` (list), `status`, `sources` (list), `confidence` (high|medium|low), `up`, `created`, `updated` (bump on every content change). Dates are `YYYY-MM-DD`. Exceptions: maps and other navigation pages omit `sources` and `confidence` (they organize, they don't assert); source pages omit `confidence`. Templates default `up` to `[[Home]]` as a fallback — set it to the page's map at creation.
- **Unknown ≠ invented:** when a source does not state a value (owner, approval date…), leave the property **empty**. Empty values are surfaced by the registers as audit findings. Never guess.
- Status vocabularies are fixed: general pages `draft | current | conflicted | superseded`; ideas `seedling | budding | evergreen | parked`; decisions `proposed | active | superseded | reversed`; risks `open | watching | mitigating | closed`; clippings `inbox | ingested`.
- Stable IDs, assigned at creation and never reused or renamed: SOPs `SOP-<area##>.<##>` (e.g. SOP-31.04), decisions `DEC-<YYYY>-<###>` (e.g. DEC-2026-014). The index records them.
- Type-specific required fields are defined by the templates in `templates/` — always start from the template.

## Naming, titles and aliases

- Wiki pages: Title Case, the subject itself as the name, no dates in the name (exception: dated periodic analyses such as `Weekly Review YYYY-MM-DD`). The filename is the link target — `[[Incident Management]]` must resolve. Avoid `[ ] # ^ | \ / :` in names.
- Titles are handles: declarative and specific ("Contractor Onboarding SOP", not "Onboarding stuff").
- **Every SOP and process gets question-phrased `aliases`** ("How do we onboard a contractor?") so natural questions hit the right page in search and in chat.
- Source pages: the human-readable title of the original document; the exact path lives in the `original` property.
- Raw files and clippings keep their original names — never renamed.

## Formatting rules

- One `# H1` matching the filename; shallow `##` hierarchy; `**bold**` for the key lines (progressive-summarization discipline); every entity page opens with a TL;DR callout.
- Wiki-links on first mention per section; `[[Page#Section]]` and `[[Page|display]]` as needed; embeds `![[file]]`.
- House callouts (defined in `sb-identity.css`): `[!map]` navigation · `[!sop]` procedure highlights · `[!risk]` risk statements · `[!decision]` decisions · `[!idea]` ideas · `[!conflict]` contradictions. Built-ins (`[!abstract]`, `[!tip]`, `[!warning]`…) stay available. Foldable: `[!type]-` closed, `[!type]+` open.
- `> [!multi-column]` + `>> [!blank]`/typed sub-callouts for columns (needs `sb-columns.css`); separator between sub-callouts is a line holding only `>`.

## Citation and provenance

- **Every important factual statement cites its source**: `(source: [[Source Page]])` — the source page records the original file path.
- Frontmatter `sources:` lists every source cited on the page.
- Maximum ~2 direct quotes per page; prefer distilled statements in our own words.
- Evidence (cited) is separated from interpretation (marked "Assessment:" or equivalent).
- Uncertain claims get `confidence: low` — the dashboard surfaces them.

## Conflicts

When new information contradicts existing pages: keep both versions visible under a `> [!conflict]` callout quoting the exact conflicting statements; name the competing sources and their dates; set `status: conflicted`; log it; ask the owner which governs. After the ruling: mark the losing information superseded (kept, in a History section), restore status, log the resolution.

## Dedup and link integrity

- Read `index.md` before creating any page; search for an existing page first — duplicates are vault rot.
- Don't create a page you cannot fill with at least 3 meaningful sentences; a concept needs ≥2 distinct sources engaging with it.
- **Re-read a page in full before updating it.**
- Link at write time, in both directions — but **only to files that exist on disk**; verify the target before writing the link. A link that must wait is logged: `SKIPPED: [[Target]] from Page.md — target not found at write time`.
- No vault-wide "standardize all frontmatter" passes — bulk edits silently break views. Bounded per-folder tasks only, with YAML validity checked in the same turn.

## Bases authoring rules

The live views live in `bases/*.base` and inline ` ```base ` blocks (maps). When writing or editing them:

- Only documented keys: top-level `filters / formulas / properties / summaries / views`; per view `type / name / limit / filters / groupBy / groupOrder / sort / order / summaries`.
- `sort` entries are maps with exactly `property` and `direction`, direction **uppercase** `ASC`/`DESC` — anything else is *silently ignored*.
- Quote formulas: single-quote the YAML scalar, double-quote strings inside: `'if(price, price.toFixed(2) + " dollars")'`.
- Filters reference `file.inFolder("wiki/sops")`, `file.hasTag()`, `file.hasProperty()`, bare property names, `file.mtime > now() - "1 week"`, `this.file` in embeds.
- Inside callouts embed **base files** (`> ![[dashboard.base#View]]`), never fenced ` ```base ` blocks (known editing bugs). Fenced blocks are fine standalone.
- Obsidian may append its own UI-state keys to .base files — leave them in place.

## Clippings

`clippings/` is an inbox, not a destination. The Web Clipper template (in `setup/`) stamps every capture with `status: inbox`. **The one permitted edit to a clipping** is flipping its frontmatter `status` from `inbox` to `ingested` during ingestion — the body below the frontmatter is never touched. Everything else about raw-immutability applies.

## Workflows

### Ingestion ("Ingest raw/sops/X" / "Ingest all new files in raw/" / "Ingest the new clippings")

1. Read `index.md` and `log.md` first; identify new or unprocessed files (clippings: `status: inbox`).
2. Read every selected source completely — no skimming.
3. Summarize facts, requirements, responsibilities, risks, decisions, processes; for a multi-source batch, present 3–5 key takeaways to the owner before writing.
4. Create a source page in `wiki/sources/` (template; `original:` = exact path).
5. Create/update the entity pages per the routing table, from their templates, citing the source; assign IDs and aliases; set `area`.
6. Cross-link in both directions (link-integrity rules above) and add each new page to its map's curated trails with commentary.
7. Check for conflicts; handle per Conflicts.
8. Clippings: flip `status` to `ingested`.
9. Update `index.md`; append to `log.md`.
10. Report: files created/updated, conflicts, anything needing review (empty owners/dates, low confidence). Expect one ingest to touch 5–15 pages.

### Query (the owner asks a question)

1. `index.md` first → relevant pages → follow links as needed.
2. Answer from the knowledge base, citing the supporting pages (and through them the sources).
3. State plainly when evidence is missing; never fill gaps; offer to ingest what would cover them.
4. Offer to save valuable conclusions into `wiki/analyses/` (then index + log).

### Planting and tending ideas ("Plant an idea: …")

Create the page in `wiki/ideas/` from Idea Template (`status: seedling`, `planted`/`tended` today, `up: [[Greenhouse]]`); link related pages; index + log. Tending updates `tended` and promotes status when earned; graduation creates a decision page.

### Comparison (`Compare [[article]] against [[SOP]]`)

Ingest the external source if new → read the current SOP and its source → write a comparison in `wiki/analyses/`: point-by-point table, gaps, labeled recommendations. **The SOP page itself does not change** — recommendations become SOP changes only when the owner approves and provides or authorizes an updated source document; then the lesson is edited into the SOP page, handbook-first.

### Weekly review ("Run the weekly review")

Pre-fill a `wiki/analyses/Weekly Review YYYY-MM-DD` page from the Weekly Review Template using `log.md` and the week's page changes: wins, stuck, open loops, Greenhouse check (promote/demote; resurface seedlings untended 30+ days), overdue `review_due` decisions and risks, next week's top 3. The owner confirms and decides; index + log.

### Audit ("Run a wiki audit (dry run)")

Check: broken/mis-cased links; orphans (no inbound links, missing from index or a map); duplicates; contradictions; unsupported claims; superseded pages still `current`; subjects mentioned 3+ times without a page; SOPs with empty owner/approved/review_due or past review; risks without controls; decisions without evidence or past review; malformed frontmatter and off-vocabulary statuses; index entries pointing nowhere; maps violating gardening rules; un-ingested files in `raw/` and `clippings/`. **The first audit — and any audit unless the owner says otherwise — is a dry run**: report, get approval, then fix. Log both. Cadence: monthly, or after every ~10 ingests; review this manual monthly too.

## index.md rules

Lists **every** wiki page, organized by business area first, knowledge type as a secondary label; entries carry an Obsidian link, a one-sentence description, last-updated date, and supporting sources. Maps are listed in their own Navigation section; source pages in the Source Library. Multi-area pages: full entry under the primary area, cross-reference under the others. The index is a rebuildable cache — the audit may regenerate it.

## log.md rules

Append-only; new entries at the end; corrections are new `correction` entries. **Record every ingestion, significant query, analysis, comparison, audit, structural change, conflict, and rule change.** Format:

```markdown
## [YYYY-MM-DD] operation | Subject
- What was done, files touched, conflicts, owner decisions.
```

Operations: `setup`, `ingest`, `query`, `analysis`, `comparison`, `idea`, `review`, `audit`, `audit-fix`, `conflict`, `resolution`, `structure`, `rule-change`, `correction`. Tag failures with `!failure`. Greppable scan: `grep "^## \[" log.md | tail -5`.

## Commands quick reference

| Owner says | Agent runs |
|---|---|
| "Ingest raw/…/<file>" / "Ingest all new files in raw/" | Ingestion |
| "Ingest the new clippings" | Ingestion over `clippings/` |
| a question | Query |
| "Plant an idea: …" | Greenhouse planting |
| `Compare [[article]] against [[SOP name]]` | Comparison |
| "Run the weekly review" | Weekly review |
| "Run a wiki audit (dry run)" / "Apply the approved audit fixes" | Audit / fixes |
