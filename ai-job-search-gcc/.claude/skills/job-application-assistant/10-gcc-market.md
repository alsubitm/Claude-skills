---
framework_version: 1.0.0-gcc
---

# GCC Market Guide (Saudi Arabia, UAE, Qatar, Kuwait, Bahrain, Oman)

This fork is set up for the job market in **Saudi Arabia** (the default home market) and the
other **GCC** countries. Every skill and command that evaluates, searches, or drafts should read
this file alongside the generic framework files. Where this file and a generic file disagree on
a market convention, this file wins; the honesty, trust-boundary and verification rules in the
generic files always apply.

> **Facts change.** Nationalization quotas, restricted-profession lists, visa rules and labour-law
> details are revised often. Treat every rule below as a starting point. Before telling the user
> a role is closed to them, quote the posting, and when a decision turns on a regulation, verify it
> on the official source listed in the table at the end. Never invent a quota, percentage or
> article number.

---

## 1. Candidate fields this market needs

`/setup` records these in CLAUDE.md's **GCC Profile** block. Every gate below reads them.

| Field | Why it matters |
|---|---|
| **Nationality** (and any second nationality) | Nationalization gate (Section 2). The single most decisive field in the GCC. |
| **Current country of residence** | "In-country candidates only" is very common. |
| **Residency / visa status** per GCC country | e.g. Saudi national; Iqama holder (transferable or not); UAE residence visa (employment / Golden / family-sponsored); visit visa; none. |
| **Iqama / visa transferability** | A transferable Iqama or an in-country visa is often a hard requirement for expat hires. |
| **Notice period / availability** | Asked in nearly every GCC application form. |
| **Target countries and cities** | e.g. Riyadh, Jeddah, Dammam/Khobar (Eastern Province), NEOM/Tabuk; Dubai, Abu Dhabi; Doha; Kuwait City; Manama; Muscat. |
| **Willing to relocate within the GCC?** | Drives the Location & Logistics dimension. |
| **Driving licence** (Saudi / GCC / international) | Field, sales and site roles frequently require a valid local licence. |
| **Salary expectation** as a monthly package, in local currency | GCC offers are quoted monthly. See Section 5. |
| **Professional registrations** | e.g. Saudi Council of Engineers (SCE) membership, SCFHS for healthcare, SOCPA for accountants, UAE Ministry/DHA/DOH licences. Many roles require them. |

## 2. Nationalization Gate (Saudization / Emiratization / Qatarization / Kuwaitization / Bahrainization / Omanization)

Run this as part of `04-job-evaluation.md`'s **Eligibility Gate**, before scoring.

All six GCC states run workforce-nationalization programmes. In Saudi Arabia this is
**Saudization** under the **Nitaqat** programme of the Ministry of Human Resources and Social
Development (HRSD). Some professions are reserved for citizens by ministerial decision, and many
employers advertise roles only to nationals to meet their quota.

Read the posting's eligibility wording **verbatim** (in English and in Arabic) and classify:

| Posting wording | Candidate | Verdict |
|---|---|---|
| "Saudi nationals only", "Saudi national", "Saudization role", "للسعوديين فقط", "سعودي الجنسية" (likewise "UAE Nationals only" / "Emirati" / "مواطن", "Qatari nationals", "Omani nationals", "Kuwaiti", "Bahraini") | Not a national of that country | **FAIL - hard stop.** Quote the wording. Do not score or draft. |
| Same wording | Is a national of that country | **PASS - a positive.** Mention it naturally in the application where the form or letter asks (e.g. "Saudi national, available immediately"). |
| "GCC nationals" / "مواطني دول مجلس التعاون" | Any GCC national | PASS. Others: FAIL. |
| "Must be in KSA with a transferable Iqama", "local candidates only", "must hold a valid UAE residence visa", "in-country only" | Status in CLAUDE.md does not match | **FAIL** (or FLAG if the profile says the status is about to change; show the dates). |
| "Visa will be provided", "relocation package", "international applicants considered" | Expat abroad | PASS. Note it as a positive. |
| **Silent**, but the role is in a profession the user knows (or you verified on HRSD/MOHRE) to be reserved for nationals in that country | Not a national | **FLAG - unverified.** Do not claim a rule you did not verify. Tell the user what to check. |
| Silent, nothing suggests a restriction | Anyone | PROCEED. |

**Rules that are easy to get wrong:**

1. **Do not infer nationality from a name.** Use only the Nationality field in CLAUDE.md.
2. **Do not invent restricted-profession lists or quota percentages.** If you are not certain,
   FLAG and point to the official source.
3. **Being a national is an advantage, not a footnote.** For Saudi candidates, a Saudization-targeted
   role is often the best-odds application in the pool. Say so in the evaluation.
