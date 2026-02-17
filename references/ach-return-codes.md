# ACH Return Reason Codes

> Last updated: 2026-02. ACH returns are governed by NACHA (National Automated Clearing House Association) rules.
> Returns are initiated by the **RDFI** (Receiving Depository Financial Institution) and sent back to the
> **ODFI** (Originating Depository Financial Institution). ACH returns are **not traditional chargebacks** --
> they are payment returns through the ACH network and are generally not contested like card disputes.
> Return windows vary: **2 banking days** for most administrative returns, **60 calendar days** for unauthorized returns.
> NACHA compliance thresholds: **15%** overall return rate, **3%** administrative return rate (R02, R03, R04),
> **0.5%** unauthorized return rate (R05, R07, R10, R29).

---

## R01 -- Insufficient Funds

**Category:** Administrative
**Return Window:** RDFI must return within 2 banking days of settlement.

**Description:**
The account does not have sufficient available funds to cover the transaction amount. This is the single most common ACH return code and does not necessarily indicate fraud or intent -- the customer may simply have a low balance at the time of the debit.

**Common Causes:**
- Customer's account balance is below the debit amount at time of settlement
- Timing mismatch between when the debit posts and when the customer expected funds to be available
- Customer has multiple debits posting on the same day, exhausting available balance
- Recurring payment scheduled before the customer's paycheck deposits

**Preventive Measures:**
- Implement account balance verification or validation services before initiating debits
- Align debit timing with the customer's known pay cycle (e.g., debit on the 3rd rather than the 1st)
- Send payment reminders 2-3 days before the scheduled debit so customers can ensure funds are available
- Offer customers the ability to choose their preferred debit date

**Strategy Tips:**
- Retry the transaction up to 2 times within 30 days of the original authorization date (per NACHA rules); retrying more than twice or after 30 days is a violation
- Allow 3-5 business days between retry attempts to give the customer time to fund their account
- Contact the customer to confirm funds availability before retrying

**What to Do When Received:**
1. Note the return date and begin the 30-day retry window countdown
2. Contact the customer to inform them of the failed payment and discuss timing for a retry
3. If retries also fail, request an alternative payment method
4. Update internal records and monitor this customer's account for repeat R01 returns

---

## R02 -- Account Closed

**Category:** Administrative
**Return Window:** RDFI must return within 2 banking days of settlement.

**Description:**
The bank account that was previously active has been closed by the account holder. The routing and account number are valid, but the account no longer accepts transactions.

**Common Causes:**
- Customer closed their bank account and did not update their payment information with the merchant
- Customer switched banks and forgot to cancel recurring ACH debits from the old account
- Bank closed the account due to inactivity, overdraft, or compliance reasons

**Preventive Measures:**
- Implement account validation services that check account status before initiating debits
- Send periodic reminders to customers to update their banking information if it has changed
- Process Notification of Change (NOC) entries promptly when received from the ACH network
- Monitor for R02 returns and proactively reach out to affected customers

**Strategy Tips:**
- Do not retry the transaction on a closed account -- it will return again
- Contact the customer immediately for updated bank account information or an alternative payment method
- This code counts toward the 3% administrative return rate threshold (R02, R03, R04); sustained high R02 rates can trigger NACHA enforcement

**What to Do When Received:**
1. Immediately flag the customer's payment method as invalid in your system
2. Suspend any future scheduled debits to this account
3. Contact the customer to obtain new banking details or an alternative payment method
4. Update your records and re-initiate only after receiving verified new account information

---

## R03 -- No Account / Unable to Locate Account

**Category:** Administrative
**Return Window:** RDFI must return within 2 banking days of settlement.

**Description:**
The account number structure is valid, but it does not correspond to any individual account at the RDFI. The bank cannot find an account matching the provided number.

**Common Causes:**
- Customer provided an incorrect account number (transposed digits, missing digits)
- Account number was entered incorrectly during onboarding or enrollment
- The account number belongs to a different financial institution than the one indicated by the routing number
- Data entry error when migrating customer records between systems

**Preventive Measures:**
- Implement real-time account validation (micro-deposit verification or instant account verification) during enrollment
- Use front-end validation to check account number format and length before submission
- Require customers to enter their account number twice for confirmation
- Validate routing number and account number pairs using verification services

**Strategy Tips:**
- Do not retry with the same account information -- contact the customer first
- This code counts toward the 3% administrative return rate threshold; high R03 rates indicate a data quality problem in your enrollment process
- Review your onboarding flow to identify where account number errors are being introduced

