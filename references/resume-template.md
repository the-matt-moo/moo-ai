# Resume Template — 2-Page Reverse-Chronological

This skeleton defines the section order and formatting rules for the tailored resume. The markdown output should follow it section-for-section. Any .docx rendering should preserve the order and visual hierarchy but use a clean ATS-friendly single-column layout.

## Skeleton

```markdown
# [YOUR NAME]

[City, State]  |  [Phone]  |  [Email]  |  [LinkedIn or Portfolio URL]

---

## Professional Summary

[2–3 sentences. Start from professional_summary.md and retarget the seniority and stack
to the JD. Lead with years of experience, primary domain, and the 1–2 capabilities the
JD weights heaviest. Do not invent — only sharpen and focus.]

---

## Core Competencies

[2- or 3-column compact list of technologies/skills that appear in BOTH the JD and at
least one role's tech list in ./context/. Aim for 12–18 items. Group loosely by category
(e.g., Languages | Frameworks | Cloud & Infrastructure | CI/CD | Observability | Other).
Avoid one-offs that aren't in the JD — those belong in role bullets, not here.]

---

## Professional Experience

### [Most Recent Title]  —  [Company], [City, State]
*[Start Year] – Present*

- [4–6 bullets. Present tense. Lead with the bullet most aligned to the JD.
  Each bullet must trace back to a source line in the corresponding context file.]

### [Previous Title]  —  [Company], [City, State]
*[Start Year] – [End Year]*

- [3–4 bullets. Past tense.]

### [Earlier Title]  —  [Company], [City, State]
*[Start Year] – [End Year]*

- [2–3 bullets, condensed.]

### [Earliest Relevant Role]  —  [Company], [City, State]
*[Start Year] – [End Year]*

- [1–2 condensed bullets, or omit if page-constrained.]

---

## Education

[From the education context file, verbatim. Degree, institution, year if present.]

---

## Fit Concerns

[Markdown table from the fit-check step. THIS SECTION IS FOR THE USER'S EYES ONLY —
strip it before producing the .docx or any version submitted to employers.]
```

## Length Guidance

- **Page 1**: header, summary, competencies, most recent role, and the next 1–2 roles.
- **Page 2**: remaining roles, education, optional certifications.
- **Total bullets across all roles**: target 18–24. Going over 24 risks overflowing page 2.
- If content runs over, trim oldest/least-relevant role bullets first.

## Bullet Rewriting Rules

These show the right level of JD-alignment. Each example starts from a hypothetical source bullet and ends with a tailored version. **Never** produce a bullet containing a technology not listed in the source role's tech list.

### Example A — JD asks for "Kubernetes"; source role lists Docker Swarm

**Source:** *"Manage and scale containerized microservices across a 200-node Docker Swarm cluster supporting production workloads."*

**Tailored:** *"Manage and scale containerized microservices across a 200-node Docker Swarm cluster, orchestrating production workloads with container-native tooling."*

**Why:** Does not falsely claim Kubernetes. Strengthens the language around container orchestration so the ATS picks up the concept, while staying truthful. If Docker Swarm and Kubernetes serve the same JD need, the recruiter can see the transferable skill.

### Example B — JD asks for "CI/CD pipeline development"; source describes Jenkins and GitHub Actions

**Source:** *"Built and maintained automated build and deployment pipelines using Jenkins and GitHub Actions for a team of 40 engineers."*

**Tailored:** *"Developed and maintained CI/CD pipelines (Jenkins, GitHub Actions) serving 40 engineers, automating build, test, and deployment stages to accelerate release velocity."*

**Why:** Leads with the JD's exact phrase "CI/CD pipelines," preserves the specific tools from the source, and adds an outcome ("accelerate release velocity") that the source implies through the automation context.

### Example C — JD wants "infrastructure as code"; source describes Terraform

**Source:** *"Wrote Terraform modules to provision cloud infrastructure across three AWS regions."*

**Tailored:** *"Architect infrastructure-as-code solutions using Terraform to provision and manage cloud environments across three AWS regions, ensuring consistent and repeatable deployments."*

**Why:** Leads with the JD's keyword phrase "infrastructure-as-code," keeps Terraform and AWS (both in source), adds a professional outcome clause grounded in what IaC inherently provides.

### Example D — JD mentions "mentoring" or "technical leadership"

**Source:** *"Helped onboard new team members and created training documentation for internal tools."*

**Tailored:** *"Mentor new engineers through structured onboarding, designing training curriculum covering internal tooling, platform architecture, and team workflows."*

**Why:** Elevates the verb from "helped" to "mentor," restructures to lead with the leadership signal the JD values. All claims stay within the source bullet's scope.

## Formatting Rules (ATS Compatibility)

- **No tables** in the body of the .docx — ATS parsers mangle them. Use plain paragraph text with separators (em-dash or pipe) between role/company/location.
- **No text boxes, sidebars, headers, footers, page numbers in headers** — same ATS reason.
- **No color other than black** for body text. A single accent color for section headers is acceptable if the rendering tool supports it cleanly.
- **No graphics, icons, or images** — ATS cannot parse them.
- **Spell out acronyms** that aren't in the JD or aren't widely known on first use.
- **Single-column layout only** — two-column layouts break most ATS parsers.
- **Standard fonts**: use widely available fonts (Calibri, Arial, Georgia, Garamond, Times New Roman) at 10–11pt for body text.
- **Consistent date formatting**: use the same format throughout (e.g., "2020 – 2023" or "Jan 2020 – Mar 2023").

## Things to Avoid

- More than 24 total bullets across all roles.
- Any technology, certification, year, or metric not present in `./context/`.
- Buzzwords without substance ("synergy," "leverage," "paradigm shift").
- Starting multiple bullets with the same verb.
- Passive voice ("was responsible for") — always use active voice.
- First-person pronouns (I, me, my) — resume bullets are implicitly first-person.
- Paragraphs in the experience section — bullets only.