4. In `/rank`, a Nationalization FAIL is reported as `location_verdict: "FAIL"` (eligibility and
   logistics share that veto) with the quoted wording as the first `gaps` bullet, so it is excluded
   from the shortlist exactly like a relocation FAIL.

## 3. Language

- **English** is the working language of most private-sector and multinational roles across the GCC.
- **Arabic** is required or strongly preferred in government, semi-government, customer-facing,
  legal, HR, and many Saudization roles. Postings say "Arabic native speaker", "bilingual
  (Arabic/English)", "يجيد اللغتين العربية والإنجليزية".
- Apply `04-job-evaluation.md`'s Language Gate unchanged. Arabic must be in the candidate's
  Languages table for an Arabic-required posting to pass.
- Write search queries in **both English and Arabic** when Arabic is in the Languages table
  (see `job-scraper/search-queries.md`).
- Posting written in Arabic → cover letter in Arabic (the generic "match the posting's language"
  rule). The CV stays in the `CV language` from CLAUDE.md (English by default; see Section 6).

## 4. Location & logistics

- **Work week:** Sunday-Thursday in Saudi Arabia, Qatar, Kuwait, Bahrain and Oman. The UAE
  federal government works Monday-Friday (with a short Friday), and many UAE private employers
  follow it. Note the schedule in the evaluation only when it conflicts with a user constraint.
- **Ramadan:** reduced working hours are standard; interview scheduling slows. Mention when
  timing an application.
- **Remote/site work:** giga-project and energy roles (NEOM, Red Sea, Eastern Province plants,
  offshore) are often rotational or site-based with camp accommodation. FLAG rotation patterns
  (e.g. 28/28) against the user's constraints.
- **Relocation within the GCC** is a FAIL only if the user said they will not relocate.

## 5. Compensation (salary benchmark adjustments)

- GCC offers are normally quoted **monthly**, as a **package**: basic salary + housing allowance +
  transportation allowance (+ sometimes other allowances). Always compare package to package,
  and ask whether a posting's figure is basic or total.
- Other common components: annual bonus, annual air tickets (home flights for expats), medical
  insurance (mandatory, check family coverage), children's education allowance, relocation.
- **End-of-service benefit (gratuity)** is calculated on the basic salary in both Saudi Arabia
  and the UAE, so a low basic with high allowances reduces it. Point this out when an offer is
  allowance-heavy, but do not quote a formula unless you have verified it for that country.
- **Social insurance:** GOSI in Saudi Arabia (mandatory for Saudis, with different coverage for
  expats); GPSSA in the UAE for Emiratis. Contributions affect net pay for nationals.
- **Income tax:** the GCC states currently levy no personal income tax on employment income;
  Oman has announced a personal income tax on high earners from 2028. Verify before relying on it.
- **Currencies:** SAR (Saudi riyal), AED (dirham), QAR (Qatari riyal), KWD (Kuwaiti dinar),
  BHD (Bahraini dinar), OMR (Omani rial). SAR, AED, QAR, BHD and OMR are pegged to the US dollar;
  KWD is pegged to a basket. Always state the currency.
- **Benchmarks:** when no `salary_data.json` exists, use public GCC salary guides found via
  WebSearch (recruiter salary guides for the Middle East, Glassdoor, Bayt salary pages) and say
  which source and year each number came from. Never present a guessed number as a benchmark.
  To build `salary_data.json` for the GCC, see `tools/README_SALARY_TOOL.md` (use absolute
  monthly values in your currency; record source and year in `metadata`).

## 6. CV conventions (applies on top of `05-cv-templates.md`)

GCC recruiters and ATS systems expect a short **personal details** line under the header. Include
only what the user approved in `/setup`:

- **Include by default:** Nationality, current location (city, country), visa/Iqama status (and
  "transferable" when true), notice period/availability, languages.
- **Optional, user's choice:** date of birth, marital status, driving licence, photo. These are
  still common in the region, but they are not required by multinational employers and a photo
  can break ATS parsing. Default: no photo, no date of birth, no marital status, unless the user
  asked or the employer's form requires it.
- **Professional registration numbers** (SCE, SCFHS, SOCPA, DHA, etc.) go next to the relevant
  qualification.
- **Two pages** remains the standard (the generic rule holds).
- **Language:** English is the default and is accepted by almost all private and multinational
  employers. An Arabic CV is useful for government and some semi-government employers. The
  bundled moderncv and cover.cls templates are built and verified for Latin script; for an Arabic
  CV or letter, compile with `lualatex`/`xelatex` and an Arabic-capable font (e.g. Amiri or
  Noto Naskh Arabic) using babel or polyglossia right-to-left support, and run the full
  compiled-PDF and ATS text-layer verification before presenting it. If that verification fails,
  tell the user rather than presenting a broken document.