**What to Do When Received:**
1. Flag the payment method as invalid
2. Contact the customer to verify the correct routing number, account number, and account type
3. Re-verify the corrected information through account validation before re-initiating
4. Audit your enrollment process if R03 rates are elevated

---

## R04 -- Invalid Account Number

**Category:** Administrative
**Return Window:** RDFI must return within 2 banking days of settlement.

**Description:**
The account number structure is invalid -- wrong number of digits, incorrect format, or fails check-digit validation. The RDFI cannot process the entry because the account number does not conform to the expected format.

**Common Causes:**
- Customer provided an account number with too many or too few digits
- Typographical error during data entry
- Account number from a non-US financial institution was entered
- System migration or data import corrupted account number data

**Preventive Measures:**
- Implement check-digit validation algorithms on account numbers before submission
- Validate account number length against the RDFI's expected format
- Use Plaid, Yodlee, or similar services for programmatic account verification
- Require double-entry confirmation of account numbers in enrollment forms

**Strategy Tips:**
- Do not retry with the same invalid number -- it will always fail
- This code counts toward the 3% administrative return rate threshold (R02, R03, R04)
- If you see systematic R04 returns, audit your data entry and import processes for corruption

**What to Do When Received:**
1. Flag the payment method as invalid in your system
2. Contact the customer to obtain the correct account number
3. Validate the new account number before re-initiating
4. Review your ACH file generation process for data integrity issues

---

## R05 -- Unauthorized Debit to Consumer Account

**Category:** Unauthorized
**Return Window:** RDFI may return within 60 calendar days of settlement.

**Description:**
A debit entry was applied to a consumer account without proper authorization, or a corporate SEC code (CCD/CTX) was used to debit a consumer account. The consumer has told their bank the debit was not authorized. This is a serious return code that is actively monitored by NACHA.

**Common Causes:**
- Using a corporate SEC code (CCD or CTX) to debit a consumer account instead of PPD or WEB
- Consumer does not recognize the transaction due to an unfamiliar company name in the ACH entry
- Authorization was not properly obtained before initiating the debit
- Consumer forgot they authorized the payment and disputes it with their bank

**Preventive Measures:**
- Always use the correct SEC code: PPD for prearranged consumer debits, WEB for internet-initiated consumer debits; never use CCD/CTX for consumer accounts
- Maintain signed or electronically captured authorization records for every consumer debit
- Use a clear, recognizable company name in the ACH Company Name field so consumers can identify the charge
- Send transaction confirmation notifications so consumers expect the debit on their statement
- Retain authorization records for at least 2 years after the last transaction (NACHA requirement)

**Strategy Tips:**
- R05 counts toward the critical 0.5% unauthorized return rate threshold; exceeding this triggers NACHA enforcement, fines, and potential suspension
- While ACH returns generally cannot be "fought," maintaining proper authorization documentation protects you if NACHA or your ODFI audits your practices
- Implement a robust authorization workflow: capture date, amount, frequency, and consumer consent method for every debit

**What to Do When Received:**
1. Immediately cease all future debits to this account
2. Pull the authorization record for this consumer and verify it is complete and valid
3. Contact the consumer to understand the dispute and attempt resolution
4. If authorization was valid, provide documentation to your ODFI -- they may be able to challenge the return in limited circumstances
5. Review your SEC code usage to ensure compliance

---

## R07 -- Authorization Revoked by Customer

**Category:** Unauthorized
**Return Window:** RDFI may return within 60 calendar days of settlement.

**Description:**
The customer who previously authorized recurring ACH debits has formally revoked their authorization by notifying their bank. Unlike R08 (which stops a single payment), R07 revokes all future authorization for the originator to debit the account.

**Common Causes:**
- Customer cancelled a subscription or service but the merchant continued debiting
- Customer contacted their bank to stop all debits from the originator rather than contacting the merchant directly
- Customer disputes the ongoing relationship with the originator
- Merchant failed to process a cancellation request in a timely manner

**Preventive Measures:**
- Provide a clear, easy-to-use cancellation process so customers cancel with you first (before going to their bank)
- Process cancellation requests promptly and send written confirmation
- Send advance notice before each recurring debit so customers can cancel before the charge
- Maintain timestamped logs of all authorization and cancellation activity
- Honor cancellation requests immediately -- do not process "one more" debit after cancellation

**Strategy Tips:**
- R07 counts toward the 0.5% unauthorized return rate threshold
- Once received, you must cease all debits immediately; continuing to debit after R07 is a NACHA violation and can result in severe penalties
- If the customer revoked authorization in error, obtain new written authorization before re-initiating any debits

