# Fit-Check Rules

Apply each rule below against the JD facts extracted in Step 1 of the workflow. The user's specific preferences are defined in `./context/basic_information.md` under a `## Preferences` section. This file defines the *framework* — which categories to evaluate and how to classify each.

**These are warnings, not gates.** Always produce the resume regardless of fit-check results.

For each rule, classify as one of:

- **Pass** — JD clearly meets the user's stated preference
- **Concern** — JD clearly violates the user's stated preference
- **Unknown** — JD does not provide enough information to decide; flag it so the user knows to research before applying

If the user has not defined a preference for a given category in their `basic_information.md`, skip that rule entirely rather than guessing.

---

## 1. Employment Type

Look for the user's employment type preference in `basic_information.md` (e.g., "Full-time only" or "Open to contract and full-time").

- **Pass** if the JD's employment type matches the stated preference.
- **Concern** if the JD states a type the user has excluded (e.g., user says "no contract" and JD says "6-month contract").
- **Unknown** if the JD does not state an employment type.

Common JD signals: "Full-time," "Permanent," "FTE," "Contract," "C2H," "Contract-to-hire," "Consulting," "1099," "W2 contract," "Temp," "Part-time."

## 2. Work Location and Remote Policy

Look for the user's location and remote/hybrid preferences in `basic_information.md`. Users typically express these as rules around their home location, e.g.:

> *"I live in Austin, TX 78701. Remote is fine for non-local roles. Hybrid is acceptable within 30 miles. On-site only within 15 miles."*

Apply whatever rules the user has defined:

- **Pass** if the JD's location/remote policy satisfies the user's rules.
- **Concern** if the JD requires on-site or hybrid attendance in a location the user has excluded or that falls outside their distance thresholds.
- **Concern** if the JD requires relocation and the user hasn't indicated willingness.
- **Unknown** if the JD's location or remote policy is ambiguous.

## 3. Industry Alignment

Look for a preferred-industries list in `basic_information.md` (e.g., "FinTech, Aerospace, EdTech").

- **Pass** if the company is clearly in a preferred industry.
- **Concern** if the company is in an industry the user has explicitly excluded, or is not on the preferred list and the user has indicated "preferred industries only."
- **Unknown** if the industry is not obvious from the JD. Use general knowledge of the company name to infer before marking Unknown.

If the user has not listed industry preferences, skip this rule.

## 4. Employer Type

Look for employer-type preferences in `basic_information.md` (e.g., "Direct hire at established companies only, no staffing agencies").

- **Pass** if the hiring entity is clearly the end employer.
- **Concern** if the listing is from a staffing or placement firm (e.g., Robert Half, TEKsystems, Insight Global, Apex Systems, Randstad, Modis) or a consulting body shop, and the user has excluded these.
- **Unknown** if it's unclear whether the listing is a direct hire.

If the user has not expressed a preference, skip this rule.

## 5. Employer Rating

Look for a minimum rating threshold in `basic_information.md` (e.g., "4.0+ on Glassdoor/Indeed").

- **Pass** if a rating at or above the threshold is visible on Glassdoor, Indeed, Comparably, LinkedIn, or Blind.
- **Concern** if a rating below the threshold is visible.
- **Unknown** if no rating is visible from the JD page — note this as something the user should verify before applying.

If the user has not set a rating threshold, skip this rule.

## 6. Company Culture

Look for culture preferences in `basic_information.md`. The default framework uses Westrum's Organizational Culture typology (Generative / Bureaucratic / Pathological), but the user may express preferences differently.

Signals to look for in the JD:

- **Pass-leaning signals**: language emphasizing learning from failure, blameless postmortems, cross-functional collaboration, inner-source, internal mobility, mentoring, time for innovation/exploration, psychological safety.
- **Concern-leaning signals**: language emphasizing rigid SLAs as personal accountability, stack-ranking, mandatory PIPs, "fast-paced and demanding," "we work hard and play hard," "rockstar/ninja" framing, excessive emphasis on overtime or availability.
- **Unknown** is the default — most JDs do not give enough culture signal.

---

## Output Format

Produce a markdown table for the resume's `Fit Concerns` section:

```markdown
## Fit Concerns

| Preference | JD Signal | Status |
|---|---|---|
| Employment type | "Full-time" stated | Pass |
| Location/remote | Hybrid, Denver CO office, 3 days/week | Concern — outside user's range |
| Industry | FinTech (payments company) | Pass |
| Employer type | Direct hire (company name on listing) | Pass |
| Public rating | Glassdoor not visible from JD | Unknown — verify before applying |
| Culture | "Blameless postmortems" mentioned | Pass-leaning |
```

Add a one-line summary above the table:

> **Fit summary:** 4 Pass / 1 Concern / 1 Unknown — likely worth applying if the Denver hybrid is acceptable.

Only include rows for preference categories the user has actually configured. If the user defined 3 preferences, the table has 3 rows (plus the culture row, which is always evaluated if the user mentions culture preferences).