- Example personal-details line (LaTeX, inside the CV after `\makecvtitle`):
  `\cvitem{Personal}{Saudi national \textbullet{} Riyadh, Saudi Arabia \textbullet{} Available immediately}`
  `\cvitem{Personal}{Indian national \textbullet{} Dubai, UAE \textbullet{} UAE employment visa \textbullet{} 30 days' notice}`

## 7. Cover letter conventions (applies on top of `06-cover-letter-templates.md`)

- Tone: formal and respectful; slightly more formal than Northern European or US norms.
- Salutation if the name is unknown: "Dear Hiring Manager," / Arabic: "السادة / إدارة الموارد البشرية المحترمين،"
- Arabic opening line (optional): "تحية طيبة وبعد،"
- Closing: "Kind regards," or "Yours sincerely," / Arabic: "وتفضلوا بقبول فائق الاحترام والتقدير،"
- State availability (notice period) and, for expats, visa/Iqama status in one short sentence near
  the end, when the posting asks for in-country or transferable candidates.
- Linking motivation to **Saudi Vision 2030** (or UAE/Qatar national visions) is welcome **only
  when concrete and true** (the employer's actual programme, a real sector goal). Never as filler.
  The writing-style rules in `03-writing-style.md` still apply (no clichés, no em-dashes).

## 8. Interview preparation (applies on top of `07-interview-prep.md`)

- Expect questions on: notice period, visa/Iqama transfer, current and expected **package**
  (basic + allowances), willingness to work on site/rotation, Arabic level, and for nationals,
  interest in long-term career growth within the company.
- Prepare a package-based salary answer: state the expected monthly total in local currency and
  which components it assumes.
- Good questions to ask: package breakdown, medical coverage for family, annual tickets, probation
  length, working hours and week, career path, and (for expats) who handles visa/Iqama transfer
  and costs.

## 9. Red flags specific to GCC job ads

Flag these to the user (observations, never accusations):

- The employer or an agent asks the **candidate to pay** for a visa, recruitment, medical or
  "processing" fee. Charging workers recruitment fees is prohibited in Saudi Arabia and the UAE;
  treat any such request as a strong scam signal and tell the user.
- Offer letters arriving before any interview, contact only via personal email/WhatsApp, or a
  company name that does not match its email domain.
- "Visit visa now, work visa later" arrangements.
- A posting copied identically across many GCC cities with no company name (the generic
  mass-posting rule in `/scrape` Step 2.5 applies).

## 10. Job sources

`/scrape` uses these (CLI where one is installed; WebSearch `site:` fallback otherwise). The full
query templates are in `.claude/skills/job-scraper/search-queries.md`.

| Source | Coverage | Access in this fork |
|---|---|---|
| LinkedIn Jobs | All GCC | `linkedin-search` CLI (enabled), pass a GCC `--location` |
| freehire.me | Tech roles, global | `freehire-search` CLI (enabled) |
| Bayt.com | All GCC, largest regional board | WebSearch fallback (`site:bayt.com`); build a CLI with `/add-portal` on your own machine |
| GulfTalent | All GCC, professional/mid-senior | WebSearch fallback (`site:gulftalent.com`) |
| Naukrigulf | All GCC | WebSearch fallback (`site:naukrigulf.com`) |
| Indeed (sa / ae / qa / kw / bh / om) | Country sites | WebSearch fallback (`site:sa.indeed.com`, ...) |
| Jadarat (جدارات) | Saudi Arabia - national employment platform (public and private sector) | WebSearch fallback (`site:jadarat.sa`); applying requires a national login |
| Tanqeeb, Glassdoor | Aggregators | WebSearch fallback |
| Employer careers pages | e.g. Saudi Aramco, SABIC, STC, PIF and its portfolio (NEOM, Red Sea Global, ROSHN, Qiddiya, Diriyah), ACWA Power, Ma'aden, Elm, SDAIA, major banks; ADNOC, Emirates Group, Etisalat (e&), Mubadala; QatarEnergy; KNPC; Bapco; OQ | WebSearch `site:` queries per company |

## 11. Official sources to verify regulations

| Country | Labour / nationalization | Work contracts & transfers |
|---|---|---|
| Saudi Arabia | Ministry of Human Resources and Social Development (hrsd.gov.sa) | Qiwa (qiwa.sa); GOSI (gosi.gov.sa) |
| UAE | Ministry of Human Resources and Emiratisation (mohre.gov.ae) | MOHRE; Nafis (for Emiratis) |
| Qatar | Ministry of Labour (mol.gov.qa) | Ministry of Labour |
| Kuwait | Public Authority for Manpower (manpower.gov.kw) | PAM |
| Bahrain | Labour Market Regulatory Authority (lmra.gov.bh) | LMRA |
| Oman | Ministry of Labour (mol.gov.om) | Ministry of Labour |

Use these only to verify a specific question that decides an evaluation. They are reference
sources, not something to crawl.
