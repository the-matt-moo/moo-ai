# Resume Tailor — Job-Specific Resume Agent

An LLM-powered agent that takes a job posting and your career history, then produces a tailored 2-page resume with ATS-optimized formatting and a fit-check report. It aligns your bullets to the job description's vocabulary, scores your fit against your own preferences, and never invents experience you don't have. Works with any LLM — ChatGPT, Claude, Gemini, local models, or anything else that accepts a system prompt.

## Features

- **JD vocabulary alignment** — rewrites your bullets using the job posting's terminology without fabricating skills
- **ATS-friendly output** — single-column layout, no tables/text boxes/headers that break applicant tracking systems
- **Fit-check warnings** — evaluates the posting against your personal preferences (location, employment type, industry, etc.) and surfaces concerns before you apply
- **Honest by design** — every claim traces back to your context files; nothing is invented or embellished
- **LLM-agnostic** — one system prompt that works in any chat interface or coding assistant

## Quick Start

1. **Clone the repo**
   ```bash
   git clone https://github.com/YOUR_USERNAME/resume-tailor.git
   cd resume-tailor
   ```

2. **Fill in your context files**
   Copy the example files in `context/` and replace the placeholder content with your real information:
   ```bash
   cp context/basic_information.example.md context/basic_information.md
   cp context/professional_summary.example.md context/professional_summary.md
   cp context/role.example.md context/company_role_title.md
   ```
   Create one role file per position in your career. See `context/README.md` for details.

3. **Use with your LLM** — see the platform-specific instructions below.

## Usage

### Any LLM (ChatGPT, Gemini, etc.)

1. Open a new chat session.
2. Copy the entire contents of `system-prompt.md` and paste it as your first message (or as a system/custom instruction if the platform supports it).
3. In the same or next message, paste the contents of each file in `context/` so the model has your career data.
4. Send the job posting URL or paste the full job description text.
5. The model will produce a tailored resume in Markdown and a fit-check summary.

### Claude Code

If you have Claude Code installed, the repo includes a native skill:

```bash
cd resume-tailor
# The resume-tailor skill is available automatically
# Pass a job posting URL or paste JD text
```

Claude Code will use `WebFetch` to pull the job description, run the full workflow, and write output files to `output/`.

### Local Models (Ollama, LM Studio)

Same workflow as "Any LLM" above. Note that local models typically cannot fetch URLs, so paste the full job description text directly instead of a link. For best results, use a model with a large context window (32k+ tokens) so it can hold your full career context alongside the job description.

## File Structure

```
resume-tailor/
├── system-prompt.md           # Complete LLM instructions — paste into any chat
├── context/                   # Your career data (gitignored, private)
│   ├── basic_information.md   # Name, contact, location, preferences
│   ├── professional_summary.md
│   └── <company>_<role>.md    # One file per role
├── references/
│   ├── fit-check.md           # Preference rules for fit evaluation
│   └── resume-template.md     # Section-by-section resume structure
├── output/                    # Generated resumes (gitignored)
├── CLAUDE.md                  # Claude Code integration (optional)
└── skills/resume-tailor/      # Claude Code skill (optional)
```

## How the Fit-Check Works

You define your job preferences in `context/basic_information.md` — things like employment type (full-time only?), acceptable locations, preferred industries, and minimum employer rating. The agent evaluates the job posting against each preference and produces a table:

| Preference | JD Signal | Status |
|---|---|---|
| Employment type | "Full-time" stated | Pass |
| Location/remote | Hybrid, Denver CO | Concern |
| Industry | FinTech | Pass |

The fit-check is advisory — the agent always produces the resume regardless of concerns, so you can decide whether to apply.

## Tips for Best Results

- **Use specific metrics** in your context files — "reduced deployment time by 40%" is far more useful than "improved deployments"
- **Keep context files current** — update them when you take on new responsibilities or complete projects
- **One role per file** — makes it easy to add, update, or remove positions
- **List technologies per role** — the agent uses these lists to avoid claiming tools you didn't use in that position
- **Define your preferences honestly** — the fit-check only helps if it reflects what you actually care about

## License

[MIT](LICENSE)
