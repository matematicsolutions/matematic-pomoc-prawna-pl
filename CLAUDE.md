# Legal Aid PL - organization configuration

> **DISCLAIMER.** MateMatic provides a tool (software). MateMatic does NOT provide legal aid, is NOT a law firm, does NOT practice as an attorney or legal adviser, and does NOT give legal advice. This plugin prepares a skeleton for the administrative work around legal counseling. Substantive advice, citation verification, and supervision rest entirely with the organization using it and its licensed lawyers. Responsibility for the outcome, legal compliance, and supervision lies with the organization, not MateMatic.

This file holds the organization configuration. It is filled in by the `konfiguracja` skill (run once at the start). Skills read this file instead of hard-coding legal rules (Article VII of the constitution), so the plugin works according to the organization's reality and current regulations.

---

## Part 0 - Preconditions: ethics and confidentiality (fill in BEFORE using with real cases)

- [ ] **Claude account tier and data retention/training policy** - confirm what applies to the organization and whether it meets GDPR requirements and internal confidentiality rules.
- [ ] **Client consent and disclosure of AI-assisted work** - determine whether and how the organization informs the people it helps; document it.
- [ ] **Handling confidential and sensitive data** - what enters the session, where results are stored, who has access, for how long, how staff turnover affects access.
- [ ] **Areas of heightened confidentiality** (e.g. domestic violence, immigration cases, some family cases) - decide whether the plugin is appropriate at all for these cases.
- [ ] **Anonymizing personal data** - recommendation: pseudonymize data before pasting it into a session (see the let-it-be skill).

Do not skip this part. The `konfiguracja` skill records these decisions as its first step.

---

## Part 1 - Organization profile (filled in by `konfiguracja`)

- **Organization type:** [legal aid point / law clinic / foundation / NGO]
- **Counseling areas:** [e.g. housing, family, consumer, immigration, benefits, debt]
- **Competence / jurisdiction:** [region, competent courts]
- **Eligibility criteria:** [rules by which the organization qualifies people - e.g. declaration, eligible group; enter the current ones per regulations and the organization's bylaws]
- **Conflict-check process:** [how the organization checks for conflicts of interest]
- **Funding sources / restrictions:** [if applicable - restrictions imposed by the grantor]

---

## Part 2 - Supervision model (choose one, filled in by `konfiguracja`)

The plugin adapts to how the organization actually supervises, not the other way around.

1. **Formal review queue** - a result directed to the client/court goes into a queue, a coordinator approves it, everything is logged.
2. **Configurable flags, informal review** - specific triggers mark a result with a `CHECK WITH COORDINATOR` label, without a queue mechanism.
3. **Lighter supervision** - standard draft labels on everything, the coordinator oversees through the organization's existing structure (case meetings, file review).

**Selected model:** [set by `konfiguracja`]

---

## Part 3 - Supervision and verification backbone (fixed, do NOT edit)

### Confidence markers (every skill applies them in the content)

Trust flags more than their absence. A missing flag does NOT mean the lawyer skips verification.

- `[AI DRAFT - requires analysis and supervision by a licensed lawyer]` - the baseline label on every result. This is a review label, not content for the client; remove it before sending anything.
- `[UNCERTAIN: reason]` - the skill is genuinely uncertain at this point.
- `[TO VERIFY: claim - check the source]` - a claim that is likely but unverified. The lawyer confirms it before relying on it.
- `[RESEARCH NEEDED: ...]` - a research gap in the memo skeleton, not a conclusion.
- `[LAWYER ANALYSIS: ...]` - a spot for analysis deliberately left empty.
- `[LAWYER CONCLUSION: ...]` - a spot for a conclusion deliberately left empty.
- `[FACT MISSING: ...]` - a required fact absent from the file. The lawyer fills it in; no guessing.
- `[GDPR/AI ACT LIMIT: ...]` - a flag when a planned action may touch GDPR or AI Act limits; the organization's compliance person weighs in.
- `CHECK WITH COORDINATOR BEFORE SENDING` / `BEFORE FILING` - the supervision label in "configurable flags" mode.

### Fixed rules

- Every result is a draft (Article I). Nothing goes out without the supervision model.
- No legal citation is taken for granted (Article III) - tag `[TO VERIFY]`.
- Without a case-law connector, every citation defaults to `[TO VERIFY]`.
- Skills do not hard-code the law (Article VII) - they read the configuration above.
- Audit trail: every material result is logged (model, date, sources, who) - Article V, AI Act art. 12.

---

## Part 4 - How the plugin learns

This profile is not static - tune it as you use it. Skills signal when a result used a default value worth refining in this file.