**What to Do When Received:**
1. Immediately stop all future scheduled debits to this account
2. Review your records to determine if a cancellation request was received and whether it was honored
3. Contact the customer to confirm they intended to revoke authorization and attempt to resolve
4. If the customer wants to continue service, obtain a new signed authorization before re-initiating debits
5. Document everything for NACHA compliance purposes

---

## R08 -- Payment Stopped

**Category:** Administrative
**Return Window:** RDFI must return within 2 banking days of settlement.

**Description:**
The account holder has placed a stop payment order on a specific ACH debit transaction. Unlike R07 (which revokes all authorization from the originator), R08 applies to a single specific payment only.

**Common Causes:**
- Customer disputes a specific charge amount and instructed their bank to stop it
- Customer placed a stop payment due to a billing disagreement or service issue
- Customer expected a refund or credit and stopped the payment when it was not received
- Customer stopped payment on a transaction they believe was processed in error

**Preventive Measures:**
- Resolve billing disputes and customer complaints promptly before they escalate to stop payments
- Provide clear invoices and billing statements so customers understand each charge
- Offer easy-to-reach customer support channels for billing questions
- Send payment reminders before debiting so customers can raise concerns in advance

**Strategy Tips:**
- Do not retry a stopped payment without obtaining new, explicit authorization from the customer
- R08 is administrative (2-day return window), not unauthorized, so it does not count toward the 0.5% unauthorized threshold
- Use the stop payment as an opportunity to address the customer's underlying concern

**What to Do When Received:**
1. Do not retry the stopped payment
2. Contact the customer to understand why they stopped the payment
3. Resolve any underlying billing dispute or service issue
4. Obtain new authorization before attempting to collect the payment again
5. If the dispute cannot be resolved, pursue alternative collection methods

---

## R10 -- Customer Advises Originator is Not Known and/or Not Authorized

**Category:** Unauthorized
**Return Window:** RDFI may return within 60 calendar days of settlement.

**Description:**
The account holder has told their bank that they do not know the originator of the transaction and/or did not authorize the debit. This is one of the most serious unauthorized return codes because the customer is denying any relationship with or knowledge of the originator.

**Common Causes:**
- The Company Name in the ACH entry does not match what the customer recognizes (e.g., using a parent company name instead of the brand name)
- The customer genuinely did not authorize the transaction (potential fraud or identity theft)
- The customer forgot they authorized the payment and does not recognize it on their statement
- A third party (spouse, employee) authorized the payment without the account holder's knowledge

**Preventive Measures:**
- Use a company name in ACH entries that customers will recognize -- match your billing name to how customers know your brand
- Send confirmation emails or texts immediately after authorization is obtained
- Send advance notice before each debit with clear identification of the charge
- Maintain comprehensive authorization records including IP address, timestamp, and method of consent for WEB entries
- Implement identity verification during enrollment to prevent unauthorized third-party sign-ups

**Strategy Tips:**
- R10 counts toward the critical 0.5% unauthorized return rate threshold; even a small number of R10 returns can push you over the threshold
- Proper authorization documentation is your best defense if audited by NACHA or your ODFI
- Review your Company Name and Company ID fields -- if customers consistently do not recognize your debits, this is the first thing to fix

**What to Do When Received:**
1. Immediately cease all debits to this account
2. Pull the authorization record for this transaction and verify it is complete
3. Contact the customer to clarify the relationship and authorization status
4. If authorization exists, provide documentation to your ODFI
5. If the customer denies the relationship, investigate for potential fraud or enrollment errors
6. Review your Company Name field to ensure it is recognizable to customers

---

## R29 -- Corporate Customer Advises Not Authorized

**Category:** Unauthorized
**Return Window:** RDFI must return within 2 banking days of settlement.

**Description:**
A corporate account holder has notified their bank that the originator is not authorized to debit their account. This is the corporate equivalent of R10 and applies to CCD and CTX entries against business accounts.

**Common Causes:**
- Authorization agreement between the companies has expired or was never properly executed
- The corporate customer's accounts payable department does not recognize the debit
- Personnel changes at the corporate customer resulted in loss of institutional knowledge about the authorization
- The originator debited the wrong corporate account

**Preventive Measures:**
- Maintain signed corporate authorization agreements with clear terms, effective dates, and authorized signatories
- Send reminders to corporate customers before initiating debits, especially for new or infrequent transactions
- Verify the correct account and authorization with the corporate customer's accounts payable department
- Keep authorization agreements current and renew them periodically
- Store authorization records securely and make them easily retrievable for audit purposes

