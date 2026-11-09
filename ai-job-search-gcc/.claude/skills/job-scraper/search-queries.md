# Search Queries for Job Scraper

<!-- SETUP: Customize these queries based on your skills, target roles, and location -->

## Installed portal CLIs (primary for `/scrape`)

`/scrape` discovers every portal skill under `.agents/skills/*/SKILL.md` and runs its CLI first. Shipped country-agnostic CLIs include `linkedin-search` and `freehire-search`; Danish demos and any skill you add with `/add-portal` are included the same way. You do **not** need a matching `site:` line below for those CLIs to run.

The `site:` query templates in this file are the **WebSearch fallback** — for portals without a CLI, company career pages, or when a CLI fails.

**Language scope:** write every query category in every language listed in your CLAUDE.md Languages table (typically 1-2, sometimes more). A posting requiring a language you have *not* declared, as a job condition, is excluded before scoring; a posting requiring a *higher level* than you declared in a language you *do* work in is flagged for your own judgment, not excluded — see `04-job-evaluation.md`'s Language Gate, the single source of truth for this rule. Translate each category's keywords rather than machine-translating word-for-word (e.g. "Frontend Developer" -> "Desarrollador Frontend", not a literal word-for-word translation) if you work in more than one language.

## Search Sites (Saudi Arabia / GCC)

This fork is pre-configured for **Saudi Arabia first, then the rest of the GCC** (UAE, Qatar, Kuwait, Bahrain, Oman). Adjust the markets to match CLAUDE.md's GCC Profile (`Target markets`). Market rules (Saudization etc.) are in `.claude/skills/job-application-assistant/10-gcc-market.md`.

Installed CLIs (run first):
- **linkedin-search** - pass a GCC place string as `--location`: `"Saudi Arabia"`, `"Riyadh, Saudi Arabia"`, `"Jeddah, Saudi Arabia"`, `"Dammam, Eastern, Saudi Arabia"`, `"United Arab Emirates"`, `"Dubai, United Arab Emirates"`, `"Abu Dhabi, United Arab Emirates"`, `"Qatar"`, `"Kuwait"`, `"Bahrain"`, `"Oman"`. Run one call per target market.
- **freehire-search** - tech roles; scope with `--country SA` (or `SA,AE,QA,KW,BH,OM` for the whole GCC), or `--region mena`, as documented in its SKILL.md.

