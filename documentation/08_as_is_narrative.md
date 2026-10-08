# 08 — As-Is Process Narrative


**Process:** Retail unsecured personal loan origination, Meridian Bank (fictional)  

**Version:** 0.2

> built using public sources (see [`evidence/`](evidence/)).I have not validated with real bank staff. Anything not backed by a source is an **Assumption** and listed in [02_assumption_register.xlsx](analysis/02_assumption_register.xlsx) (AS-xx).

## How to read this

- Each activity has a fixed ID (A1–A26). The same IDs are used in the diagrams, metrics, pain point log and gap analysis.
- **Trigger:** each activity starts when the one before it finishes, unless the table says otherwise.
- **Sources:** S01–S09 refer to `07_source_log.md`.

## Actors and systems

**Actors:** Customer · Branch Sales Officer (BSO) · Credit Operations Analyst · Underwriter · Credit Manager · Risk & Compliance Officer · Disbursement Officer

**Systems:** LOS (Loan Origination System) · DMS (Document Management System) · CBS (Core Banking System) · KYC / CKYC registry · Credit Bureau interface · Email

## Process boundary

- **Start:** Loan application submitted
- **End:** Funds credited and welcome pack issued
- **Other ends:** Application declined  · Application lapsed 

---

## Stage 1 — Capture

| ID | Activity | Who | System | Output | What can go wrong | Source |
|---|---|---|---|---|---|---|
| A1 | Submit loan application | Customer (helped by BSO) | Paper or web form | Signed application form | Blank or wrong fields; asks for more than income supports | S06 |
| A2 | Capture application in LOS | BSO | LOS | Application record + ID | Typing errors (name, PAN, DOB) cause mismatches later | S06; Assumption AS-29 |
| A3 | Collect KYC documents | BSO | Paper, later scanned | KYC documents | Expired or unclear ID; address mismatch; no PAN | S01, S03, S05 |
| A4 | Collect income documents | BSO | Paper / PDF | Salary slips, 3 months' bank statements | Wrong number of slips (banks differ); locked PDFs | S03, S05 |
| A5 | Obtain customer consents | BSO + Customer | Form, recorded in LOS | Signed consent | Consent missing, so checks can't legally go ahead | S02 |
| A6 | Scan and hand over file | BSO | DMS, LOS | File in Credit Ops queue | File waits for end-of-day batch; bad or wrong scans | Assumption AS-30 |

## Stage 2 — Verify

| ID | Activity | Who | System | Output | What can go wrong | Source |
|---|---|---|---|---|---|---|
| A7 | Check document completeness | Credit Ops | LOS, DMS | File complete, or list of missing items | File waits in queue; branch's documents rejected here | S07, S03 |
| A8 | Request missing documents (rework loop) | Credit Ops → BSO → Customer | Email, phone, DMS | Updated file back in queue, or lapsed | Customer slow to reply; wrong document collected; customer gives up; can repeat | S03, S05; Assumption AS-02 to AS-04 |
| A9 | Verify KYC | Credit Ops | CKYC registry, LOS | KYC verified / failed | No CKYC record; details don't match; video KYC fails | S01 |
| A10 | Validate PAN and identity | Credit Ops | PAN service, LOS | PAN validated | Name mismatch (often from A2 typing) | S01; Assumption AS-31 |
| A11 | Cross-check application against documents | Credit Ops | LOS, DMS | Verified data | Late discrepancies send the file back (another A8) | S08 |
| A12 | Verify employment | Credit Ops | Email, phone | Employment verified | Employer HR doesn't reply; small employers hard to check | S07; Assumption AS-32 |
| A13 | Screen for fraud and negative lists | Credit Ops; Risk & Compliance for hits | Screening tool, LOS | Cleared, or referred by email | False positives for common names hold up genuine customers | S08, S01 |

## Stage 3 — Assess

| ID | Activity | Who | System | Output | What can go wrong | Source |
|---|---|---|---|---|---|---|
| A14 | Pull credit bureau report | Credit Ops | Bureau interface, LOS | Credit report and score | Pulled this late, so weak applications have already used days of work | S06 |
| A15 | Assess income and obligations | Underwriter | LOS, DMS, spreadsheet | Net income and existing EMIs | Income checked again (already seen at A11); copied by hand | S02, S06 |
| A16 | Calculate debt-to-income ratio | Underwriter | Spreadsheet | DTI and maximum eligible amount | Spreadsheet errors; amount too high, so customer is contacted again | S04 (65% cap) |
| A17 | Apply credit policy checks | Underwriter | LOS, policy document | Within policy, or deviation | Policy applied differently by different underwriters | Assumption AS-33 |

## Stage 4 — Decide

| ID | Activity | Who | System | Output | What can go wrong | Source |
|---|---|---|---|---|---|---|
| A18 | Refer deviation for approval | Underwriter → Credit Manager | Email | Deviation approved / rejected | Approver busy; status not visible in LOS | S08; Assumption AS-34 |
| A19 | Record credit decision | Underwriter | LOS | Approved, or declined (process ends) | Reasons not recorded; customer told late | S06 |


## Stage 5 — Close & Disburse

| ID | Activity | Who | System | Output | What can go wrong | Source |
|---|---|---|---|---|---|---|
| A20 | Issue sanction letter and KFS | Disbursement Officer | LOS, email | Sanction letter + KFS sent | Wrong figures from re-typing; KFS missing (regulatory breach) | S02, S06 |
| A21 | Customer accepts sanction | Customer | Signed letter | Acceptance | Customer delays; offer expires (lapses) | S02, S06 |
| A22 | Execute loan agreement | Customer, BSO, Disbursement Officer | Paper agreement, DMS | Signed agreement | Extra branch visit to sign on paper; missing signatures | S04 (branch execution) |
| A23 | Register repayment mandate | Disbursement Officer + Customer | Mandate platform, CBS | Auto-debit set up | Rejected by customer's bank; takes days | Assumption AS-35 |
| A24 | Final compliance check | Risk & Compliance | LOS, DMS, checklist | Cleared, or sent back | Missing evidence found only at the end | S02, S01 |
| A25 | Disburse funds | Disbursement Officer | CBS | Loan account created, funds credited | Wrong account details; misses payment cut-off | S02, S07 |
| A26 | Send welcome pack and archive file | Disbursement Officer | CBS, DMS, email | Welcome pack sent, file archived (end) | Signed copies not sent to customer; incomplete archive | S02, S07 |

---

## Conclusion

- **26 activities, 5 stages, 7 actors, 6 systems** (including email).
- Customer data is **typed more than once** (A2, then again in A15–A16).
- The main rework loop is the **document chase (A8)**, which can repeat. A11 and A24 can also send files back.
- The **credit report is pulled late (A14)**, so applications that will fail still go through most of the process.
- Several handoffs happen **by email** (A8, A12, A13, A18), so their status isn't visible in the LOS.