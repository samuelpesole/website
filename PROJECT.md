# PROJECT MEMORY — read this first, then only the files your task needs

Single source of truth for all agents. Keep it short (<150 lines). Only the CEO edits it;
other agents propose changes in their task comment ("Memory update: …").

## 1. Facts
- Owner & final approver: Samuel Pesole. Nothing goes live without his explicit OK.
- Who he is: BSc Defence & Security Sciences; MSc (in progress) Strategic Studies & Security Policy;
  works in IAM & cybersecurity, leads a team. Tone: informal, accessible ("divulgativo").
- Site: Hugo + Blowfish theme, scheme `ocean`, light/dark auto. Repo `samuelpesole/website`, branch `main`.
- URL: https://samuelpesole.github.io/website/ (baseURL in `config/_default/hugo.toml`).
- Deploy: GitHub Actions on push to `main` (`.github/workflows/`). Pages source must be "GitHub Actions".
- Languages: EN primary (`file.md`), IT translation (`file.it.md`). Every page/post exists in both.
- Profiles: LinkedIn `samuel-pesole`, GitHub `samuelpesole`. No email/phone/city on the site. Nothing downloadable.
- Contact form: Formspree, id in `config/_default/params.toml` → `contact.formspreeId` (still `YOUR_FORM_ID` = pending).

## 2. Where things are (don't explore beyond this)
| Need | File |
|---|---|
| Home / About / Contact text | `content/_index*.md`, `content/about*.md`, `content/contact*.md` |
| Posts | `content/posts/<slug>/index.md` + `index.it.md` (page bundle) |
| Paper-post template | `archetypes/paper.md` (`hugo new content --kind paper posts/<slug>/index.md`) |
| Site params / menus / languages | `config/_default/*.toml` |
| Contact form markup | `layouts/shortcodes/contact-form.html` |
| UI strings | `i18n/` |
Never read `themes/`, `public/`, `resources/` unless the task is about the theme itself.

## 3. Editorial pipeline (one task per step, handoff via the same issue)
1. Research Writer → EN draft at `content/posts/<slug>/index.md`, `draft: true`.
2. Fact-checker → comment: OK / list of fixes / "do not publish" flags. Fixes only, no rewrite.
3. Translator IT → `index.it.md`, same front matter keys, glossary below.
4. CEO → asks Samuel for approval.
5. Web Engineer → sets `draft: false`, `hugo --minify` must pass, opens PR. Merge only after approval.

## 4. Style rules
- Post structure: In one sentence / Why it matters / Key points / body / What I'd do next.
- 600–1200 words. Links for every source. Mark unverified claims `[unverified]`.
- Slugs: kebab-case, English, same slug for both languages.
- Front matter: title, date, draft, description (≤160 chars), categories, tags.

## 5. Do NOT publish
- Anything about Factor-y internals, clients, projects, colleagues.
- Sensitive defence/security operational details; non-public info from events (e.g. Mare Aperto).
- Personal contact data.

## 6. Glossary EN → IT (keep consistent; add terms here)
| EN | IT |
|---|---|
| critical infrastructure | infrastruttura critica |
| identity and access management (IAM) | gestione delle identità e degli accessi (IAM) |
| Zero Trust | Zero Trust (non tradurre) |
| threat | minaccia |
| resilience | resilienza |
| NIS2 / DORA | NIS2 / DORA (non tradurre) |

## 7. Token rules for every agent
- Read this file + only the files listed for your task. No repo-wide searches, no reading the theme.
- Don't re-read the full issue thread: the task description is the brief.
- Short comments: result, files touched, open questions. No recaps.
- Stop as soon as the done criteria are met.

## 8. Decisions log (newest first, one line each)
- 2026-11-18 Team: Web Engineer, Research Writer, Fact-checker, Translator IT (Sonnet, on-demand only).
- 2026-11-18 Repo `samuelpesole/website` → URL under `/website/`. Rename to `samuelpesole.github.io` = optional later.
- 2026-11-18 Graphics: Blowfish, ocean, auto light/dark, narrow reading column, no photo yet.
- 2026-11-18 Contact via Formspree only; no email shown.

## 9. Open items
- Samuel: enable GitHub Pages (Settings → Pages → Source: GitHub Actions) and re-run deploy.
- Samuel: Formspree form id.
- Samuel: first post topics.
