# Capabilities in detail

Open when assessing or designing one capability. Each gives the laws, a failure example, what the product should offer and the options with their costs. Facts as checked on 2026-11-28; re-verify first (SKILL.md, Laws change). Not legal advice.

Contents: Access and export · Erasure by the customer · Free-text correction and redaction · Privacy search · Retention per kind of data · Log retention floors · Legal hold · Read logging · Encryption · Notice and privacy contact · AI disclosure · Sub-processor list and data location · Data return at contract end · Request register with legal clocks · Restriction and objection · Multi-factor sign-in · Automated decisions · Hashed identifiers · Backups that keep erasures · Breach support · Sensitive data · Image metadata · DPDP extras · Children · Processor duties

## Access and export (Must-have)

**Laws:**
- GDPR Art. 15(1)-(4): confirm the processing; give a copy plus purposes, recipients, retention and source; in a commonly used electronic form when asked electronically; without adversely affecting others' rights.
- GDPR Art. 20: a structured, machine-readable copy of the data the person provided, where the basis is consent or contract and the processing is carried out by automated means.
- CCPA 1798.110, 1798.130(a)(2)(A), Reg. 7024: specific pieces in a "readily useable format", including what a service provider holds. A search may be skipped only for data that is not reasonably accessible, and the person is told which record types were not searched (Reg. 7024(c)).
- Other US states: a portable copy.
- DPDP s.11: a summary and the list of recipients only; no copy right.

**Fails when:** a former employee in Germany asks for everything held about them. The administrator can open their profile, but cannot collect their records, comments, approvals, device history, notifications and AI chats into one file. Drafts and chats are visible only to the person. The one-month limit passes, or the answer is incomplete.

**Offer:** an administrator's person export.
- Scope: one person, by user id, or by an outside email for a non-user (found with the privacy search).
- Content: every store that holds the person: profile, records raised by or for them, what they wrote, approvals, assignments, devices, notifications, AI conversations, their audit rows, records of inbound mail about them.
- Built by a job; JSON plus a readable page; delivered by a short-lived link; the export and each download audited.
- A review step before release that flags other people's content in shared threads and lets the admin leave it out (GDPR 15(4), CCPA Reg. 7024(d)).
- Its own permission, held by administrators by default.
- It says what backups hold (EDPB 01/2022 para 110; see Backups).

| Option | Gets right | Costs |
|---|---|---|
| A. Admin export in the product (recommended) | The customer meets its deadline alone; one tool serves GDPR, CCPA and the DPDP summary | The export is another copy of personal data, so it needs a short life |
| B. Vendor operator runs the export | No customer-facing screen | Every request waits on vendor staff; vendor staff read customer data each time, which needs the customer's instruction each time (GDPR 28(3)(a), 29); the deadline runs on the vendor's queue |
| C. Self-service "download my data" only | People serve themselves | Ex-users who cannot sign in and non-users are shut out; nobody reviews third-party content. Useful beside A |

## Erasure by the customer (Must-have)

**Laws:** GDPR Art. 17(1) (without undue delay) and 28(3)(e) (the processor assists "by appropriate technical and organisational measures"); CCPA 1798.105(c), Reg. 7022 (the business deletes and instructs its service providers); DPDP s.12(3), 8(7).

**Fails when:** only vendor staff can erase. A deactivated ex-employee cannot sign in to ask; the administrator has no erase action and must email the vendor; a request that only reaches the vendor leaves the customer with no record and no clock.

**Offer:** an erasure action for the customer's administrator, with the same checks as any operator erasure (refuse removing the last administrator; refuse while the person holds open work that would be orphaned), a typed confirmation, and a result report: what was erased, what was kept and why. A deletion request made by the person reaches the customer's administrator, not only the vendor.

| Option | Gets right | Costs |
|---|---|---|
| A. Admin erasure in the product (recommended) | The customer acts within its deadline and keeps control as controller | Erasure cannot be undone, so a mistaken one is final; the typed confirmation is the guard |
| B. Vendor-only erasure with a contractual turnaround | Only trained staff erase | Each erasure needs a written instruction; the 1-month or 45-day clock runs on the vendor's queue; ex-users still have no way to ask |

## Free-text correction and redaction (Must-have)

