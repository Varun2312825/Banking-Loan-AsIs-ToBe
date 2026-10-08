# 09 — Root Cause Analysis





**Method:** 5 Whys, used on the top two pain points from `pain_point_log.xlsx` (PP-01 and PP-02)



> Rebuilt from public sources (see `07_source_log.md`). Times are estimates from `process_metrics.xlsx`; assumptions are in `assumption_register.xlsx`.



**How I used 5 Whys:** each "why" asks about the answer above it. I stopped when the answer was something the bank can change: a rule, a system feature or a responsibility.



---



## Root cause 1 — PP-01: the document chase



**Symptom:** About 4 in 10 files are sent back to the branch for a missing or unreadable document (A7 → A8). Each round takes about 72 hours and adds 4 handoffs, about 36 hours per application on average.



1. **Why is the file sent back?**

   Credit Operations finds a missing document during the completeness check (A7).

2. **Why is it only found at A7?**

   Nobody checks documents against the checklist while collecting them (A3–A4).

3. **Why doesn't the branch check them?**

   The branch collects the documents, but Credit Operations owns completeness (RACI, OBS-01). So gaps become someone else's problem.

4. **Why does Credit Operations own it?**

   The process treats completeness as a back-office check after the handoff, not a check while the customer is still there.

5. **Why do incomplete files get through?**

   Nothing at capture stops them. The first real check is at A7, and checklists differ between banks (1 salary slip at ICICI, S03; 3 at Kotak, S05), so staff work from memory.



**Root cause:** Completeness is checked too late, by a team that never meets the customer.



**What can change:**

- **System rule:** the application can't be submitted until every mandatory document is uploaded and readable.

- **Responsibility:** completeness is owned at capture (by the customer online, or the branch for walk-ins). Update the RACI.



**Not the root cause:** "customers are careless" or "staff make mistakes". Mistakes will always happen. The real problem is that the process can't catch them while the customer is still there.



---



## Root cause 2 — PP-02: closing waits for the customer



**Symptom:** After approval, the file waits about 60 hours for the customer to accept the offer and then visit the branch to sign (A21–A22). Close & Disburse has the most waiting of any stage: 130 hours, 48% of all waiting (Bottleneck sheet).



1. **Why does closing take so long?**

   The customer has to act twice: accept the sanction letter (A21), then visit the branch to sign (A22).

2. **Why twice?**

   Accepting and signing are separate steps, done by different people at different times.

3. **Why separate?**

   The agreement must be signed in person at the branch.

4. **Why in person?**

   It's a paper document that needs a physical signature. Meridian has no e-sign.

5. **Why no e-sign?**

   E-sign and e-mandate aren't connected to Meridian's loan system. Other banks already do this: SBI uses Aadhaar OTP e-sign (S04).



**Root cause:** Closing is built around paper and separate steps, instead of one digital action by the customer.



**What can change:**

- **System feature:** add Aadhaar OTP e-sign and e-mandate to the loan system.

- **Process:** accept, sign and set up repayment in one session, after the customer sees the Key Fact Statement (a control that must stay, S02).



**Also solves:** PP-03, the 48-hour mandate registration (A23). It's another separate paper step (AS-35), so the same fix removes it.



---



## How this shapes the To-Be



| Root cause | Fix | Control that must stay |
|---|---|---|
| 1. Completeness checked too late, by the wrong team | Check completeness at capture; one request listing everything missing | KYC documents and consent (S01, S02) |
| 2. Closing built around paper and separate steps | One digital step: accept, e-sign, e-mandate | KFS before signing; money only to the borrower's own account (S02) |

