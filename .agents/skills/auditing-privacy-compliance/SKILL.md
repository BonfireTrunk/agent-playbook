---
name: auditing-privacy-compliance
description: "Audits any software product against privacy law from its customer's side: what the product must let a controller, business or Data Fiduciary do, or offer as a setting, under the GDPR, UK GDPR, CCPA/CPRA and other US state laws, HIPAA, GLBA, FERPA, COPPA, India's DPDP Act and the EU AI Act. Holds a capability checklist with laws and priorities, the jurisdiction comparison and the strictest common design, the research method with source grades, a dated list of changing laws and open points, and the gap-analysis report shape. Use when designing or reviewing a feature that holds personal data, writing a privacy gap analysis or answering a customer's privacy questionnaire, comparing privacy laws, or when GDPR, CCPA, DPDP, data subject or access requests, DSAR, erasure, redaction, retention, legal hold, audit or read logs, sub-processors, a DPA, data residency, breach notification, automated decisions or children's data come up."
---

# Privacy-law capabilities a product must offer

**Scope.** What a software product must let its customer do, or offer as an option or setting, so that the customer can comply with privacy law using the product. The aim: a customer never finds that something a privacy law required of it could not be done with the product. The customer is the controller (GDPR), the business (CCPA) or the Data Fiduciary (DPDP); the vendor is its processor, service provider or Data Processor. The vendor's own duties as processor: `references/capabilities.md`, Processor duties. Application security (password hashing, log fields, uploads): `securing-applications`.

**Not legal advice.** Every report built with this skill says so in its first lines. The skill finds capability gaps. The customer's lawyer decides legal bases, periods and scope.

## Laws change: re-verify before relying on this

The facts here were checked against the sources on 2026-11-28. Before using them:

- Re-check every date in `references/dates-and-sources.md` that has passed since then or falls within the next year. Due after the check: CCPA automated-decision rules (1 Jan 2027), Oklahoma and Louisiana (1 Jan 2027), HIPAA Privacy Rule amendments (in force 19 Jan 2027, compliance 19 Jul 2027), Alabama (1 May 2027), India's DPDP main duties (13 May 2027), CCPA risk assessments for older processing (31 Dec 2027), Vermont (1 Jan 2028, unverified).
- Check for US state privacy laws enacted since the check. New ones usually take effect in January.
- Check pending rules: the HIPAA Security Rule rewrite was still a proposal on 2026-11-28.
- Check whether the open points in `references/dates-and-sources.md` have been closed.
- Write the date of your check, and what changed, into the report.

## The method

1. **Scope.** List the laws that reach the product's customers: where their people are, their sector (health, finance, schools), and whether the product holds staff data (most US state laws exclude it; the GDPR, UK GDPR, CCPA and DPDP do not). Tables: `references/jurisdictions.md`.
2. **Read the product.** For each capability, find what the product does in its specs and code, and name the store, screen or job. Never assess from an impression.
3. **Walk the checklist** below, every row, including the ones that look not to apply. Write "not applicable, because ..." rather than skipping.
4. **Primary texts first.** Read the statute, regulation or gazette itself. Grade every claim by its source (table below). A claim that rests only on secondary sources, or on nothing, is marked **UNVERIFIED**.
5. **Mark lawyer points.** A question only the customer's lawyer can decide is marked **LAWYER**, never answered by the audit. Standard list: `references/report.md`.
6. **Write the gap analysis** in the shape in `references/report.md`. It goes in the repo's git-ignored `temp/` folder unless the user names another place.

| Grade | Source |
|---|---|
| Primary (the default, not marked) | The official text: statute, regulation, gazette, the Federal Register or eCFR (their official APIs included), or a provider's own legal or docs page |
| Archived official | A Wayback Machine copy of the official page, read in raw text, with the snapshot date |
| Mirror | A third-party copy of the statute, because the official host refused |
| Official guidance | A ministry's or regulator's own page (GOV.UK, the ICO, the EDPB), not the law itself |
| Secondary | Law firms or trackers only. The claim is **UNVERIFIED** |

Rules for every finding:

- Cite only provisions you have read. Example: the UK "reasonable and proportionate" search rule is confirmed only in official guidance, so no article number is cited for it.
- An open point stays open. Never write an **UNVERIFIED** claim as settled; carry it into the report's open list.
- Describe a gap from the customer's side ("the customer cannot ..."), with a failure example: a real kind of person, a real request and the deadline that is missed.
- Options include the standard capability a customer expects, not only narrow repairs. Each cost is a concrete consequence (a missed deadline, a data copy that must be protected), never effort.
- Defaults follow `~/.agents/instructions/product.md`: restrictive when unset, optional behaviour off. Example: a feature that sends personal data to a new sub-processor starts off until an administrator turns it on.

**Priorities:**

- **Must-have:** a law requires the capability, and without it the customer cannot comply using the product.
- **Should-have:** a law expects it, or a customer in a common situation (EU staff, a regulated sector) needs it.
- **Nice-to-have:** good practice, or needed only by an unusual customer.

## From audit to code

Law citations belong in the audit report and the customer-facing compliance documents, never in code. In software they are features: an export, an erasure, a retention setting, a hold.

- No law names or article, section or rule numbers in identifiers, comments, setting keys, error codes, log lines or UI text. Example: `closedRecordRetentionDays`, not `gdprArt5Days`; a job's comment says what the job does, not "per CCPA Reg. 7022(d)".
- A duration a law sets (an answer deadline, a log floor) reaches the product as a setting value or a default, named for what it does. Which law set it is recorded in the report.
- Each gap's recommendation names the feature to build, so the work items carry feature names, not citations.

## Capability checklist

Laws, failure examples, options and costs for each row: `references/capabilities.md`.