**Laws:** GDPR Art. 17 covers all the person's personal data, not only the profile row; Art. 16 includes completion by a supplementary statement. CCPA Reg. 7022(b) allows deleting, de-identifying or aggregating. DPDP s.12(3), 8(7). **LAWYER:** whether text another person typed about the subject is "collected from the consumer" under CCPA 1798.105(a); treating it as in scope is safer.

**Fails when:** a person wrote "send the laptop to my home, 12 Lake Road, my mobile is ..." in a record. After erasure the text still reads the same under "Erased user", visible to every viewer until the account ends, and nobody can blank it because submitted text is not editable.

**Offer:**
1. A redact action for a privacy role on any free-text field and any posted image. It replaces the content with "[removed for privacy]" and writes an audit row with no content, so the removed text survives nowhere.
2. An erasure option (account setting, off by default) that also blanks the free text the person wrote. Records keep their structure, numbers, statuses and dates.
3. Both skip held items (Legal hold) and say so in the result report.

| Option | Gets right | Costs |
|---|---|---|
| A. Redact action plus the erasure option (recommended) | Personal details go; the business record stays for the 17(3)(b),(e) reasons | A redacted record loses context a later investigation might need; legal hold protects the cases that matter |
| B. Delete every record the person raised | Simple to explain | Breaks other people's records: reports, approvals and history lose rows the customer must keep, and colleagues' comments go too |
| C. Keep text and document it | No change | Fails erasure wherever no exception applies; the customer cannot remove a pasted ID number even on its own initiative |

## Privacy search (Must-have)

**Laws:** GDPR Art. 15: a search of all IT and non-IT filing systems (EDPB Guidelines 01/2022 para 125); effort alone does not make a request excessive (para 188). UK since the Data (Use and Access) Act 2025: a "reasonable and proportionate" search (official guidance; no article number confirmed, so cite none). CCPA Reg. 7024(c): only data not searchable or reasonably accessible is excused, and the person is told which record types were not searched. DPDP s.11.

**Fails when:** a colleague named a non-user in five records. The customer cannot find them: search matches record numbers only, and there is no person filter.

**Offer:** a privacy search for the privacy role.
- By person: every row naming the user id in any role (author, requester, assignee, approver, holder, recipient, audit actor).
- By text: a name, email or phone fragment over every free-text field, AI messages included.
- Each search audited, with the search text masked.

| Option | Gets right | Costs |
|---|---|---|
| A. Search in the main database (recommended) | No new store; erasure reaches everything the search finds | Text search over large accounts needs an index (trigram or full-text) on free-text columns, which adds write cost |
| B. A separate search service | Fast fuzzy search | Another copy of all text that erasure, purge, regions and backups must cover; a new sub-processor or component |
| C. Export the account for the customer to search | No product change | Hands everyone's data to one admin to answer one request: over-disclosure, and the export needs protecting |

## Retention per kind of data (Must-have)

**Laws:** GDPR Art. 5(1)(e) and 25(2) (no longer than necessary, by default); CCPA 1798.100(a)(3) (disclose the period per category and keep to it); DPDP s.8(7) (erase when the purpose is served or consent is withdrawn); GLBA 314.4(c)(6) (dispose 2 years after last use, for FTC-regulated financial institutions). **LAWYER** sets every period.

**Fails when:** the customer's notice says "records are kept 3 years after closure" but the product keeps them until the account ends, and an ex-employee's name, email, phone and picture stay forever.

**Offer:** one account setting per kind of data, each "keep" by default so nothing changes until the customer chooses:

| Kind | At the end of the period |
|---|---|
| Closed records, with their comments, images and approvals | Delete, or anonymise: blank the free text, keep numbers and statuses |
| Deactivated users | Erase, the same erasure as above |
| AI conversations | Their own period, not tied to the audit log's |
| Notifications | Per account, within a global maximum |
| Assignment history of departed people | Anonymise the person |

Every job skips held items and writes one counting audit row.

| Option | Gets right | Costs |
|---|---|---|
| A. One setting per kind (recommended) | Matches how laws and notices state periods | More settings on one page |
| B. One account-wide period | One number | Forces the shortest period on everything (losing records the customer must keep) or the longest (breaking minimisation) |
| C. Manual deletion only | No jobs | The notice promise cannot be kept at scale |

## Log retention floors (Must-have for Indian customers)

