# Where the laws agree and differ

Open when deciding which laws reach a product's customers, or comparing rights, deadlines, breach timings and staff-data scope. Checked 2026-11-28; re-verify first (SKILL.md, Laws change). Grades follow SKILL.md. UK cells rest on official guidance, because the UK statute was not read; every other cell with no grade was read in primary text. Not legal advice.

Contents: Rights · Deadlines · US state laws · Breach timings · Is staff data in scope? · Sector laws · EU AI Act · Transfers · Strictest common design

## Rights

| Right | GDPR, UK GDPR | CCPA (California) | Other US states | DPDP (India) |
|---|---|---|---|---|
| Copy of the data | Art. 15(3), in a commonly used electronic form | 1798.110, 1798.130(a)(2): "readily useable" format | Yes, a portable copy | **No.** s.11 gives a summary and a list of recipients only |
| Portability, machine-readable | Art. 20: only data the person provided, processed by automated means on consent or contract | 1798.130(a)(3)(B)(iii), where feasible | Yes | No |
| Correction | Art. 16 | 1798.106 | Yes (Utah from 1 Jul 2026, HB 418, archived official) | s.12(1),(2) |
| Erasure | Art. 17, exceptions in 17(3) | 1798.105, exceptions in (d) | Yes | s.12(3), 8(7) |
| Restriction | Art. 18 | No | No | No |
| Objection | Art. 21: processing on public task or legitimate interests (6(1)(e),(f)); direct marketing in 21(2) | Opt-out of sale or sharing | Opt-out of targeted ads, sale and profiling | Withdraw consent, s.6(4) |
| Automated decisions | Art. 22. UK: Arts 22A-22D from 5 Feb 2026 (DUAA s.80; information, representations, human intervention, contest). Stricter limits stay for special-category data and for decisions resting on a recognised legitimate interest. Official guidance; the ICO's automated-decision guidance is a consultation draft | ADMT rules, Reg. 7200 onwards, from 1 Jan 2027 | Profiling opt-out | No |
| Grievance, nomination | No | No | Appeal (see US state laws) | s.13 grievance (90 days, rule 14(3)); s.14 nomination |

## Deadlines

| Step | GDPR | UK (from 5 Feb 2026; official guidance) | CCPA | Other US states | DPDP |
|---|---|---|---|---|---|
| Acknowledge | No set time | No set time | 10 business days (Reg. 7021(a)) | No set time | No set time |
| Answer | 1 month, plus 2 with reasons (Art. 12(3)) | Same, with "stop the clock" where a clarification is reasonably required: paused on the day clarification is asked, resumed the day after it arrives (UK GDPR Art. 12A; wording not read) | 45 days, plus 45 with notice (1798.130(a)(2)(A)) | Per state, usually 45 plus 45 | None for access, correction or erasure; grievances within 90 days |
| Appeal or complaint | Complaint to the authority (Art. 12(4)) | The controller runs a complaints process: acknowledge within 30 days, keep the person updated, answer without undue delay (DPA 2018 ss.164A-164B, inserted by DUAA s.103, in force by 19 Jun 2026; wording not read). The person may still go to the regulator, which in practice first sends them to the controller | None for ordinary requests | Per state, usually 60 days | Board, after the grievance route (s.13(3)) |
| Keep the request record | Accountability, Art. 5(2) | Same | 24 months (Reg. 7101) | No set time | No set time |

HIPAA, covered entities, from 19 Jul 2027 (45 CFR 164.524(b)(2) as amended 19 Nov 2026): access within 15 calendar days, one extension of up to 30 days in writing with the reason and a date. It covers health information in a designated record set; whether a product's records form part of one is **LAWYER**.

## US state laws

Comprehensive consumer privacy laws, as read on 2026-11-27 and 28. "Answer" is the request deadline plus its extension; "Appeal" is the time to decide an appeal. Apart from California, every law read excludes people acting in a commercial or employment context from "consumer", so staff and B2B contacts are out of scope; outside requesters acting for themselves are in. Indiana and Vermont were not read.