**Strategy Tips:**
- R29 counts toward the 0.5% unauthorized return rate threshold
- Corporate authorizations should name specific authorized signatories and be stored with your accounts receivable documentation
- Unlike consumer unauthorized returns (60-day window), R29 has only a 2 banking day return window, so you will see these returns quickly

**What to Do When Received:**
1. Immediately cease all debits to this corporate account
2. Retrieve the authorization agreement and verify it is current and properly signed
3. Contact the corporate customer's accounts payable or treasury department to clarify
4. If authorization exists and is valid, provide documentation to your ODFI
5. Obtain a new authorization agreement before re-initiating any debits

---

## R06 -- Returned per ODFI's Request

**Category:** Referral / Regulatory
**Return Window:** Determined by agreement between ODFI and RDFI; RDFI must respond within 2 banking days of the ODFI's request.

**Description:**
The Originating Depository Financial Institution (ODFI) has requested the RDFI to return the ACH entry. This is typically initiated when the originator or ODFI discovers an error in the transaction after it was submitted.

**Common Causes:**
- The originator discovered a duplicate or erroneous entry after submission and asked the ODFI to recall it
- The ODFI identified a compliance issue with the entry
- The originator requested a reversal through the ODFI

**Preventive Measures:**
- Implement pre-submission review and validation of ACH files to catch errors before they are sent
- Use batch reconciliation to identify duplicate or incorrect entries before settlement
- Maintain clear communication channels with your ODFI for timely error reporting

**Strategy Tips:**
- R06 is typically initiated by you (the originator) or your ODFI, so it indicates an internal process issue rather than a customer problem
- Review your ACH file generation and submission workflow to prevent the errors that caused the recall

**What to Do When Received:**
1. Confirm the reason for the return with your ODFI
2. Correct the underlying error (wrong amount, wrong account, duplicate, etc.)
3. Re-initiate the corrected entry if appropriate
4. Update your processes to prevent recurrence

---

## R09 -- Uncollected Funds

**Category:** Administrative
**Return Window:** RDFI must return within 2 banking days of settlement.

**Description:**
The account has sufficient ledger balance, but the funds are not yet available because they are uncollected (e.g., a recently deposited check has not yet cleared). This is distinct from R01 (Insufficient Funds) -- with R09, the money exists but is on hold.

**Common Causes:**
- Customer deposited a check shortly before the ACH debit posted, and the check has not yet cleared
- Large deposit is subject to an extended hold by the customer's bank
- Customer's account has holds placed on recent deposits due to bank policy

**Preventive Measures:**
- Time debits to avoid the first few days of the month when customers may have pending deposits
- Allow sufficient lead time between when customers set up payment and when the first debit posts
- Send payment reminders so customers can ensure deposited funds have cleared

**Strategy Tips:**
- Retry the transaction (up to 2 times within 30 days of the original authorization date, per NACHA rules)
- Wait 3-5 business days before retrying to allow the uncollected funds to clear
- R09 is functionally similar to R01 for retry purposes but suggests the customer likely has the funds and simply needs time

**What to Do When Received:**
1. Wait 3-5 business days for the uncollected funds to become available
2. Retry the transaction (within the 2-retry, 30-day NACHA limit)
3. If retries fail, contact the customer for an alternative payment method
4. Monitor for patterns -- recurring R09 returns from the same customer may indicate systemic timing issues

---

## R11 -- Check Truncation Entry Return

**Category:** Referral / Regulatory
**Return Window:** Varies; specific to check truncation programs and governed by applicable regulations.

**Description:**
This code is used exclusively when returning a check truncation entry. The RDFI is unable to process the entry that was created from a truncated (converted) check, typically due to issues with the check image or data.

**Common Causes:**
- The check image is illegible, damaged, or does not meet quality standards
- Required check data fields are missing or incorrect in the ACH entry
- The check truncation entry fails the RDFI's processing criteria
- The original check was altered or contains discrepancies

**Preventive Measures:**
- Ensure check scanning equipment produces high-quality, legible images
- Validate all check data fields (MICR line, amount, payee) before creating the ACH entry
- Maintain and calibrate check scanning hardware regularly
- Train staff on proper check handling and scanning procedures

**Strategy Tips:**
- R11 is uncommon and specific to check conversion programs (ARC, BOC, POP)
- If you receive frequent R11 returns, audit your check scanning equipment and image quality processes

**What to Do When Received:**
1. Review the check image quality and data accuracy
2. If the check image is available and legible, resubmit with corrected data
3. If the original check is available, process it through traditional check clearing instead
4. Contact the customer for an alternative payment if the check cannot be reprocessed