WebSearch `site:` fallback (no CLI installed for these yet; build one with `/add-portal` on your own machine if you use a board heavily):
- **bayt.com** - largest Gulf job board, all GCC
- **gulftalent.com** - professional / mid-senior, all GCC
- **naukrigulf.com** - all GCC
- **sa.indeed.com**, **ae.indeed.com**, **qa.indeed.com**, **kw.indeed.com**, **bh.indeed.com**, **om.indeed.com** - Indeed country sites
- **jadarat.sa** - Saudi national employment platform (جدارات); public and private sector; applying needs a national login
- **tanqeeb.com**, **glassdoor.com** - aggregators
- **Employer careers pages** - your target companies from CLAUDE.md (e.g. Aramco, SABIC, STC, NEOM, Red Sea Global, ROSHN, Qiddiya, ACWA Power, Ma'aden, Elm, SDAIA, ADNOC, e&, QatarEnergy)

## Query Categories

Queries are grouped by priority. Write **each category in every language from your Languages table** - for most GCC candidates that means **English and Arabic** (see Language scope above). Combine each query with your target city or country.

**Organize by function, not job title.** The same underlying work carries different titles across companies and markets. Name each priority category after the function it covers, and list several plausible job titles as query variants.

Arabic search terms: وظائف (jobs), وظيفة (job), مهندس (engineer), محلل (analyst), مدير (manager), أخصائي (specialist), الرياض (Riyadh), جدة (Jeddah), الدمام (Dammam), الخبر (Khobar), دبي (Dubai), أبوظبي (Abu Dhabi), الدوحة (Doha). Translate titles naturally, not word-for-word (e.g. "Data Scientist" -> "عالم بيانات").

### Priority 1: [YOUR_PRIMARY_ROLE_TYPE]

```
site:bayt.com "[YOUR_PRIMARY_JOB_TITLE_1]" Riyadh
site:gulftalent.com "[YOUR_PRIMARY_JOB_TITLE_1]" "Saudi Arabia"
site:naukrigulf.com "[YOUR_PRIMARY_JOB_TITLE_2]" Saudi Arabia
site:sa.indeed.com "[YOUR_PRIMARY_JOB_TITLE_1]"
site:jadarat.sa "[YOUR_PRIMARY_JOB_TITLE_ARABIC]"
site:bayt.com "[YOUR_PRIMARY_JOB_TITLE_ARABIC]" الرياض
```
linkedin-search: `-q "[YOUR_PRIMARY_JOB_TITLE_1]" -l "Saudi Arabia" --jobage 14`

### Priority 2: [YOUR_DOMAIN_EXPERTISE]

```
site:bayt.com [YOUR_DOMAIN_KEYWORD_1] "Saudi Arabia"
site:gulftalent.com [YOUR_DOMAIN_KEYWORD_1] [YOUR_CITY]
site:naukrigulf.com [YOUR_DOMAIN_KEYWORD_2] [YOUR_CITY]
```
linkedin-search: `-q "[YOUR_DOMAIN_KEYWORD_1]" -l "[YOUR_CITY], Saudi Arabia" --jobage 14`

### Priority 3: [YOUR_ADJACENT_ROLE_TYPE] (and other GCC markets)

```
site:bayt.com "[YOUR_ADJACENT_TITLE_1]" Dubai OR "Abu Dhabi"
site:gulftalent.com "[YOUR_ADJACENT_TITLE_1]" UAE OR Qatar
site:ae.indeed.com "[YOUR_PRIMARY_JOB_TITLE_1]"
site:qa.indeed.com "[YOUR_PRIMARY_JOB_TITLE_1]"
```
linkedin-search: `-q "[YOUR_PRIMARY_JOB_TITLE_1]" -l "United Arab Emirates" --jobage 14` (repeat for Qatar, Kuwait, Bahrain, Oman if they are in your Target markets)

### Priority 4: Target employers and giga-projects

```
site:careers.aramco.com "[YOUR_PRIMARY_JOB_TITLE_1]"
"[YOUR_PRIMARY_JOB_TITLE_1]" careers NEOM OR "Red Sea Global" OR ROSHN OR Qiddiya
"[YOUR_PRIMARY_JOB_TITLE_1]" careers [YOUR_TARGET_COMPANY_1]
```

## Location Filter

Verify each job's location against CLAUDE.md's GCC Profile (`Target markets`, `Relocate within GCC`). Tiers:
- **Ideal:** [YOUR_CITY] (e.g. Riyadh)
- **Acceptable:** [ACCEPTABLE_AREA_1] (e.g. other Saudi cities you named), remote roles open to Saudi residents
- **Borderline (FLAG):** site-based / rotational roles (NEOM, Red Sea, offshore, remote plants), [BORDERLINE_AREA]
- **Too far (FAIL unless you relocate):** [TOO_FAR_AREA] (e.g. GCC countries you will not move to)

## Eligibility Filter (GCC)

Apply `10-gcc-market.md` Section 2 (Nationalization Gate) during `/scrape`'s Quick Fit Assessment: a posting that says "Saudi nationals only" / "للسعوديين فقط" (or another nationality the candidate does not hold), or requires an in-country/transferable visa the candidate lacks, is marked **Low** with the quoted wording, exactly like an undeclared-language override. For a candidate who **is** a national, a nationals-only posting is a highlight, not a filter.

## Language Filter

Your working languages and levels are in CLAUDE.md's Languages table. When filtering scraped results, apply `04-job-evaluation.md`'s Language Gate: a posting requiring a language you haven't declared at all is excluded; a posting requiring a higher level than you declared in a language you do work in is not excluded, flag it clearly instead (see `job-scraper/SKILL.md`'s Step 3 "Quick Fit Assessment" for how the flag surfaces in `/scrape` output). Postings simply *written* in a language you don't work in, that don't require it on the job, are fine.

## Date Filter

Only include jobs posted within the last 14 days, or with an application deadline that has not yet passed. If a posting date cannot be determined, include it but flag as "date unknown".

## Adapting Queries

If the user specifies a focus area, select queries from the matching category and also generate 2-3 custom queries for that focus. For example:
- "/scrape [focus_area]" -> relevant category queries + custom focus-specific queries