| State | In force | Answer | Appeal | Staff data | Grade |
|---|---|---|---|---|---|
| California (CCPA) | In force; staff data from 1 Jan 2023 | 45 plus 45; acknowledge in 10 business days | None | **In scope** (1798.145(m)(4), (n) inoperative) | Primary (CPPA copy) |
| Virginia, Texas, Maryland, Connecticut | In force (dates not recorded in the check) | 45 plus 45 | 60 days | Excluded | Primary (Connecticut from the AG page) |
| Colorado | 1 Jul 2023 | 45 plus 45 | 45, extendable by 60 | Excluded | Mirror |
| Utah | 31 Dec 2023 | 45 plus 45 | None in the text read; the whole chapter was not read | Excluded | Mirror; date archived official |
| Oregon | 1 Jul 2024 | 45 plus 45 | 45 | Excluded; employee exemption tied to the role | Mirror |
| Florida | 1 Jul 2024 | 45 plus **15** | 60 | Excluded | Primary; reaches only businesses over $1B revenue |
| Montana | 1 Oct 2024 | 45 plus 45 | 60, no extension | Excluded where the person acts solely within their role | Primary, date archived official; SB 297 (2025) lowers thresholds, its effective date not found |
| Iowa | 1 Jan 2025 | **90** plus 45 | 60 | Excluded; employee exemption tied to the role | Primary |
| Delaware | 1 Jan 2025 | 45 plus 45 | 60 | Excluded; employee exemption tied to the role; from 1 Jan 2027 the exemption reportedly stops covering profiling (fetch summary, not re-read) | Primary; thresholds drop on 1 Jan 2027 |
| Nebraska | 1 Jan 2025 | 45 plus 45 | 60 | Excluded; employee exemption tied to the role | Archived official |
| New Hampshire | 1 Jan 2025 | 45 plus 45 | 60 | Excluded | Archived official |
| New Jersey | 15 Jan 2025 (computed) | 45 plus 45 | 45 | Excluded | Archived official |
| Tennessee | 1 Jul 2025 | 45 plus 45 | 60 | Excluded | Archived official |
| Minnesota | 31 Jul 2025 | 45 plus 45 | 45, extendable by 60 | Excluded; employee exemption tied to the role | Primary, date official (indexed) |
| Kentucky | 1 Jan 2026 | 45 plus 45 | 60 | Excluded | Primary |
| Rhode Island | 1 Jan 2026 | 45 plus 45 | 60 | Excluded (the law says "customer") | Archived official |
| Indiana | 1 Jan 2026 (official, indexed) | **UNVERIFIED** | **UNVERIFIED** | **UNVERIFIED** | The official host serves only a JavaScript page |
| Oklahoma | 1 Jan 2027 | 45 plus 45 | 60 | Excluded | Primary |
| Louisiana | 1 Jan 2027 | 45 plus 45 | 60 | Excluded; employee exemption not read in full | Archived official |
| Alabama | 1 May 2027 | 45 plus 45 | **None** | Excluded; employee exemption tied to the role | Archived official |
| Vermont | 1 Jan 2028 | **UNVERIFIED** | **UNVERIFIED** | **UNVERIFIED** | Secondary |

Applicability thresholds (number of consumers, revenue) differ per state and change; read them in the statute for each customer.

## Breach timings

| Who tells whom | GDPR | DPDP | US |
|---|---|---|---|
| Processor to customer | Without undue delay (Art. 33(2)) | Not set; by contract | NY immediately, within 30 days; TX immediately; FL within 10 days |
| Customer to the authority | Within 72 hours where feasible, unless unlikely to be a risk (Art. 33(1)) | Without delay, then full details within 72 hours (rule 7(2)); **every** breach counts (s.2(u)) | CA AG sample within 15 days of notifying people, when more than 500 residents are notified (1798.82(f), archived official); TX AG within 30 days at 250 or more; FL within 30 days at 500 or more; FTC within 30 days at 500 or more for GLBA |
| Customer to the people affected | Without undue delay, if high risk (Art. 34); not needed where data was made unintelligible (34(3)(a)) | Without delay, every breach (rule 7(1)) | CA 30 calendar days from discovery, delay allowed for law enforcement or to find the scope (1798.82(a)(2), archived official); NY 30 days; FL 30 days; TX 60 days |

State breach laws exempt encrypted data; read for New York (GBL 899-aa(1)(b)).

## Is staff data in scope?