---

## R12 -- Branch Sold to Another DFI

**Category:** Referral / Regulatory
**Return Window:** RDFI must return within 2 banking days of settlement.

**Description:**
The branch or office where the account was held has been sold to another depository financial institution. The routing number used in the ACH entry is no longer valid for this institution because the account has moved to the acquiring institution.

**Common Causes:**
- A bank branch sale or merger transferred the account to a new institution with a different routing number
- The RDFI's routing number changed due to corporate restructuring
- The originator's records were not updated to reflect the change

**Preventive Measures:**
- Process Notification of Change (NOC) entries promptly -- NOCs (C01, C02, C03, C04) provide updated routing and account information
- Monitor banking industry news for mergers and acquisitions that may affect your customers' accounts
- Implement automated NOC processing in your ACH system

**Strategy Tips:**
- Check for a corresponding NOC entry that provides the new routing number and account number
- This is an informational return, not a customer problem -- the customer likely still wants to pay but their bank information changed

**What to Do When Received:**
1. Check your NOC queue for updated routing and account information
2. Contact the customer for their new bank details if no NOC was received
3. Update your records with the new routing number and/or account number
4. Re-initiate the entry with the corrected information

---

## R13 -- Invalid ACH Routing Number

**Category:** Referral / Regulatory
**Return Window:** RDFI must return within 2 banking days of settlement.

**Description:**
The routing number in the ACH entry is not a valid ACH participant routing number. It does not correspond to any financial institution in the ACH network, or the institution is not an ACH participant.