| Capability | The customer must be able to | Main laws | Priority |
|---|---|---|---|
| Access and export | Give one person a copy of all their data, machine-readable, with third-party content reviewed out | GDPR 15, 20; CCPA 1798.110, 1798.130, Reg. 7024; US states; DPDP s.11 (summary only) | Must |
| Erasure by the customer | Erase a person itself, without waiting on the vendor, including ex-users who cannot sign in | GDPR 17, 28(3)(e); CCPA 1798.105, Reg. 7022; DPDP s.12(3), 8(7) | Must |
| Free-text correction and redaction | Remove personal details typed into any free-text field or posted image | GDPR 16, 17; CCPA Reg. 7022(b); DPDP s.12 | Must |
| Privacy search | Find every record about a person: by user id, and by name, email or phone in free text | GDPR 15 (EDPB 01/2022 para 125); CCPA Reg. 7024(c); DPDP s.11 | Must |
| Retention per kind of data | Set a period per kind (closed records, ex-users, chats, notifications) and delete or anonymise after it | GDPR 5(1)(e), 25(2); CCPA 1798.100(a)(3); DPDP s.8(7); GLBA 314.4(c)(6) | Must |
| Log retention floors | Keep logs at least as long as the strictest law asks | DPDP rules 6(1)(e), 8(3) (1 year); HIPAA 164.316 (6 years, documentation) | Must (India) |
| Legal hold | Stop deletion of an account, a person or a record set during litigation or a law-enforcement hold | GDPR 17(3)(b),(e); CCPA 1798.105(d), 1798.145(a)(1); DPDP s.17(1) | Must |
| Read logging | Say who read whose data, after a stolen session | DPDP rule 6(1)(c); HIPAA 164.312(b); GLBA 314.4(c)(8); GDPR 33(3) | Must |
| Encryption | Rely on encryption at rest and in transit inside the deployment, backups included | GDPR 32(1)(a), 34(3)(a); DPDP rule 6(1)(a); GLBA 314.4(c)(3); breach-law safe harbours; CCPA 1798.150 | Must (deployment) |
| Notice and privacy contact | Show its own privacy notice and contact at every point where the product collects data | GDPR 13, 14; CCPA 1798.100(a); DPDP s.5, 8(9), rule 9 | Must |
| AI disclosure | Tell people they deal with an AI, name the provider and what is sent, and choose whether it is on | EU AI Act 50(1); GDPR 28(2); CCPA Reg. 7051(b) | Must |
| Sub-processor list and data location | Authorise or object to sub-processors, and know where each copy of the data is | GDPR 28(2),(4), 30(2), Chapter V; CCPA 1798.140(ag)(2); DPDP s.16 | Must (list), Should (regions) |
| Data return at contract end | Get all its data back before deletion, and a confirmation of deletion | GDPR 28(3)(g); Va. Code 59.1-579(B)(2) | Must |
| Request register with legal clocks | Log each privacy request with its jurisdiction's deadlines, and keep the record | GDPR 12(3),(4); UK DPA 2018 s.164A; CCPA Reg. 7021, 7101; DPDP rule 14(3); US state appeals; HIPAA 164.524 | Should |
| Restriction and objection | Keep a person's data stored but out of use while a dispute runs | GDPR 18, 21 | Should (EU, UK) |
| Multi-factor sign-in | Require MFA without an external identity provider | GLBA 314.4(c)(5); GDPR 32; CCPA Reg. 7123 | Should (Must for GLBA) |
| Automated decisions | Give notice of, and explain, automated decisions about staff (work allocation, scoring) | CCPA Reg. 7001(ddd)(4)(B), 7220, 7222; GDPR 22; UK GDPR 22A-22D | Should, LAWYER |
| Hashed identifiers | Keep an erased person's identifier only as a keyed hash | GDPR Recital 26 | Should |
| Backups that keep erasures | Restore a backup without bringing erased people back | CCPA Reg. 7022(d); GDPR 17; EDPB 01/2022 para 110; ICO "beyond use" | Should |
| Breach support | Receive the vendor's breach notice and list the people affected quickly | GDPR 33, 34; DPDP rule 7; state breach laws; GLBA 314.4(j) | Should |
| Sensitive data | Warn, restrict and redact health, ID and financial details that users type in | GDPR 9, 10; CCPA 1798.121, 1798.140(ae); state consent rules | Should |
| Image metadata | Keep location and device data in uploaded images out of the record | GDPR 5(1)(c), 25 | Nice |
| DPDP extras | Record consent, serve nominees, offer notices in Indian languages | DPDP s.5(3), 6(10), 14; rule 4 | Nice, LAWYER |
| Children | Handle child users only if the product serves them | GDPR 8; UK GDPR 8; DPDP s.9; COPPA | Nice (Must if children are users) |

## Strictest common design

A product built to these satisfies every law above at once (details: `references/jurisdictions.md`):

- the GDPR's one-month answer clock and its restriction right;
- California's 10-business-day acknowledgement and 24-month request record, with staff data in scope;
- India's one-year log floor and its rule that every breach is notified, with no risk or size threshold;
- HIPAA's 15-day access answer, where a customer is a covered entity (from 19 Jul 2027).

## References

| Open | When |
|---|---|
| `references/capabilities.md` | assessing or designing one capability: its laws, failure example, options and costs; the vendor's processor duties |
| `references/jurisdictions.md` | deciding which laws apply, or comparing rights, deadlines, breach timings and staff-data scope across laws and US states |
| `references/dates-and-sources.md` | re-verifying dates, checking what was read and in which version, the open points, hosts that block automated reads, what to check in each vendor's terms |
| `references/report.md` | writing the gap analysis: its shape, the standard lawyer points, what to state as strengths |