**Laws:** DPDP rule 6(1)(e) (keep logs and personal data 1 year, to detect and investigate unauthorised access) and rule 8(3) ("personal data, associated traffic data and other logs of the processing for a minimum period of one year"), from 13 May 2027. HIPAA 164.316(b)(2) keeps documentation 6 years; whether audit logs count is **LAWYER**.

**Fails when:** an Indian customer leaves the audit log on a 180-day default and holds half the required year. A 90-day security log falls short the same way.

**Offer:** a 365-day default for audit and security logs, or a per-account floor. Do not tie other data's retention to the audit period, or a 1-year floor keeps chats for a year too. **LAWYER:** rule 8(3) against an erasure request, and whether pseudonymous audit rows (ids and markers only) satisfy erasure.

| Option | Gets right | Costs |
|---|---|---|
| A. 365-day default (recommended) | Meets India with no customer action; still inside GDPR minimisation for security logs (**LAWYER**) | Customers elsewhere keep logs longer unless they lower the value |
| B. Jurisdiction profile per account | Each customer gets its own floors | A customer that picks the wrong profile gets the wrong floors silently |

## Legal hold (Must-have)

**Laws:** GDPR 17(3)(b) (a legal obligation under EU or member-state law only, so a US hold does not count under (b)) and (e) (legal claims, which can still cover it); CCPA 1798.105(d)(8) and 1798.145(a)(1)(A),(B),(E) (a law-enforcement direction not to delete for 90 days, renewable); on a denial, delete the rest and restrict what is kept (Reg. 7022(f)); DPDP s.17(1)(a),(c).

**Fails when:** a former employee sues the customer, and retention jobs delete their records and the audit trail on schedule; or a customer under investigation cancels and the account purge runs with nothing to stop it.

**Offer:** a hold at three levels: account, person, record or record set. The account hold pauses the purge and every retention job; person and record holds make erasure, redaction and retention skip the held items and report them. Each hold records who set it, the reason code, the start and an optional review date, with a reminder for the 90-day law-enforcement kind. Only the privacy role sets or lifts one; every change is audited.

| Option | Gets right | Costs |
|---|---|---|
| A. Hold flags at three levels (recommended) | Exact; the rest of the person's data can still be erased (Reg. 7022(f)) | Held data must be kept out of ordinary use, which ties into Restriction |
| B. Suspend the account | Often exists | Stops everyone working; does not stop the purge of a closed account |

## Read logging (Must-have)

