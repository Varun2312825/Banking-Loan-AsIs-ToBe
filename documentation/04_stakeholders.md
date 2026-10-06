**Project: Banking Loan Process — As-Is / To-Be**

**Prepared by: Varun**

**Date: 25 September 2026**



**Stakeholders are listed by role, not by name. Roles are what appear in the process model, and a role-based register stays valid even if people change jobs or the bank reorganises.**



&#x20;**Stakeholder register**



**| Stakeholder role | Type | Their role in the process | What they care about | Their pain | How i would elicit from them |**

**|---|---|---|---|---|---|**

**| Client (applicant) | External | Submits the application, provides KYC and income documents, accepts the sanction, signs the agreement and sets up the repayment mandate | Fast decision, certainty about approval, not being asked for the same thing twice | Repeated document requests, no visibility of application status, long wait for funds | Survey, review of public customer complaints and app reviews, own experience of applying for a loan |**

**| Branch Sales Officer / Relationship Manager | Internal | Captures the application in the LOS, collects documents, forwards the file to Credit Operations, relays document requests back to the customer | Meeting sales targets, keeping customers happy, spending time selling rather than chasing paperwork | Chasing customers for missing documents, re-entering data, customers calling for status updates | Interview, process observation at a branch |**

**| Credit Operations Analyst | Internal | Checks document completeness, verifies KYC against the registry, validates identity and PAN, verifies employment, pulls the credit bureau report | Clean, complete files; manageable queue; meeting turnaround SLAs | Incomplete files, switching between LOS, DMS and email, re-keying data, files bounced back to the branch | Interview, process observation, system walkthrough |**

**| Underwriter | Internal | Assesses income and obligations, calculates debt-to-income ratio, applies credit policy, refers deviations, records the credit decision | Making sound credit decisions, having all information in one place, a defensible decision record | Doing data entry instead of analysis, files arriving incomplete, waiting for deviation approvals | Interview, document analysis of credit policy, walkthrough of a sample file |**

**| Risk \& Compliance Officer | Internal | Performs the final compliance check before disbursal, reviews negative-list and fraud hits, ensures regulatory controls are followed | Every mandatory control performed and evidenced, a complete audit trail, no regulatory breaches | Manual checks late in the process, missing evidence in files, controls done inconsistently | Interview, document analysis of RBI directions and internal policies |**

**| Disbursement Officer | Internal | Generates the sanction letter, executes the loan agreement, sets up the repayment mandate, releases funds, archives the file | Accurate, complete paperwork before releasing money | Mandate registration failures, unsigned or incorrect agreements, files arriving late in the day | Interview, process observation |**

**| IT / LOS Application Owner | Internal | Owns and configures the Loan Origination System and its integrations with CBS, DMS, the bureau and the KYC registry | System stability, realistic change requests, clear requirements | Manual workarounds bridging systems, vague change requests from the business | System walkthrough, interview, review of system documentation |**

**| Head of Retail Lending (Sponsor) | Internal | Owns the lending business and the project; approves scope, requirements and investment | Loan volumes, turnaround time vs competitors, cost per loan, regulatory safety | Losing applications to faster lenders, rising operations cost, no visibility of where delays occur | Interview (first, to agree scope and success criteria), review of management reports |**

**| Regulator (RBI) | Regulatory | Sets the rules the process must follow: KYC, AML, digital lending, borrower disclosure. Does not perform tasks in the process | Customer protection, fair lending, financial system integrity | Not applicable (sets constraints rather than experiencing the process) | Document analysis of RBI Master Directions and circulars |**



**| Role | Appears in the BPMN model as |**

**|---|---|**

**| Customer | Separate pool (external participant) |**

**| Branch Sales Officer / Relationship Manager | Lane: Branch / Sales |**

**| Credit Operations Analyst | Lane: Credit Operations |**

**| Underwriter | Lane: Underwriting |**

**| Disbursement Officer | Lane: Disbursement \& Compliance |**

**| Risk \& Compliance Officer | Lane: Disbursement \& Compliance (final compliance check); also reviews fraud referrals |**

**| IT / LOS Application Owner | No lane — owns the systems, does not perform process tasks |**

**| Head of Retail Lending (Sponsor) | No lane — owns the project, does not perform process tasks |**

**| Regulator (RBI) | No lane — sets constraints only |**



**Decision: Branch Sales Officer and Relationship Manager are modelled as \*\*one lane\*\*, because both perform the same work on the same object (capturing the application and collecting documents).**



**Note: The sponsor, IT owner and regulator have no lane because they do not perform tasks inside the process. They are still key stakeholders: the sponsor approves the project, IT owns every system requirement, and the regulator defines the controls that the To-Be has to preserve.**