**Common Causes:**
- Customer provided an incorrect routing number (transposed digits, wrong bank's number)
- The routing number belongs to a non-ACH-participant institution (e.g., some credit unions or international banks)
- Data entry error during enrollment or payment setup
- The routing number was recently deactivated

**Preventive Measures:**
- Validate routing numbers against the Federal Reserve's routing number directory before submitting ACH entries
- Implement real-time routing number lookup during enrollment to verify the number is valid and active
- Require customers to provide a voided check or bank statement for account verification

**Strategy Tips:**
- Do not retry with the same routing number -- it will fail again
- This is a data quality issue; fix it at the source during enrollment

**What to Do When Received:**
1. Flag the payment method as invalid
2. Contact the customer to obtain the correct routing number
3. Validate the new routing number against the Federal Reserve directory before re-initiating
4. Review your enrollment process for routing number validation gaps

---

## R14 -- Representative Payee Deceased or Unable to Continue

**Category:** Referral / Regulatory
**Return Window:** RDFI returns by the next file delivery time following processing.

**Description:**
The representative payee -- a person authorized to receive payments on behalf of another individual (such as a minor, elderly person, or disabled individual) -- is either deceased or no longer able to continue serving in that capacity.

**Common Causes:**
- The representative payee has passed away
- The representative payee has become incapacitated and can no longer manage the account
- The representative payee's authority has been legally revoked or transferred

**Preventive Measures:**
- Maintain current contact information for both the representative payee and the beneficiary
- Periodically verify that the representative payee is still active and authorized
- For recurring payments, confirm the arrangement is still valid at regular intervals

**Strategy Tips:**
- This is a sensitive situation requiring careful handling; do not simply retry the transaction
- The underlying beneficiary may still be entitled to receive payments, but a new representative payee or payment arrangement is needed

**What to Do When Received:**
1. Cease all entries to this account immediately
2. Contact the beneficiary, their family, or legal representative to establish a new payment arrangement
3. Obtain new authorization and updated account information from the new representative payee
4. Update your records before re-initiating any entries

---

## R15 -- Beneficiary or Account Holder Deceased

**Category:** Referral / Regulatory
**Return Window:** RDFI must return within 2 banking days of settlement.

**Description:**
The beneficiary or account holder has died. The bank has been notified of the death and the account is typically frozen or restricted, preventing any further ACH activity.

**Common Causes:**
- The account holder has passed away and the bank has been notified
- The estate has not yet designated a new account for receiving payments or settling debts

**Preventive Measures:**
- For recurring payment relationships, periodically verify account holder status
- Maintain alternative contact information (next of kin, estate representative) for critical payment relationships
- Implement processes to handle deceased account holder notifications promptly

**Strategy Tips:**
- Immediately cease all entries to this account; continuing to debit a deceased person's account creates legal and compliance risks
- Work with the estate's executor or administrator for any outstanding balances

**What to Do When Received:**
1. Immediately stop all future ACH entries to this account
2. Flag the account in your system as deceased/inactive
3. Contact the estate's executor, administrator, or next of kin for resolution of any outstanding balance
4. For credit entries (payments owed to the deceased), coordinate with the estate for proper disbursement

---

## R16 -- Account Frozen

**Category:** Referral / Regulatory
**Return Window:** RDFI must return within 2 banking days of settlement.

**Description:**
The account has been frozen due to a legal action such as a court order, tax levy, garnishment, or bankruptcy. Alternatively, the Office of Foreign Assets Control (OFAC) may have instructed the institution to block the account. No ACH transactions can be processed against a frozen account.

**Common Causes:**
- Court-ordered account freeze due to litigation or judgment
- IRS or state tax levy placed on the account
- Bankruptcy filing triggered an automatic stay on the account
- OFAC sanctions compliance requires the account to be blocked
- Bank froze the account due to suspected fraud or suspicious activity

**Preventive Measures:**
- There is no way to prevent this return in advance -- account freezes are external legal actions
- Maintain alternative contact methods for the customer in case their primary account becomes unavailable
- For high-value recurring payment relationships, consider backup payment methods

**Strategy Tips:**
- Do not retry against a frozen account; the freeze will remain in place until the legal matter is resolved
- If OFAC is involved, exercise extreme caution and consult legal counsel before taking any action
- Account freezes are typically temporary, but the timeline is unpredictable

**What to Do When Received:**
1. Suspend all future ACH entries to this account
2. Contact the customer (if legally appropriate) to discuss alternative payment arrangements
3. If OFAC-related, consult your compliance team and legal counsel immediately
4. Monitor the situation and only resume entries when confirmed the freeze has been lifted
5. Do not attempt to collect the debt through other means without understanding the legal situation

---

## R17 -- File Record Edit Criteria

**Category:** Referral / Regulatory
**Return Window:** RDFI must return within 2 banking days of settlement.

**Description:**
The ACH entry contains a field that does not meet the RDFI's or the ACH Operator's file record edit criteria. One or more data fields are improperly formatted, contain invalid values, or are missing required data elements per NACHA file specifications.

**Common Causes:**
- Invalid field format in the ACH entry (wrong data type, incorrect length)
- Missing required fields in the batch or entry detail record
- SEC code does not match the transaction type or entry class
- File or batch header/control totals do not balance

**Preventive Measures:**
- Validate ACH files against NACHA format specifications before submission
- Use ACH file generation software that enforces field-level validation rules
- Test file formatting with your ODFI or ACH processor before going live
- Implement automated pre-submission file validation checks

**Strategy Tips:**
- R17 is a technical/formatting issue, not a customer problem; fix the file generation process
- Work with your ODFI or ACH processor to identify exactly which field(s) failed validation
- This should be rare if your ACH file generation is properly configured

**What to Do When Received:**
1. Contact your ODFI or ACH processor to identify the specific field(s) that failed validation
2. Correct the formatting issue in your ACH file generation system
3. Resubmit the corrected entry
4. Add validation checks to prevent the same formatting error in future files

---

## R20 -- Non-Transaction Account

**Category:** Referral / Regulatory
**Return Window:** RDFI must return within 2 banking days of settlement.

**Description:**
The ACH entry was directed to a non-transaction account -- an account type that does not permit the specific type of ACH transaction. For example, a savings account that does not allow ACH debits, or a loan account that only accepts credits.

**Common Causes:**
- Customer provided a savings account number for a debit transaction, but the account type does not permit ACH debits
- The account is a specialized account (CD, IRA, loan) that restricts certain transaction types
- Customer confused their account types when providing banking information

**Preventive Measures:**
- During enrollment, ask customers to confirm their account type (checking vs. savings) and verify it supports ACH debits
- Use account validation services that confirm the account type supports the intended transaction
- Clearly communicate that you need a checking account (or ACH-debit-eligible account) for payment purposes

**Strategy Tips:**
- Do not retry against the same account -- the account type restriction will not change
- Contact the customer for a different account that supports ACH debits (typically a checking account)

**What to Do When Received:**
1. Flag the payment method as incompatible with ACH debits
2. Contact the customer to obtain a checking account or other ACH-debit-eligible account
3. Verify the new account type before re-initiating
4. Update your enrollment forms to clarify account type requirements

---

## R21 -- Invalid Company Identification

**Category:** Referral / Regulatory
**Return Window:** RDFI must return within 2 banking days of settlement.

**Description:**
The company identification field in the ACH batch header is not valid. The RDFI cannot identify or validate the originating company based on the identification number provided (typically the EIN/Tax ID or a NACHA-assigned number).

**Common Causes:**
- Incorrect EIN or Tax ID in the ACH file's company identification field
- Company identification number was not properly registered with the ODFI
- Data entry error in the batch header when generating the ACH file
- Company identification format does not match RDFI expectations

**Preventive Measures:**
- Verify your company identification (EIN/Tax ID) is correctly configured in your ACH file generation system
- Confirm the company identification format with your ODFI during onboarding
- Test ACH file generation with your processor before going into production

**Strategy Tips:**
- This is a configuration issue, not a customer problem; work with your ODFI to correct it
- Once fixed, all entries should process normally

**What to Do When Received:**
1. Contact your ODFI to verify the correct company identification number and format
2. Update your ACH file generation configuration with the correct company ID
3. Resubmit the corrected entry
4. Validate company identification in all ACH file templates

---

## R22 -- Invalid Individual ID Number

**Category:** Referral / Regulatory
**Return Window:** RDFI must return within 2 banking days of settlement.

**Description:**
The individual identification number in the ACH entry detail record is invalid. This field is used primarily for CIE (Customer Initiated Entry) and certain other SEC codes where individual identification is required by the RDFI.

**Common Causes:**
- The individual ID number format does not match the RDFI's requirements
- The ID number is missing or contains invalid characters
- The entry uses a SEC code that requires individual identification but the field is empty or incorrect

**Preventive Measures:**
- Verify individual ID number format requirements with the RDFI before submission
- Validate the individual ID field in the entry detail record before generating the ACH file
- Ensure your system populates the individual ID field correctly for the SEC code being used

**Strategy Tips:**
- This is an uncommon return code; if received, it typically indicates a configuration or data mapping issue in your ACH system
- Work with your ODFI to understand the specific ID format required

**What to Do When Received:**
1. Contact your ODFI to determine the correct individual ID format
2. Verify the customer's identification information
3. Correct the entry and resubmit with valid individual identification
4. Update your ACH system configuration to properly format the individual ID field

---

## R23 -- Credit Entry Refused by Receiver

**Category:** Referral / Regulatory
**Return Window:** RDFI must return within 2 banking days of settlement.

**Description:**
The receiver (account holder) has refused an ACH credit entry. This can occur when the receiver does not want to accept the payment, or the credit does not meet minimum payment requirements set by the receiver or the RDFI.

**Common Causes:**
- The receiver does not want to accept a credit from this originator
- The credit amount does not meet a minimum threshold required by the receiver or RDFI
- The receiver has instructed their bank to refuse credits from certain originators
- The credit is for a disputed or contested amount

**Preventive Measures:**
- Communicate with the receiver before sending credits to confirm they will accept the payment
- Verify minimum payment thresholds and receiver preferences before initiating credit entries
- Obtain the receiver's agreement to accept ACH credits from your organization

**Strategy Tips:**
- This is a receiver-driven decision; you cannot override their refusal
- Contact the receiver to understand why they refused the credit and arrange alternative payment delivery

**What to Do When Received:**
1. Contact the receiver to understand why the credit was refused
2. Determine if there is a minimum payment threshold that was not met
3. Arrange alternative payment delivery if the receiver does not want ACH credits
4. Do not re-initiate the credit without the receiver's agreement

---

## R24 -- Duplicate Entry

**Category:** Referral / Regulatory
**Return Window:** RDFI must return within 2 banking days of settlement.

**Description:**
The ACH entry is a duplicate of a previously processed entry. The RDFI has identified matching trace number, amount, and other key fields that indicate this entry has already been settled.

**Common Causes:**
- The same ACH file was submitted twice (e.g., after a timeout or error during transmission)
- A batch was reprocessed without realizing it had already settled
- System error generated duplicate entries in the ACH file
- Manual resubmission of an entry that had already been processed successfully

**Preventive Measures:**
- Implement duplicate detection logic in your ACH file generation system (check trace numbers, amounts, and dates)
- Track submitted file and batch IDs to prevent resubmission
- Use unique trace numbers for every legitimate ACH entry
- Implement idempotency controls in your payment processing workflow
- Reconcile ACH submissions against settlement reports daily

**Strategy Tips:**
- If the entries are legitimately separate transactions, ensure each has a unique trace number and that identifying data elements differ
- Review your file submission logs to determine whether the duplicate was caused by a system error or process issue

**What to Do When Received:**
1. Verify whether the entry was truly a duplicate or a legitimate separate transaction
2. If it was a genuine duplicate, no further action is needed -- the original entry was already processed
3. If the entries represent separate legitimate transactions, resubmit with unique trace numbers and identifiers
4. Fix the root cause of the duplication in your file generation or submission process

---

## R28 -- Routing Number Check Digit Error

**Category:** Referral / Regulatory
**Return Window:** RDFI must return within 2 banking days of settlement.

**Description:**
The routing number in the ACH entry fails the check digit validation algorithm. The ninth digit of the routing number (the check digit) does not match the calculated value based on the first eight digits, indicating the routing number is incorrect.

**Common Causes:**
- Customer provided a routing number with transposed or incorrect digits
- Data entry error during enrollment or payment setup
- System error corrupted the routing number during processing or storage

**Preventive Measures:**
- Implement routing number check digit validation before submitting ACH entries (the algorithm uses a weighted sum of the first 8 digits modulo 10)
- Validate routing numbers at the point of entry during enrollment
- Cross-reference routing numbers against the Federal Reserve's official directory

**Strategy Tips:**
- This is always a data quality issue; never retry with the same routing number
- The check digit algorithm is simple to implement and should catch most errors before submission

**What to Do When Received:**
1. Flag the payment method as invalid
2. Contact the customer to obtain the correct routing number
3. Validate the new routing number using the check digit algorithm before re-initiating
4. Add check digit validation to your enrollment and file generation processes if not already present

---

## R33 -- Return of XCK Entry

**Category:** Referral / Regulatory
**Return Window:** May be returned up to 60 calendar days after the settlement date.

**Description:**
An XCK (Destroyed Check) entry has been returned. XCK entries are created when an original check is destroyed during the conversion to ACH, and the ACH entry subsequently needs to be returned. This code provides a mechanism for returning converted check entries within an extended time frame.

**Common Causes:**
- The original check was destroyed, lost, or damaged during the conversion process and the ACH entry cannot be honored
- The check image captured during conversion is unprocessable or illegible
- The receiver disputes the converted check entry
- The RDFI cannot process the XCK entry for technical or compliance reasons

**Preventive Measures:**
- Ensure check images are captured at high quality before destroying original checks
- Maintain backup copies or images of all checks before conversion
- Verify check data accuracy (amount, account number, routing number) before creating the XCK entry
- Follow NACHA and Federal Reserve guidelines for check conversion and destruction timelines

**Strategy Tips:**
- R33 has a 60-day return window, much longer than most administrative returns -- factor this into your cash flow planning for check conversion programs
- This code is specific to check conversion programs (ARC, BOC, POP); if you do not operate such programs, you should not see R33 returns

**What to Do When Received:**
1. Review the check image and conversion records for the entry
2. If the check image is available and legible, work with your ODFI to resolve
3. Contact the customer for an alternative payment method if the entry cannot be reprocessed
4. Review your check conversion and destruction procedures to prevent recurrence

---

## Quick Reference

### ACH Return Codes by Category

| Category | Codes | Return Window |
|----------|-------|---------------|
| Administrative | R01, R02, R03, R04, R08, R09 | 2 banking days |
| Unauthorized | R05, R07, R10, R29 | 60 calendar days (R05, R07, R10); 2 banking days (R29) |
| Referral / Regulatory | R06, R11, R12, R13, R14, R15, R16, R17, R20, R21, R22, R23, R24, R28, R33 | 2 banking days (most); 60 calendar days (R33); varies (R06, R11) |

### Return Window Summary

| Window | Codes | Notes |
|--------|-------|-------|
| 2 banking days | R01, R02, R03, R04, R06, R08, R09, R12, R13, R14, R15, R16, R17, R20, R21, R22, R23, R24, R28, R29 | Standard administrative/regulatory returns |
| 60 calendar days | R05, R07, R10 | Consumer unauthorized returns |
| 60 calendar days | R33 | XCK (destroyed check) entries |
| Varies | R11 | Check truncation; program-specific |

### NACHA Compliance Thresholds

| Metric | Threshold | Monitored Codes |
|--------|-----------|-----------------|
| Overall Return Rate | 15% | All R-codes |
| Administrative Return Rate | 3% | R02, R03, R04 |
| Unauthorized Return Rate | 0.5% | R05, R07, R10, R29 |

### Retry Rules (NACHA)

| Rule | Detail |
|------|--------|
| Maximum retries | 2 attempts after the original entry |
| Retry window | Within 30 days of the original authorization date |
| Eligible codes | R01, R09 (and similar funds-availability returns) |
| Not eligible for retry | R02, R03, R04, R05, R07, R08, R10, R13, R14, R15, R16, R20, R29 (and most others) |