**Laws:** DPDP rule 6(1)(c) ("visibility on the accessing of such personal data, through appropriate logs, monitoring and review"); HIPAA 164.312(b) (record and examine activity); GLBA 314.4(c)(8) (monitor and log authorised users' activity); GDPR 33(3)(a) (the breach notice gives the approximate number of people and records); state breach laws (residents affected).

**Fails when:** an attacker reads records for three days with a stolen session. Only writes are audited. The customer must tell the authority within 72 hours how many people are concerned and cannot, so it treats the whole account as exposed.

**Offer:** a read log: one row per read of a person-bearing record (detail pages, attachment links issued, exports, AI reads, audit-log pages), holding account, user, record type and id, time and route, with no IP (the IP stays in security log lines; fields: `securing-applications`). Its own retention, 1 year by default. A report of everything a user or session read in a period. Rows written outside the request transaction.

| Option | Gets right | Costs |
|---|---|---|
| A. A read log table (recommended) | Answers "who saw whose data" per account | Write volume per page read; it is personal data with its own retention and purge |
| B. Proxy access logs with the user id | No app change | All accounts in one log outside the account scope; customers cannot query it |
| C. Log exports and bulk reads only | Small | Misses the slow targeted read, the usual pattern of a stolen session |

## Encryption (Must-have, at the deployment)

**Laws:** GDPR 32(1)(a) (pseudonymisation and encryption); DPDP rule 6(1)(a) (encryption, obfuscation or masking); GLBA 314.4(c)(3) (in transit and at rest, required); HIPAA 164.312(a)(2)(iv), (e) (addressable; the proposed Security Rule rewrite would require it, proposed 164.312(b)(2), still a proposal). Breach laws exempt encrypted data (NY GBL 899-aa(1)(b)); GDPR 34(3)(a) drops the notice to people where data was made unintelligible, but the Art. 33 notice to the authority still applies. CCPA 1798.150 damages apply to non-encrypted data.

**Fails when:** a database backup leaks. Without encryption at rest, every record is a notifiable breach everywhere; with it, and the key safe, it may not need notifying.

**Offer:** state as production requirements, in the security documentation customers receive: encrypted database storage and backups, server-side encryption on object storage, TLS from the app to the database, caches, object storage and mail relay. Refuse to boot in production with any of these transport encryptions turned off.

| Option | Gets right | Costs |
|---|---|---|
| A. Storage and transport encryption at the deployment (recommended) | Covers every table, object and backup; what questionnaires ask for | Protects stolen media and dumps, not a live attacker inside the app |
| B. Application-level encryption of free text | Protects against a database-only attacker | Breaks search over text; needs per-account key handling |

## Notice and privacy contact (Must-have)

**Laws:** GDPR Art. 13 (for what people give) and 14 (for people others name, with exceptions that are **LAWYER**); CCPA 1798.100(a) (notice at or before collection; employees are consumers); DPDP s.5 and rule 3 (a notice with each consent request), s.8(9) and rule 9 (publish a privacy contact).

**Fails when:** sign-up and invite mails collect a person's data and neither shows the customer's notice; a Californian onboarded by invite never sees one.

**Offer:** two account settings: a privacy notice URL (with a version label), shown at sign-in and sign-up, in invite and verification mails, in the footer and in an AI panel before the first message, recording which version each person was shown and when; and a privacy contact, shown beside it and in privacy-request mails.

| Option | Gets right | Costs |
|---|---|---|
| A. Notice and contact settings (recommended) | The customer's own text at the collection points the product owns | The "shown" record is one more personal-data row per person |
| B. The customer publishes the notice elsewhere | No product change | No notice at sign-up, invite or the AI panel |

## AI disclosure (Must-have)

**Laws:** EU AI Act Art. 50(1) (tell people they are interacting with an AI unless obvious), from 2 Aug 2026; the duty falls on the provider of the AI system, which is the vendor; whether a title such as "AI assistant" alone makes it obvious is **LAWYER**. GDPR 28(2),(4) (no sub-processor without authorisation; same terms passed down). CCPA 1798.140(ag)(2), Reg. 7051(b) (notify the business, bind the subcontractor), Reg. 7050(a)(3) (no use for another customer), Reg. 7150(b)(6) (training on personal data for some purposes triggers a risk assessment).

**Fails when:** the AI feature is on by default; an employee asks it about a colleague's record and the colleague's comments, possibly health details, go to a model provider the customer's processing agreement does not list. The employee then cannot delete their own chat history.

**Offer:**
1. A disclosure line in the AI panel and on the admin's settings: who writes the replies, and what is sent ("Replies are written by an AI model from <provider>. Your messages and the records you can see are sent to it.").
2. The provider on the sub-processor list, with its terms: training, retention, zero-retention availability and conditions, and where data rests and is processed. What to check, vendor by vendor: `dates-and-sources.md`, Vendor terms. Each vendor is judged on its own terms; the choice of vendor, and of model, can decide what the product can promise.
3. People can delete and export their own conversations (also part of the person export).
4. A deliberate default for new accounts:

| Option | Gets right | Costs |
|---|---|---|
| A. Off until an administrator turns it on after seeing the disclosure (recommended) | The controller makes the choice GDPR 28(2) and 25(2) expect; nothing is sent before | Fewer people try the feature |
| B. On, with the provider named in a processing agreement every customer signs | Keeps the experience | Holds only if every customer signs before first use; a self sign-up account uses it before any agreement |
| C. On, with the disclosure only | Smallest change | An account whose agreement does not name the provider sends colleagues' data to an unapproved sub-processor |

## Sub-processor list and data location (Must-have list, Should-have regions)

**Laws:** GDPR 28(2),(4) (authorisation, notice of changes), 30(2) (the processor's record, listing transfers), Chapter V (a transfer needs an adequacy decision under Art. 45(3), such as the EU-US Data Privacy Framework, or safeguards such as SCCs under Art. 46(2)(c); UK transfers use the UK IDTA; the choice is **LAWYER**). CCPA 1798.140(ag)(2). DPDP s.16 (the government may restrict transfers to countries it notifies; rule 15 lets it add requirements by order; neither had been used on 2026-11-28, an absence checked only on the Data Protection Board's site; s.16 in force from 13 May 2027).

**Fails when:** an EU customer's lawyer asks where attachments, backups and logs are held and who the sub-processors are, and nothing is written down.

**Offer:** a published list: hosting, database and object-store location, mail relay, AI provider, log store, backups, identity providers the customer enables, each with a location; a 30-day change notice with a right to object. Regional hosting where customers' contracts require it.

## Data return at contract end (Must-have)

**Laws:** GDPR 28(3)(g) (delete or return all data at the controller's choice, and delete copies); Va. Code 59.1-579(B)(2).

**Fails when:** a cancelling customer asks for its records and the product offers only a closing period, then deletion.

**Offer:** an account export (every table plus stored objects) the administrator downloads during the closing period, built by the same job as the person export; a deletion confirmation after the purge; a stated backup expiry. Build it before the first paying customer.

## Request register with legal clocks (Should-have)

**Laws:**
- GDPR 12(3),(4): answer in 1 month, plus 2 with reasons; a refusal gives reasons and the right to complain.
- UK: the clock stops while a clarification that is reasonably required is awaited (UK GDPR Art. 12A); the controller runs a complaints process, acknowledging within 30 days (DPA 2018 ss.164A-164B; official guidance).
- CCPA Reg. 7021: acknowledge in 10 business days, answer in 45 plus 45; Reg. 7101: keep request records 24 months with listed fields; Reg. 7022(e): the record survives the deletion it asked for; Reg. 7063: authorised agents.
- Other US states: answer and appeal deadlines per state (`jurisdictions.md`).
- DPDP rule 14(3): grievances in 90 days; rule 14(1),(2): publish how to make a request.
- HIPAA, covered entities, from 19 Jul 2027: access in 15 calendar days plus one 30-day extension (164.524(b)(2)); no unreasonable identity checks (164.514(h)(2)(v)); the business associate agreement says whether the vendor discloses to the person or the customer (164.502(a)(4)(ii)); only a designated record set (**LAWYER**).

**Fails when:** a California employee asks to know their data; the customer cannot show when it arrived, that it acknowledged within 10 business days, or keep the 24-month record that survives the person's erasure.

**Offer:** a register. Each entry: type (access, correction, erasure, restriction, objection, complaint, grievance, appeal); subject (a user, or an outside email); received date and jurisdiction; acknowledgement and answer clocks from that jurisdiction's rule, in calendar days, with extension and reason, paused for a UK clarification; verification steps; authorised agent with proof; outcome and basis of any denial. Kept 24 months outside ordinary erasure; visible to the privacy role; self-service deletion requests open an entry; a public form or a privacy mailbox lets non-users and ex-users in.

| Option | Gets right | Costs |
|---|---|---|
| A. Built-in register (recommended) | Ties each request to the export, erasure and hold actions; clocks follow the law | A new record type and screens to maintain |
| B. A generic record or workflow type with service-level timers | Nothing new | Requester must be a user; service-level timers usually run in working hours, not legal calendar days; erasing the requester anonymises the record that proves it was done |
| C. The customer's own tool | No change | Nothing ties a request to what was done in the product |

## Restriction and objection (Should-have, EU and UK)

**Laws:** GDPR Art. 18 (store only, while accuracy is contested, an objection is weighed, or for claims; tell the person before lifting, 18(3)); Art. 21(1) (objection to processing based on Art. 6(1)(e) or (f); stop unless compelling grounds or legal claims).

**Fails when:** an employee contests figures recorded about them and objects to AI processing of their data; the only control is deactivation, which also stops them working.

**Offer:** a per-person "restricted" flag set by the privacy role with a reason: data stays stored, but is left out of AI reads, pickers, mail bodies, exports and reports. Lifting it reminds the admin to tell the person. Alternative, deactivation: the person loses sign-in over a dispute about one kind of data.

## Multi-factor sign-in (Should-have; Must-have for GLBA)

**Laws:** GLBA 314.4(c)(5) (MFA for anyone accessing any information system, FTC-regulated financial institutions); GDPR 32 ("state of the art"); CCPA Reg. 7123 (MFA among the cybersecurity-audit components); HIPAA's proposed Security Rule rewrite (proposed 164.312(f)(2)(ii)(A), still a proposal on 2026-11-28).

**Fails when:** a non-bank lender with no identity provider uses password sign-in and cannot meet the Safeguards Rule.

| Option | Gets right | Costs |
|---|---|---|
| A. TOTP and passkeys in the product, with an account setting to require MFA for admins or everyone (recommended) | Works without an identity provider | Recovery codes and lost devices become a support process |
| B. Require SSO for regulated accounts | The identity provider's MFA applies | A customer without a supported identity provider cannot comply; a break-glass password admin stays single-factor |

## Automated decisions (Should-have, LAWYER)

**Laws:** CCPA regulations: "allocation or assignment of work for employees" is a significant decision (Reg. 7001(ddd)(4)(B)); ADMT is computation that replaces human decision-making (7001(e)); from 1 Jan 2027 (7200(b)) a pre-use notice (7220) and access to the ADMT (7222); no opt-out needed when used solely for allocating work and it "works for the business's purpose and does not unlawfully discriminate" (7221(b)(3)); inferring performance at work triggers a risk assessment (7150(b)(4)). GDPR Art. 22 needs a decision based solely on automated processing with a legal or similarly significant effect. UK: Arts 22A-22D replace Art. 22 from 5 Feb 2026, with stricter limits kept for special-category data and decisions resting on a recognised legitimate interest (official guidance; the ICO's is a consultation draft). **LAWYER** for both.

**Fails when:** a California business turns on rule-based auto-assignment; from 2027 its staff are owed a pre-use notice and, on request, an explanation of how the logic decided for them.

**Offer:** a ready pre-use notice text; the decision reason (rule, method, inputs) recorded and shown in the person export; human review (reassignment or override); a documentation line that per-person performance reports must not drive pay or discipline without the customer's own assessment.

## Hashed identifiers (Should-have)

**Law:** GDPR Recital 26: pseudonymised data attributable with additional information "should be considered" personal data. An unkeyed hash of an email is attributable by anyone with a candidate address.

**Fails when:** a database copy leaks; anyone hashes a known address and confirms the person was a user and was erased.

| Option | Gets right | Costs |
|---|---|---|
| A. Keyed hash (HMAC under a server key) (recommended; same rule as the security log's identifier hash, `securing-applications`) | Only the app can match an address | A rotated key leaves old hashes unmatchable unless rotation re-hashes them |
| B. Drop the identifier (random placeholder) | Nothing left | Support cannot confirm a past erasure or warn when the address is invited again |
| C. Unkeyed hash | No change | As in the failure example |

## Backups that keep erasures (Should-have)

**Laws:** CCPA Reg. 7022(d) (deletion from backups may wait until restore or next use, then must apply); UK ICO accepts backup data put "beyond use" until overwritten (official guidance, UK only); EU: no adopted EDPB position (the 2025 erasure enforcement report, adopted 10 Feb 2026, names it open), and EDPB 01/2022 para 110 expects access to reach backup-only data where technically feasible.

**Fails when:** a restore from a 3-week-old backup brings five erased people back with their names and emails.

**Offer:** a documented backup retention (for example 35 days); an erasure ledger (account id, user id, time of each erasure and purge, no personal data) that the restore runbook replays before the app opens.

## Breach support (Should-have)

**Laws:** GDPR 33(2) (processor tells the controller without undue delay), 33(5) (the controller documents every breach), 34; DPDP rule 7 (every breach, with listed details, to each person and to the Board); US state counts of residents; GLBA 314.4(j). Timings: `jurisdictions.md`.

**Offer:** an account security contact setting (required for the vendor's notice to land) and a vendor breach runbook; an "affected people" report: given a set of records or a user's read-log entries, list the people whose data they hold, with contact details. Residence for US counts comes from the customer's HR data when the product holds no address.

## Sensitive data (Should-have)

**Laws:** GDPR 9, 10 (special category and criminal data need a condition, **LAWYER**); CCPA 1798.140(ae) (sensitive personal information), 1798.121 (limits on use); state laws require consent for sensitive data outside the employment exemption.

**Fails when:** a requester writes "I am off for chemotherapy, please set up remote access" and every viewer and the AI can read it.

**Offer:** an account notice on input forms ("do not include health, ID or bank details unless needed"); a restricted visibility on a record (requester, assignee, managers), left out of AI reads, notification mails and exports; the redact action. Automatic detection is nice-to-have and only flags, never changes text: it is itself processing and gives false positives.

## Image metadata (Nice-to-have)

**Laws:** GDPR 5(1)(c), 25 (minimisation by default).

**Fails when:** the browser strips EXIF and GPS, but a client that skips the strip uploads a photo taken at home and leaks its location.

**Offer:** a server-side check at upload confirmation that walks the image header and refuses an image still carrying EXIF, XMP or GPS segments. No decoding or re-encoding on the server (`securing-applications`, Uploads).

## DPDP extras (Nice-to-have, LAWYER)

- **Consent ledger** (s.6(10): the fiduciary proves consent): only for purposes the lawyer bases on consent. Records purpose, notice version, time, language and action; withdrawal as easy as giving.
- **Notice languages** (s.5(3)): English or any Eighth Schedule language; the notice URL can point to a page per language.
- **Nomination** (s.14): a nominee acts on death or incapacity; the admin's export and erasure tools serve a verified nominee.
- **Consent managers** (s.6(7)-(9), rule 4, registration from 13 Nov 2026): no duty to integrate; no technical standard published on 2026-11-28.
- **Third Schedule** (48-hour pre-erasure notice, 3-year inactivity erasure, rule 8(1),(2)): only large e-commerce, online gaming and social media platforms.

## Children (Nice-to-have; Must-have if children are users)

- GDPR Art. 8: 16, or as low as 13 by member-state law, only where consent is the basis and the service is offered directly to a child.
- UK GDPR Art. 8(1): 13. DPA 2018 s.9 excludes preventive or counselling services (official guidance; statute not read).
- DPDP s.9: under 18, a parent's verifiable consent. A removal-of-difficulties order of 6 Oct 2026 (s.43) changed s.9(1); what it changed is **UNVERIFIED**.
- COPPA: under 13 (scope not re-read); 2025 amendments (90 FR 16918, 22 Apr 2025) effective 23 Jun 2025, compliance by 22 Apr 2026, except safe-harbor duties due earlier (312.11(d)(1) and (g) six months, (d)(4) 90 days after publication). A written information security program is in the current text (312.8(b)). The amendments add separate parental consent before disclosure to third parties (312.5(a)(2)), a written retention policy with no indefinite retention (312.10), biometric and government identifiers as personal information (312.2), and a definition of "mixed audience".
- FERPA (schools): 34 CFR 99.32 requires a record of disclosures.
- A workforce or business product holds no child data: state "for workforce and business use" in the terms, and build age handling only for a customer that serves children.

## Processor duties

What the vendor itself must do, beside the product capabilities.

| Duty | Source | What is needed |
|---|---|---|
| A processing agreement per customer | GDPR 28(3); CCPA 1798.100(d), 1798.140(ag), Reg. 7051(a)(1)-(9); Va. Code 59.1-579; DPDP s.8(2) | Instructions only, confidentiality, security, sub-processors, assistance, deletion or return, audits; CCPA terms (no sale or sharing, no combining, the named business purpose, notice if it cannot comply) |
| Assist with rights | GDPR 28(3)(e); CCPA 1798.105(c)(3), 1798.130(a)(3)(A); HIPAA 164.502(a)(4)(ii) | The customer-side tools above; forward requests sent to the vendor to the customer, never answer them itself (CCPA Reg. 7050(c)) |
| Security and breach notice | GDPR 28(3)(f), 32, 33(2); DPDP rule 6(1)(f); NY GBL 899-aa(3); Fla. Stat. 501.171(6)(a); Tex. Bus. & Com. Code 521.053(c) | Encryption; a breach runbook; notice without undue delay, within 10 days at the latest for Florida |
| Sub-processors | GDPR 28(2),(4); CCPA Reg. 7051(b) | The published list with change notice |
| Return or delete at the end | GDPR 28(3)(g); Va. Code 59.1-579(B)(2) | Data return, plus backup expiry |
| Staff act only on instructions | GDPR 29, 32(4) | Operator actions need a case reference in the audit row; log operators' reads of customer data |
| The processor's record of processing | GDPR 30(2) | Kept by the vendor, not a product feature |
| No use for other customers or training | CCPA Reg. 7050(a)(3); GDPR 28(3)(a) | State it; check each vendor's terms on training (`dates-and-sources.md`, Vendor terms) |
