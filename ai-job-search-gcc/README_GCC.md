# AI Job Search - Saudi Arabia & GCC edition

This folder is a copy of [ai-job-search-dev/ai-job-search](https://github.com/ai-job-search-dev/ai-job-search)
(MIT licence, see `LICENSE`), adapted for job hunting in **Saudi Arabia** and the other **GCC**
countries (UAE, Qatar, Kuwait, Bahrain, Oman). The upstream README (`README.md`) still describes
the full workflow; this page lists what is different and how to start.

## What was changed for the GCC

| Area | Change |
|---|---|
| **Market rules** | New `.claude/skills/job-application-assistant/10-gcc-market.md`: Saudization / Nitaqat and other nationalization programmes, Iqama and visa status, monthly salary packages (basic + housing + transport), end-of-service, work week, Arabic vs English, GCC red flags (e.g. being asked to pay visa fees), job sources, official sources to check. |
| **Eligibility** | A **Nationalization Gate** runs before scoring in `/apply`, `/rank` and `/scrape`: "Saudi nationals only" / "للسعوديين فقط", "UAE Nationals", "transferable Iqama", "in-country only" are checked against your nationality and visa status. If you are a Saudi national, Saudization roles are highlighted as a strength. |
| **Your profile** | `CLAUDE.md` has a new **GCC Profile** block (nationality, residence, visa/Iqama, target GCC cities, notice period, expected monthly package, licence, professional registrations such as SCE/SCFHS/SOCPA, which personal details to show on the CV). `/setup` asks for these. |
| **Job search** | `search-queries.md` is pre-filled for Saudi Arabia first, then the GCC: LinkedIn (CLI, GCC locations), freehire (CLI, `--country SA`), and Bayt, GulfTalent, Naukrigulf, Indeed SA/AE/QA/KW/BH/OM, Jadarat and Tanqeeb through WebSearch. English **and Arabic** query templates. |
| **CV** | GCC personal-details line (nationality, location, visa status, notice period; date of birth, marital status and photo only if you opt in), Arabic section headings, Arabic-CV guidance. |
| **Cover letter** | GCC tone, Arabic salutations and closing (وتفضلوا بقبول فائق الاحترام والتقدير). Arabic postings get Arabic letters. |
| **Interview prep** | Notice period, package-based salary answer, Iqama transfer, site/rotation questions. |
| **Salary tool** | Recognises GCC company suffixes (LLC, W.L.L., PJSC, Q.P.S.C., SAOG/SAOC, KSCP, B.S.C., FZ-LLC, FZE, DMCC). Use monthly SAR/AED/... values. |

The Danish job-board scrapers from upstream are still in `.agents/skills/` but ship **disabled**;
they do nothing unless you enable them.

## Quick start

You need [Claude Code](https://claude.com/claude-code), Python 3.10+, [Bun](https://bun.sh) and a
LaTeX distribution with `lualatex` and `xelatex` (see `SETUP.md`).

```bash
cd ai-job-search-gcc
```

```bash
python3 tools/install_portal_clis.py
```

```bash
claude
```

Then, inside Claude Code:

1. `/setup` - build your profile (answer the GCC questions: nationality, Iqama/visa, cities, package).
2. `/scrape` - find new jobs in Saudi Arabia / GCC.
3. `/rank` - score a long list and get a shortlist.
4. `/apply <job URL>` - fit evaluation, tailored CV and cover letter.
5. `/interview` and `/outcome` - prepare and track.

Keep your copy in a **private** repository: `/setup` writes personal data into tracked files.

## Good to know

- **Gulf job boards and scraping.** Bayt, GulfTalent, Naukrigulf, Indeed and Jadarat are searched
  through WebSearch `site:` queries, which work without extra code. If you use one board heavily,
  run `/add-portal` on your own computer to build and live-test a dedicated search CLI for it.
- **Rules change.** Saudization quotas, restricted professions and visa rules change often. The
  assistant is instructed to quote the posting and point you to the official source (HRSD, Qiwa,
  MOHRE, ...) instead of inventing rules.
- **LinkedIn** use is personal and low-volume only (see `.agents/skills/linkedin-search/SKILL.md`).

---

## ملخص بالعربية

هذه نسخة من أداة **AI Job Search** معدّلة للبحث عن وظائف في **المملكة العربية السعودية** ودول **مجلس التعاون الخليجي**.

- **بوابة التوطين:** يفحص المساعد عبارات مثل «للسعوديين فقط» و«إقامة قابلة للنقل» مقابل جنسيتك وحالة إقامتك قبل التقييم، ويبرز وظائف السعودة كنقطة قوة إذا كنت سعودي الجنسية.
- **ملفك الشخصي:** أضيف قسم «GCC Profile» في `CLAUDE.md` (الجنسية، الإقامة، المدن المستهدفة، فترة الإشعار، الراتب الشهري المتوقع بالريال، الرخص والعضويات المهنية).
- **البحث:** لينكدإن وبيت وجلف تالنت ونوكري الخليج وإنديد وجدارات، بكلمات بحث عربية وإنجليزية.
- **السيرة الذاتية وخطاب التغطية:** أعراف الخليج، عناوين الأقسام بالعربية، وخطابات عربية للإعلانات العربية.
- **الرواتب:** المقارنة على أساس الحزمة الشهرية (الأساسي + السكن + المواصلات).

للبدء: افتح مجلد `ai-job-search-gcc` ثم شغّل `claude` واكتب `/setup`.
