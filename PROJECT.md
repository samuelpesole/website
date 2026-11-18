# PROJECT MEMORY — read this first, then only the files your task needs

Single source of truth for all agents. Keep it short (<150 lines). Only the CEO edits it;
other agents propose changes in their task comment ("Memory update: …").

## 1. Facts
- Owner & final approver: Samuel Pesole. Nothing goes live without his explicit OK.
- Who he is: BSc Defence & Security Sciences; MSc (in progress) Strategic Studies & Security Policy;
  works in IAM & cybersecurity, leads a team. Tone: academic, analytical (MSc level); not popular-science.
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
| Templates | `archetypes/analysis.md` (topics), `archetypes/paper.md` (paper reviews): `hugo new content --kind analysis posts/<slug>/index.md` |
| Site params / menus / languages | `config/_default/*.toml` |
| Contact form markup | `layouts/shortcodes/contact-form.html` |
| UI strings | `i18n/` |
Never read `themes/`, `public/`, `resources/` unless the task is about the theme itself.

## 3. Editorial pipeline — strict handoff contract
One sub-task per post, owned by the CEO. Each step = one agent, one run, one commit, one comment.
| Step | Agent | Input | Output (only this) | Done when |
|---|---|---|---|---|
| 1 | Research Writer | brief in task (question, 3-4 points, sources) | `index.md`, `draft: true` | all §4 checks pass |
| 2 | Fact-checker | `index.md` | fixes committed in place + checklist comment | every link opened, every DOI resolved to the cited title |
| 3 | Translator IT | checked `index.md` | `index.it.md` | same headings/links/front-matter keys |
| 4 | CEO | EN+IT | approval request to Samuel on SAM-6 | Samuel replies |
| 5 | Web Engineer | "approvo <slug>" | `draft: false`, `hugo --gc --minify` OK, PR | PR open |

Hard rules for every agent:
- R1 Touch only the files in your Output column. Never edit PROJECT.md, archetypes, other posts, config.
- R2 Commit locally on branch `post/<slug>` with message `<step>: <slug>`. Never push: the CEO pushes.
- R3 Final comment = exactly 3 lines: `Result: done|blocked` / `Files: …` / `Open: none|<question>`.
- R4 Blocked = set status `blocked` with one-line reason. Never mark `done` with work left or uncommitted.
- R5 No content about process, agents, tasks or next steps inside the post. The post is the paper only.
- R6 Don't rewrite another step's work. Fact-checker fixes facts, not style; Translator translates, doesn't edit.
- R7 One revision loop max per step; if still failing, hand back to the CEO with the reason.

## 4. Style rules (academic analysis — mandatory)
- Register: academic, analytical, third person by default; first person only for an explicit authorial judgement.
  No chatty openers, no "you", no exclamation marks, no listicles in place of argument.
- Template: `archetypes/analysis.md` (topic analysis) or `archetypes/paper.md` (paper review). Use its headings, nothing else.
  Forbidden sections: "What I'd do next", "Cosa farei adesso", "Takeaways", calls to action.
- Must contain: an explicit research question; a thesis of 2-3 claims; ≥1 analytical framework from peer-reviewed
  literature; facts separated from assessments; a confidence level for every attribution/causal claim; Limitations.
- 1500-2500 words. Sources: ≥8, ≥2 peer-reviewed; primary sources (government, standards, original research) preferred over news/blogs.
  Inline links + `## References` (Author (Year). Title. Venue. DOI/link), alphabetical.
- Unverifiable claim → `[unverified]` (IT: `[non verificato]`); max 1 per post, otherwise cut it.
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
- 2026-11-18 Samuel: posts must be academic analysis, not divulgativo. New template + strict handoff rules (§3-4).
- 2026-11-18 Team: Web Engineer, Research Writer, Fact-checker, Translator IT (Sonnet, on-demand only).
- 2026-11-18 Repo `samuelpesole/website` → URL under `/website/`. Rename to `samuelpesole.github.io` = optional later.
- 2026-11-18 Graphics: Blowfish, ocean, auto light/dark, narrow reading column, no photo yet.
- 2026-11-18 Contact via Formspree only; no email shown.

## 9. Open items
- Samuel: enable GitHub Pages (Settings → Pages → Source: GitHub Actions) and re-run deploy.
- Samuel: Formspree form id.
- Samuel: first post topics.
