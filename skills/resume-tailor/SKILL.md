---
name: resume-tailor
description: Tailor a resume to a specific job posting. Use this skill any time the user asks to "tailor a resume", "build a resume for this job", "customize my resume", "make a resume for [URL]", drops a job posting link, or otherwise asks for a resume targeted at a specific role. The skill ingests the job description, reads career context from ./context/, runs a soft fit-check against employment preferences, and produces a 2-page reverse-chronological resume in .md and .docx formats inside ./output/<Company>-<Position>/. Trigger this skill even when the user does not say the word "tailor" — any combination of a job posting reference plus a resume request should invoke it.
---

# Resume Tailor

Tailors a resume to a specific job posting. Output is a 2-page reverse-chronological resume in Markdown (and optionally .docx), plus a soft fit-check report.

## Inputs the skill needs

1. **A job posting URL or pasted JD text.** If the user did not provide one, ask before doing anything else.
2. **The `./context/` folder.** Read every `.md` file there — `basic_information.md`, `professional_summary.md`, and all role files. These are the source of truth for contact info, summary, and experience. Do not embellish beyond what these files state.

## Workflow

Follow these steps in order.

### 1. Confirm the URL and fetch the JD

Ask the user for the posting URL if not already provided. Fetch it with `WebFetch` (or ask the user to paste the text if fetching fails). Extract:

- Company name
- Job title
- Location and remote/hybrid policy
- Employment type (full-time, contract, contract-to-hire, etc.)
- Required and preferred skills/technologies
- Years of experience expected
- Industry signals

If the fetch fails, tell the user and ask them to paste the JD text directly.

### 2. Run the soft fit-check

Read `./references/fit-check.md` and apply each rule against the JD facts from step 1. Build a table of `Preference -> JD signal -> Pass/Concern/Unknown`. This becomes the **Fit Concerns** section in the markdown output. Do not refuse to proceed even if everything fails — these are warnings, not gates.

### 3. Read all context files

Read every `.md` file in `./context/`. Build a mental map keyed by role: company, dates, unit, responsibilities, and the explicit technology lists. Treat the tech lists as authoritative — if a technology is not listed for a role, do not claim it was used in that role.

### 4. Select and rewrite bullets

Score each bullet from each role against the JD's required and preferred skills. Pick the highest-density bullets per role until the resume fits two pages (typically 4–6 bullets for the most recent role, tapering to 1–2 for the oldest roles).

When rewriting, follow these rules:

- **Lead with the JD's vocabulary** when the source bullet describes the same thing in different words. Example: if the JD says "GitOps pipelines" and the source says "GitLab CI/CD pipelines," write "GitOps-style GitLab CI/CD pipelines" — both are accurate.
- **Never invent technologies.** If the JD asks for Kubernetes and the role lists OpenShift, say OpenShift (which is Kubernetes-based) — do not write "Kubernetes" if it is not in the source.
- **Never artificially bolster, imply, or over-represent expertise or experience.**
- **Quantify where the source already quantifies.** Do not fabricate metrics.
- **Use strong past-tense verbs** (Architected, Led, Automated, Migrated, Mentored) and present-tense for the current role.
- **One line per bullet** when possible; never more than two physical lines on the page.
- **Correct common misspellings, grammar, punctuation, and syntax mistakes.**
- **Avoid sounding sterile or AI-generated** — keep items succinct, professional, and as human as possible.

### 5. Assemble the resume

Use the template in `./references/resume-template.md`. Section order:

1. **Contact header** — from `basic_information.md`
2. **Professional Summary** — from `professional_summary.md`, tightened/retargeted to the JD
3. **Core Competencies** — technologies that appear in BOTH the JD and at least one role's tech list
4. **Professional Experience** — reverse-chronological, bullets from step 4
5. **Education** — from context files
6. **(Optional) Certifications / Additional** — only if present in context and relevant

Aim for 2 pages. If content overflows, trim oldest role bullets first.

### 6. Write outputs

Create the output folder: `./output/<Company>-<Position>/` (spaces → underscores, strip illegal path characters).

Write:

- `Resume.md` — the markdown source, with a `## Fit Concerns` section at the bottom (for the user's eyes, not for submission)
- `Resume.docx` — if the `docx` skill is available, produce an ATS-friendly single-column layout (no tables in body, no text boxes, no headers/footers)
- `JD_summary.md` — company, title, URL, fetch date, extracted JD facts

### 7. Present results to the user

Lead with the .docx if produced, then markdown. Surface the Fit Concerns summary inline in the chat so the user sees it without opening the file.

## What this skill does NOT do

- It does not write cover letters (that is a separate task).
- It does not auto-submit applications.
- It does not invent experience, certifications, or metrics not in `./context/`.
- It does not gate on fit — even a poor-fit posting gets a resume, just with loud warnings.