| Law | Staff data |
|---|---|
| GDPR, UK GDPR | Yes |
| DPDP | Yes. The likely basis is s.7(i) employment; whether s.11 and s.12 rights attach to s.7(i) processing is **LAWYER** (the text ties them to consent and s.7(a)) |
| CCPA | Yes, since 1 Jan 2023 |
| Other US states | No, in every law read (table above); Indiana and Vermont **UNVERIFIED**. Several states (Oregon, Minnesota, Nebraska, Iowa, Delaware, Alabama, Montana) tie the exemption to data used within the person's role, and Delaware drops it for profiling from 1 Jan 2027 |

## Sector laws

| Law | Who | What it asks of the product |
|---|---|---|
| HIPAA | Covered entities and their business associates | Audit controls (164.312(b)); encryption addressable today (164.312(a)(2)(iv), (e)); documentation kept 6 years (164.316(b)(2)); access in 15 days from 19 Jul 2027 (164.524(b)(2)). The Security Rule rewrite (proposed 6 Jan 2025, 90 FR 898) would require encryption and MFA; still a proposal on 2026-11-28 (Federal Register API), final action listed for July 2027 among long-term actions; the Spring 2026 Unified Agenda shows no timetable |
| GLBA Safeguards Rule | FTC-regulated financial institutions | Encryption in transit and at rest (314.4(c)(3)); MFA for anyone accessing any information system (314.4(c)(5)); disposal 2 years after last use (314.4(c)(6)); activity logging (314.4(c)(8)); FTC notice within 30 days at 500 or more (314.4(j)) |
| FERPA | Schools | A record of disclosures (34 CFR 99.32) |
| COPPA | Online services that collect data from children under 13 (the under-13 scope was not re-read) | 2025 amendments, compliance by 22 Apr 2026 (`capabilities.md`, Children) |

## EU AI Act

Art. 50(1): people must be told they are interacting with an AI system unless it is obvious, from 2 Aug 2026 (Art. 113). The duty falls on the provider of the system. The amending Regulation (EU) 2026/1744 left Art. 50(1) alone; it gave Art. 50(2) (marking AI-generated content) a grace period to 2 Dec 2026 for systems placed on the market before 2 Aug 2026, and moved the high-risk dates to 2 Dec 2027 and 2 Aug 2028.

## Transfers

- EU: an adequacy decision (Art. 45(3); the EU-US Data Privacy Framework is one) or appropriate safeguards such as the SCCs (Art. 46(2)(c)). Arts 47-49 were not read.
- UK: the UK IDTA.
- India: s.16 lets the government restrict transfers to countries it notifies, and rule 15 lets it add requirements by order; neither had been used on 2026-11-28 (an absence, checked only on the Data Protection Board's site; the eGazette could not be reached), and s.16 takes effect on 13 May 2027.
- Which tool applies is **LAWYER**.

## Strictest common design

One design that meets every law above, where each law's strictest rule is taken:

| Point | Strictest rule | From |
|---|---|---|
| Answer deadline | 1 month, extendable by 2 with reasons; paused while a reasonably required UK clarification is awaited | GDPR Art. 12(3); UK GDPR Art. 12A (official guidance) |
| Health access answer | 15 calendar days, one 30-day extension | HIPAA 164.524(b)(2), covered entities, from 19 Jul 2027 |
| Acknowledgement | 10 business days | CCPA Reg. 7021(a) |
| Complaint acknowledgement | 30 days | UK DPA 2018 s.164A (official guidance) |
| Request record | Kept 24 months, surviving the erasure it asked for | CCPA Reg. 7101, 7022(e) |
| Restriction | Store-only flag per person | GDPR Art. 18 |
| Staff data | In scope | GDPR, CCPA, DPDP |
| Log floor | 1 year for logs of processing and access | DPDP rules 6(1)(e), 8(3) |
| Breach | Every breach is notified, no threshold; authority details within 72 hours | DPDP s.2(u), rule 7 |
| Processor breach notice | Immediately, and within 10 days at the latest | NY, TX; Fla. Stat. 501.171(6)(a) |
| MFA | Available and enforceable for every user | GLBA 314.4(c)(5) |
| Encryption | At rest and in transit, everywhere | GLBA 314.4(c)(3) |
