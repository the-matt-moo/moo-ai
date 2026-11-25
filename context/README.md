# Context — Your Career Data

This folder is where you put **your** career information. The resume agent reads every `.md` file here to source experience, contact details, and preferences when tailoring a resume to a job posting.

## Required files

| File | Purpose |
|---|---|
| `basic_information.md` | Name, contact info, location, employment preferences |
| `professional_summary.md` | Your master 3–4 sentence summary |
| `education.md` | Degrees, certifications, training |

## Role files

Create one file per role you've held, named `Company-Title.md` (e.g., `Acme_Corp-Senior_Backend_Engineer.md`). Each file should include the job title, company, location, dates, a technology list, and achievement bullets. The more specific you are, the better the agent can match your experience to a job posting.

## Tips

- **Be specific about technologies per role.** List every tool, language, and platform you used in that position. The agent treats each role's tech list as authoritative — it will not claim you used a technology in a role unless it appears in that role's list.
- **Include metrics where you have them.** "Reduced deploy time by 40%" is stronger than "Improved deploy time." The agent will not fabricate numbers.
- **List core competencies per role.** A dedicated `Core Competencies and Technologies` section in each role file makes keyword matching reliable.
- **Don't embellish.** Write what actually happened. The agent's job is to reframe and prioritize your real experience for each posting, not to invent it.

## Getting started

The `.example.md` files in this folder are templates. To use them:

1. Copy each one without the `.example` suffix (e.g., `basic_information.example.md` → `basic_information.md`)
2. Replace the placeholder content with your own data
3. Create additional role files following the pattern in `role.example.md`

## Privacy

The `context/` folder is listed in `.gitignore` so your personal data stays local by default. The `.example.md` files are tracked (they contain only fictional sample data). If you fork or clone this repo, your real context files will not be pushed unless you explicitly add them.
