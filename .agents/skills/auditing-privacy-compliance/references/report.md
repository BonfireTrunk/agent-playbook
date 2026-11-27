# The gap-analysis report

Open when writing a privacy gap analysis of a product. The report goes in the repo's git-ignored `temp/` folder unless the user names another place; tell the user the path.

## Shape

1. **Header.**
   - Title, date written, date the sources were last checked.
   - "This is not legal advice. Points the customer's lawyer must decide are marked **LAWYER**."
   - The roles: each customer is the controller, business or Data Fiduciary; the vendor is its processor, service provider or Data Processor.
   - The source grades and the priority definitions (SKILL.md), in two short lists.
2. **Summary table**, one row per checklist capability, none skipped:

   | # | Requirement | Laws | Product today | Gap | Recommendation | Priority |
   |---|---|---|---|---|---|---|

   "Product today" names what exists (a screen, a job, a setting). "Gap" says what the customer cannot do. A capability that does not apply says why in the Gap cell.
3. **Dates that matter** for this product's customers: date, what, status (grade).
4. **Where the laws agree and differ**, limited to the laws in scope: rights, deadlines, breach timings, staff data, and the strictest common design.
5. **What the product does today**, short, by area, each point with the spec or code it was read from.
6. **The gaps in detail**, one section per gap, in this order:
   - **Requirement:** each law with its article or section and what it asks.
   - **Failure example:** a real kind of person, a real request, the deadline or duty that is missed.
   - **Recommended:** the capability, concrete enough to build, named as a feature without law citations (SKILL.md, From audit to code).
   - **Alternatives:** a table.

     | Option | Gets right | Costs |
     |---|---|---|

     The recommended option is A and is marked. Costs are concrete consequences, never effort; "none of substance" when there is none. Standard capabilities a customer would expect are among the options.
7. **Points for the customer's lawyer**, numbered (list below, cut to those in scope, plus any new ones).
8. **What the product already does well**: strengths worth stating to customers in its security documentation.
9. **The vendor's duties as processor** (`capabilities.md`, Processor duties), with what exists for each.
10. **Sources and verification status:** a table of text, version read, and grade; then a "Still open" table of point and what would close it. Carry over every open point from `dates-and-sources.md` that bears on the product.

Keep the product's own names, paths and ticket numbers in the report, where they help the reader act. They never go back into this skill.

## Standard lawyer points

1. Legal basis per purpose: GDPR legitimate interests, contract or consent; DPDP s.7(i) employment, s.7(a) or consent. Whether DPDP s.11 and s.12 rights attach to s.7(i) processing. Whether GDPR Art. 20 portability applies to staff data.
2. Every retention period. How DPDP rule 8(3)'s one-year log minimum sits beside an erasure request, and whether pseudonymous audit rows satisfy erasure.
3. Whether text other people typed about a person must be erased or redacted (CCPA "collected from the consumer").
4. Whether an automated feature (work allocation, scoring, a per-person report) is an ADMT significant decision under the CCPA, or an Art. 22 decision (UK: Arts 22A-22D).
5. Whether the product's AI labelling meets AI Act Art. 50(1). Which processing agreement covers each AI provider, and the transfer tool where the provider stores data abroad.
6. The customer's status: a CCPA "business"; a Significant Data Fiduciary or Third Schedule fiduciary under the DPDP; a HIPAA covered entity; a GLBA financial institution; a FERPA school.
7. GDPR Art. 9 conditions where health, union or other special-category data predictably appears; whether a DPIA is needed (for example for an AI feature).
8. The hours the vendor promises for its breach notice to customers, and when the customer "becomes aware" if the vendor knows first.
9. The UK changes (stop the clock, complaints, automated decisions) for customers with UK staff.
10. For HIPAA covered entities: whether the product's records form part of a designated record set (the 15-day access clock from 19 Jul 2027), and whether the business associate agreement has the vendor disclose to the person or to the customer (164.502(a)(4)(ii)).
11. GDPR Art. 14 exceptions for people others name in records.
12. The transfer tool for each sub-processor outside the customer's region (adequacy, SCCs, UK IDTA).

## Strengths worth stating

Questionnaires ask about these. When the product has them, list them with where they are documented:

- An audit row per write, in the same transaction, with personal values masked, no client IP and no secrets.
- Operator actions that require a case reference in the audit row.
- Tenant scoping through one gateway, checked by a cross-tenant leak test suite.
- Slow memory-hard password hashing (Argon2id) with a common-password blocklist; rate limits; short access tokens; refresh-token reuse detection.
- A fixed-field security log, and tests that fail when personal data reaches a log line or job store.
- Inbound mail handling that stores no raw mail, sender address or subject.
- An AI feature that writes nothing without the person's confirmation, and keeps conversation text out of logs.
- A working erasure and a full account purge.
- Self-service profile correction, session review and revocation, and per-person switches for mails and AI.
