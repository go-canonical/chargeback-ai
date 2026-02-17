# Visa Chargeback Reason Codes

> Last updated: 2026-02. Visa organizes disputes into four categories under Visa Claims Resolution (VCR):
> Fraud (10.x), Authorization (11.x), Processing Errors (12.x), and Consumer Disputes (13.x).
> Merchant response window: **30 days** for all codes.

---

## 10.1 — EMV Liability Shift Counterfeit Fraud

**Category:** Fraud (Allocation workflow)
**Time Limit:** Issuer must file within 120 days of the transaction date. Merchant has 30 days to respond.

**Description:**
A counterfeit card was used at a terminal that did not support EMV chip reading. Under the EMV liability shift, the merchant bears liability for counterfeit fraud when their terminal falls back to magnetic stripe instead of reading the chip.

**Required Evidence:**
- Proof that the transaction was processed via EMV chip (not mag stripe fallback)
- TC (Transaction Certificate) or cryptogram proving chip was read and data transmitted to the issuer
- Terminal ID and certification records showing EMV compliance at time of transaction

**Compelling Evidence (improves win rate):**
- EMV terminal certification documentation from the acquirer or processor
- Full chip data log from the transaction showing application cryptogram
- Evidence the card's chip was malfunctioning (if the terminal attempted chip read but fell back)

**Strategy Tips:**
- This code is only valid for card-present transactions; if you processed via chip, gather the TC/cryptogram data immediately
- Ensure all terminals are EMV-certified and maintain certification records; this is the single best prevention measure
- If the chip read failed and you fell back to swipe, liability shifts to you and the dispute is very difficult to win

**Common Mistakes:**
- Failing to keep EMV certification records on file for each terminal
- Processing fallback swipe transactions without attempting chip insertion first
- Not training staff to insist on chip insertion before swiping

---

## 10.2 — EMV Liability Shift Non-Counterfeit Fraud

**Category:** Fraud (Allocation workflow)
**Time Limit:** Issuer must file within 120 days of the transaction date. Merchant has 30 days to respond.

**Description:**
A lost, stolen, or never-received chip card with PIN preference was used at a terminal that was not PIN-compliant. The merchant is liable because the terminal did not support PIN verification for chip transactions.

**Required Evidence:**
- Documentation proving the terminal was EMV PIN-compliant at the time of the transaction
- Transaction log showing PIN was entered and verified (application transaction counter, CVM results)
- Authorization request and response records

**Compelling Evidence (improves win rate):**
- Cardholder verification method (CVM) results showing PIN was used
- Terminal compliance certification showing PIN capability
- Video surveillance footage of the cardholder at the terminal entering their PIN

**Strategy Tips:**
- Ensure your terminals support both chip and PIN (not just chip and signature)
- Maintain up-to-date PIN pad certification; expired certifications leave you exposed
- If the card was reported lost/stolen before the transaction, the authorization response should have flagged it — check your auth logs

**Common Mistakes:**
- Using chip-and-signature terminals when the card requires PIN verification
- Not checking authorization response codes that may indicate a compromised card
- Failing to upgrade PIN pad firmware when certification expires

---

## 10.3 — Other Fraud: Card-Present Environment

**Category:** Fraud (Allocation workflow)
**Time Limit:** Issuer must file within 120 days of the transaction date. Merchant has 30 days to respond.

**Description:**
The cardholder claims a card-present transaction was unauthorized. This applies to key-entered, swiped, or unattended terminal transactions where the cardholder denies participation.

**Required Evidence:**
- Signed transaction receipt or electronic signature capture
- Authorization approval code and response
- For unattended terminals: proof that PIN was entered and validated
- For key-entered transactions: imprint of the physical card or photo ID verification record

**Compelling Evidence (improves win rate):**
- Surveillance video showing the cardholder at the point of sale
- Chip transaction data (if EMV was used) proving card was physically present
- Government-issued ID verification log matching the cardholder name
- Voice authorization records if the transaction was phone-authorized

**Strategy Tips:**
- Always obtain a signature or PIN for card-present transactions; unsigned receipts are nearly impossible to defend
- For key-entered transactions, take an imprint of the physical card and verify photo ID
- Retain surveillance footage for at least 180 days to cover the dispute window

**Common Mistakes:**
- Accepting key-entered transactions without verifying cardholder identity
- Discarding surveillance footage before the chargeback window closes
- Not obtaining proper authorization for manually entered transactions

---

## 10.4 — Other Fraud: Card-Absent Environment

**Category:** Fraud (Allocation workflow)
**Time Limit:** Issuer must file within 120 days of the transaction date. Merchant has 30 days to respond.

**Description:**
The cardholder claims a card-not-present (CNP) transaction was unauthorized. This is the most common fraud dispute code for e-commerce, phone, and mail-order transactions. Visa Compelling Evidence 3.0 (CE3.0) provides a powerful defense mechanism.

**Required Evidence:**
- AVS (Address Verification Service) match confirmation
- CVV2/CVC2 match confirmation
- 3D Secure (Visa Secure) authentication record, if used
- Order details, IP address, device fingerprint, and shipping information
- Delivery confirmation with recipient signature (for physical goods)

**Compelling Evidence (improves win rate):**
- **Visa Compelling Evidence 3.0 (CE3.0):** Provide at least two prior undisputed transactions (within 120-365 days of the disputed transaction) from the same payment card, where at least two of the following data elements match between prior transactions and the disputed transaction, and one of the two must be IP address or Device ID/fingerprint: (1) IP address, (2) Device ID/fingerprint, (3) Shipping address, (4) User account ID. If CE3.0 criteria are fully met, Visa will deny the cardholder's fraud claim.
- Proof the cardholder has an established purchase history with your business
- Communication logs (emails, chats) between you and the cardholder regarding the order
- Login/session data showing the cardholder accessed their account to place the order

**Strategy Tips:**
- Implement CE3.0 data collection now: log IP address, device fingerprint, shipping address, and user account ID for every transaction — this is the single highest-ROI fraud prevention investment for CNP merchants
- Use 3D Secure (Visa Secure) to shift liability to the issuer; authenticated transactions are largely protected
- Require CVV2 for all CNP transactions and confirm AVS match before shipping
- For digital goods, log the IP address, device, and account activity showing the customer used the product

**Common Mistakes:**
- Not collecting or retaining device fingerprint and IP address data needed for CE3.0
- Shipping high-value orders to non-AVS-matched addresses without additional verification
- Failing to implement 3D Secure when it would shift liability to the issuer
- Not linking prior undisputed transactions to build a CE3.0 defense before disputes arise

---

## 10.5 — Visa Fraud Monitoring Program

**Category:** Fraud (Allocation workflow)
**Time Limit:** Issuer must file within 120 days of the transaction date. Merchant has 30 days to respond.

**Description:**
The transaction was identified through the Visa Fraud Monitoring Program (VFMP) or the newer Visa Acquirer Monitoring Program (VAMP). Merchants exceeding fraud thresholds are enrolled in monitoring programs with escalating consequences. As of April 2025, VFMP was consolidated into VAMP with updated thresholds.

**Required Evidence:**
- Proof the transaction was legitimate and properly authorized
- Evidence of fraud prevention tools in use (3D Secure, AVS, CVV2, velocity checks)
- Documentation of fraud mitigation actions taken since program enrollment
- Transaction-level evidence similar to code 10.4

**Compelling Evidence (improves win rate):**
- Comprehensive fraud prevention audit showing tools deployed and their effectiveness
- Trend data showing declining fraud ratios since remediation began
- Third-party fraud screening results for the specific transaction
- CE3.0 evidence (same requirements as 10.4) if applicable

**Strategy Tips:**
- Monitor your fraud-to-sales ratio continuously; VAMP thresholds are: merchants in most regions have an initial threshold of 2.2%, dropping to 1.5% from April 2026 (North America, EU, Asia Pacific). The legacy VFMP thresholds were 0.65% (Early Warning), 0.9% (Standard), and 1.8% (Excessive).
- Once enrolled, focus on reducing fraud ratio below thresholds quickly — fines escalate monthly and can reach $25,000+ per month
- Implement 3D Secure, advanced fraud scoring, and velocity checks before you hit thresholds
- Work with your acquirer to develop a remediation plan immediately upon receiving an early warning

**Common Mistakes:**
- Ignoring early warning notifications and waiting until fines begin
- Not tracking fraud-to-sales ratio at the merchant ID level
- Relying solely on AVS/CVV2 without layered fraud prevention
- Failing to communicate remediation efforts to your acquirer

---

## 11.1 — Card Recovery Bulletin

**Category:** Authorization (Allocation workflow)
**Time Limit:** Issuer must file within 120 days of the transaction date. Merchant has 30 days to respond.

**Description:**
The merchant processed a transaction using a card that appeared on the Card Recovery Bulletin (CRB) or Electronic Warning Bulletin. The card had been reported lost, stolen, or compromised, and the merchant should have declined the transaction or recovered the card.

**Required Evidence:**
- Proof that an authorization approval was obtained for the transaction
- Authorization request and approval response code documentation
- Evidence that the card was not on the CRB at the time of the transaction

**Compelling Evidence (improves win rate):**
- EMV chip transaction data proving the physical card was present and PIN was validated
- Documentation from your processor confirming the CRB was checked and card was not listed
- Proof that a refund or credit has already been issued

**Strategy Tips:**
- Modern POS systems check the CRB automatically during authorization; ensure your system is configured to do so
- If you received an authorization approval despite the card being on the CRB, document the approval — this shifts liability
- Always obtain real-time authorization rather than using stored or offline approvals

**Common Mistakes:**
- Using floor limits or offline authorization that bypasses CRB checking
- Not obtaining authorization for every transaction regardless of amount
- Ignoring "pick up card" or "call center" responses from the authorization system

---

## 11.2 — Declined Authorization

**Category:** Authorization (Allocation workflow)
**Time Limit:** Issuer must file within 120 days of the transaction date. Merchant has 30 days to respond.

**Description:**
The merchant received a decline or "pick up card" response to an authorization request but processed the transaction anyway. This is one of the most clear-cut chargebacks and is very difficult to defend unless the merchant obtained a subsequent approval.

**Required Evidence:**
- Proof that a subsequent authorization request was submitted and approved after the initial decline
- Authorization approval response code from the successful request
- Transaction logs showing the timeline of authorization attempts

**Compelling Evidence (improves win rate):**
- Full authorization log showing the initial decline followed by a successful re-authorization
- Proof that the cardholder was present and provided additional verification for the re-attempt
- Documentation from the processor confirming the final authorization was valid

**Strategy Tips:**
- Never process a transaction after receiving a decline — obtain a new authorization first
- If the customer wants to retry, have them use a different card or contact their bank
- Train staff to never override or force through declined transactions

**Common Mistakes:**
- Force-posting transactions after receiving a decline response
- Re-submitting the same authorization request repeatedly hoping for approval
- Splitting a declined transaction into smaller amounts to get approvals
- Not training staff on proper decline procedures

---

## 11.3 — No Authorization

**Category:** Authorization (Allocation workflow)
**Time Limit:** Issuer must file within 120 days of the transaction date. Merchant has 30 days to respond.

**Description:**
The merchant processed a transaction without obtaining a valid authorization, or the authorization was obtained incorrectly (wrong amount, expired approval, or wrong transaction date).

**Required Evidence:**
- Valid authorization approval code for the exact transaction amount
- Authorization request and response logs with timestamps
- Proof that the authorization was obtained before the transaction was processed
- If the clearing record has an incorrect date, provide documentation of the correct transaction date

**Compelling Evidence (improves win rate):**
- Complete authorization log trail showing request, response, and settlement matching
- Processor records confirming the authorization was valid and matched the cleared amount
- Proof that a refund has already been issued if authorization truly was not obtained

**Strategy Tips:**
- Always obtain authorization before processing — no exceptions, even for small amounts
- Ensure the authorized amount matches the settled amount; partial authorizations require re-authorization for the remaining balance
- Authorization codes expire (typically 7-30 days depending on merchant category) — settle transactions promptly

**Common Mistakes:**
- Using expired authorization codes for delayed shipments
- Settling a different amount than what was authorized without obtaining a new authorization
- Not obtaining authorization for add-on charges (tips, incidentals) separately
- Relying on voice authorization without properly recording the approval code

---

## 12.1 — Late Presentment

**Category:** Processing Errors (Collaboration workflow)
**Time Limit:** Issuer must file within 120 days of the transaction date. Merchant has 30 days to respond.

**Description:**
The merchant submitted the transaction for processing past the allowed time frame, and the cardholder's account was no longer in good standing (closed, blocked, etc.) when the late transaction posted. Visa generally requires transactions to be presented within 1-2 days for electronic transactions or up to 5 days for other transaction types, though specific limits vary.

**Required Evidence:**
- Transaction receipt or processing records showing the transaction was submitted within the allowed time frame
- Proof the account was still in good standing at the time of presentment
- Documentation showing the actual transaction date and presentment date

**Compelling Evidence (improves win rate):**
- Processor records showing the batch was submitted on time
- Evidence of technical issues (system outages, processor delays) that caused the late submission
- Proof that a refund has already been issued

**Strategy Tips:**
- Settle batches daily — never let transactions sit for more than 24 hours
- Set up automated batch settlement at end of each business day
- If a delay is unavoidable (e.g., back-ordered item), note the original authorization date and re-authorize if needed

**Common Mistakes:**
- Holding transactions in an open batch for days or weeks
- Not settling after weekends or holidays, causing multi-day delays
- Forgetting to process transactions from backup or offline terminals
- Waiting to ship before settling — settle at authorization time, not shipment time (for most MCCs)

---

## 12.2 — Incorrect Transaction Code

**Category:** Processing Errors (Collaboration workflow)
**Time Limit:** Issuer must file within 120 days of the transaction date. Merchant has 30 days to respond.

**Description:**
The merchant processed a transaction with the wrong transaction code — for example, submitting a debit instead of a credit, or a credit instead of a debit. This can also occur when a refund is processed as a sale.

**Required Evidence:**
- Documentation proving the correct transaction code was used (matching authorization and clearing records)
- Transaction receipt showing the intended transaction type
- Authorization request and response showing the transaction type matches

**Compelling Evidence (improves win rate):**
- Side-by-side comparison of authorization record and settlement record showing matching transaction codes
- Processor confirmation that the transaction was submitted correctly
- Proof that a correcting transaction (reversal or credit) has been processed

**Strategy Tips:**
- Verify transaction type before submitting each batch — refunds should be credits, not debits
- Use your POS system's refund function rather than manually keying credits to avoid code errors
- Implement reconciliation checks that flag mismatched transaction types before batch settlement

**Common Mistakes:**
- Manually keying a refund as a sale transaction
- Processing a return as a new purchase instead of a credit
- Not reconciling transaction types before batch submission
- Using outdated POS software that maps transaction codes incorrectly

---

## 12.3 — Incorrect Currency

**Category:** Processing Errors (Collaboration workflow)
**Time Limit:** Issuer must file within 120 days of the transaction date. Merchant has 30 days to respond.

**Description:**
The transaction was processed in a currency different from what the cardholder agreed to, or Dynamic Currency Conversion (DCC) was applied without the cardholder's consent. The settled currency does not match the transaction currency indicated in the authorization.

**Required Evidence:**
- Proof the transaction was processed in the correct currency as agreed by the cardholder
- Authorization and settlement records showing matching currency codes
- If DCC was used: signed receipt or digital consent showing the cardholder chose DCC and was shown the exchange rate and markup

**Compelling Evidence (improves win rate):**
- DCC consent form or screen capture showing the cardholder was offered a choice and selected DCC
- Terminal configuration records showing correct currency settings
- Proof the displayed price matched the currency of the transaction

**Strategy Tips:**
- Always give the cardholder a clear choice between local and home currency for DCC transactions
- Display the exchange rate, markup percentage, and final amount in both currencies before the cardholder confirms
- Keep signed DCC consent receipts for at least 180 days

**Common Mistakes:**
- Auto-applying Dynamic Currency Conversion without explicit cardholder consent
- Not clearly displaying exchange rates and fees before DCC confirmation
- Configuring terminals with the wrong default currency
- Failing to retain DCC consent documentation

---

## 12.4 — Incorrect Account Number

**Category:** Processing Errors (Collaboration workflow)
**Time Limit:** Issuer must file within 120 days of the transaction date. Merchant has 30 days to respond.

**Description:**
The merchant posted a transaction to the wrong account number, or the account number in the clearing record does not match any account in the issuer's master file. This typically occurs with manually keyed transactions where the card number is entered incorrectly.

**Required Evidence:**
- Transaction receipt showing the correct account number was used
- Authorization record matching the clearing record account number
- Proof the card was electronically read (chip or swipe) rather than manually entered

**Compelling Evidence (improves win rate):**
- EMV chip data or magnetic stripe read confirmation proving the card number was captured electronically
- Authorization and clearing records showing matching account numbers throughout the transaction lifecycle
- Proof that a refund has already been issued to the correct account

**Strategy Tips:**
- Minimize manual key entry — always swipe, insert chip, or tap when the physical card is present
- For CNP transactions, use tokenization to reduce account number errors
- Implement account number validation checks before submitting transactions

**Common Mistakes:**
- Manually keying card numbers and transposing digits
- Not verifying the last four digits on the receipt match the physical card
- Using stored card numbers that may be outdated or incorrect
- Not implementing Luhn check validation on manually entered numbers

---

## 12.5 — Incorrect Amount

**Category:** Processing Errors (Collaboration workflow)
**Time Limit:** Issuer must file within 120 days of the transaction date. Merchant has 30 days to respond.

**Description:**
The cardholder claims the transaction amount is incorrect — the charged amount differs from what they agreed to pay. This can occur due to data entry errors, incorrect tip amounts, or unauthorized add-on charges.

**Required Evidence:**
- Signed receipt or order confirmation showing the cardholder agreed to the charged amount
- Itemized invoice or receipt matching the transaction amount
- Authorization record showing the approved amount matches the settled amount

**Compelling Evidence (improves win rate):**
- Signed receipt with the total amount clearly written by the cardholder (especially for tip-added amounts)
- Digital order confirmation email or screenshot sent to the cardholder showing the exact amount
- If the amount includes additional charges (shipping, tax, tips), provide itemized documentation

**Strategy Tips:**
- Always show the cardholder the final amount (including tax, shipping, and any surcharges) before they confirm
- For tip-adjusted transactions, retain the signed receipt with the cardholder's handwritten tip and total
- If you discover an amount error, proactively issue a partial refund before a dispute is filed

**Common Mistakes:**
- Adding charges after authorization without cardholder consent (e.g., restocking fees, convenience fees)
- Settling a different amount than what was authorized without re-authorizing
- Not retaining signed receipts showing tip amounts
- Rounding up transaction amounts without cardholder agreement

---

## 12.6 — Duplicate Processing / Paid by Other Means

**Category:** Processing Errors (Collaboration workflow)
**Time Limit:** Issuer must file within 120 days of the transaction date. Merchant has 30 days to respond.

**Description:**
The cardholder was charged more than once for the same transaction, or the cardholder paid for the same goods/services through another method (cash, check, different card) and was also charged on this card.

**Required Evidence:**
- Documentation proving each transaction represents a separate, legitimate purchase
- Unique transaction identifiers (different order numbers, dates, items) for each charge
- Proof that the cardholder did not pay by other means for the same purchase

**Compelling Evidence (improves win rate):**
- Itemized receipts for each transaction showing different products, services, or dates
- Order confirmation emails with distinct order numbers sent to the cardholder
- Payment records showing no other payment method was used for the same transaction
- Proof that a refund for the duplicate has already been issued

**Strategy Tips:**
- Implement duplicate transaction detection in your POS/payment system to flag same-card, same-amount charges within a short time window
- Only submit each batch once — track batch IDs to prevent resubmission
- When a customer switches payment methods, void the original card transaction immediately rather than waiting

**Common Mistakes:**
- Submitting the same batch multiple times due to timeout errors or system glitches
- Not voiding the first transaction when a customer decides to pay with a different method
- Processing both an online and in-store transaction for the same order
- Retrying a transaction that appeared to fail but actually went through

---

## 12.7 — Invalid Data

**Category:** Processing Errors (Collaboration workflow)
**Time Limit:** Issuer must file within 120 days of the transaction date. Merchant has 30 days to respond.

**Description:**
The merchant submitted a transaction with invalid or incorrect data fields, such as an incorrect transaction date, merchant category code (MCC), merchant or transaction type indicator, country or state code, or other required authorization fields.

**Required Evidence:**
- Correct transaction data records (date, MCC, country code, transaction type)
- Authorization and clearing records showing consistent, valid data
- Proof that the data error was caused by a processor or system issue, not the merchant

**Compelling Evidence (improves win rate):**
- Processor confirmation that the correct data was submitted by the merchant
- Terminal configuration records showing correct MCC and location data
- Side-by-side comparison of authorization and clearing records showing matching valid fields

**Strategy Tips:**
- Verify your MCC, country code, and business information are correct in your processor's system
- After onboarding or changing processors, confirm all data fields are accurately configured
- Periodically audit your transaction records for data consistency

**Common Mistakes:**
- Not updating business information after relocating or changing business type
- Using a test/sandbox MCC in production transactions
- Failing to correct known data errors reported by your processor
- Not validating required fields before batch submission

---

## 13.1 — Merchandise/Services Not Received

**Category:** Consumer Disputes (Collaboration workflow)
**Time Limit:** Issuer must file within 120 days of the expected delivery date or service date, not to exceed **540 days** from the transaction date. Merchant has 30 days to respond.

**Description:**
The cardholder claims they did not receive the purchased merchandise or services. This is one of the most common consumer dispute codes, especially for e-commerce transactions.

**Required Evidence:**
- **Signed proof of delivery is the strongest evidence** — carrier tracking with recipient signature confirmation
- Delivery tracking number and carrier confirmation showing delivery to the cardholder's address
- For services: proof the service was performed on the agreed date (signed service completion form, access logs, usage records)
- For digital goods: proof of delivery (download logs, access timestamps, email delivery confirmation)

**Compelling Evidence (improves win rate):**
- Signed delivery confirmation matching the cardholder's name and billing/shipping address
- GPS delivery confirmation from the carrier
- Photographs of the delivered package at the cardholder's address (provided by carrier)
- Post-delivery communication from the cardholder acknowledging receipt (emails, reviews, support tickets)
- Usage or access logs showing the cardholder used the product/service after delivery

**Strategy Tips:**
- Always use tracked shipping with signature confirmation for orders above your risk threshold (typically $100+)
- Ship to the AVS-verified billing address whenever possible; shipping to alternate addresses increases dispute risk
- For digital goods, log download timestamps, IP addresses, and usage data as proof of delivery
- Send shipping confirmation emails with tracking numbers — these serve as evidence the cardholder was notified

**Common Mistakes:**
- Shipping without tracking or signature confirmation
- Shipping to an address that does not match the billing address without additional verification
- Not retaining delivery confirmation records for at least 540 days (the maximum filing window)
- Charging the cardholder before shipping the merchandise

---

## 13.2 — Cancelled Recurring Transaction

**Category:** Consumer Disputes (Collaboration workflow)
**Time Limit:** Issuer must file within 120 days of the transaction date. Merchant has 30 days to respond.

**Description:**
The cardholder claims they were charged for a recurring transaction after they had already cancelled the subscription or recurring billing agreement. This also applies when the cardholder's account was closed but recurring charges continued.

**Required Evidence:**
- Signed recurring billing agreement or terms of service with cancellation policy
- Records showing no cancellation request was received prior to the disputed charge
- Communication logs showing the cardholder was informed of the cancellation policy
- **Cancellation request logs with timestamps** — proving when (or whether) the cardholder actually cancelled

**Compelling Evidence (improves win rate):**
- Detailed cancellation policy that was presented and agreed to at sign-up
- Timestamped logs showing the cardholder's account was active and no cancellation was submitted before the charge date
- Email or chat correspondence where the cardholder acknowledged the billing terms
- Proof the cardholder continued to use the service after the disputed charge date

**Strategy Tips:**
- Implement a clear, easily accessible cancellation mechanism and log every cancellation request with timestamps
- Send billing reminders before each recurring charge, especially before annual renewals
- Provide written cancellation confirmation to the cardholder immediately upon request
- Retain all cancellation-related communication for at least 18 months

**Common Mistakes:**
- Making cancellation unnecessarily difficult (hidden cancel buttons, requiring phone calls)
- Not processing cancellations promptly, resulting in one more charge after the request
- Failing to send advance billing notifications for recurring charges
- Not retaining timestamped cancellation request logs as evidence

---

## 13.3 — Not as Described or Defective Merchandise/Services

**Category:** Consumer Disputes (Collaboration workflow)
**Time Limit:** Issuer must file within 120 days of the date the cardholder first became aware of the issue, not to exceed **540 days** from the transaction date. Merchant has 30 days to respond.

**Description:**
The cardholder claims the received merchandise or services did not match the description, were defective, damaged, or were otherwise materially different from what was advertised or agreed upon.

**Required Evidence:**
- Original product listing, description, or service agreement showing what was promised
- Proof of what was actually delivered (photos, specifications, shipping records)
- Return/exchange policy that was presented to and agreed upon by the cardholder before purchase

**Compelling Evidence (improves win rate):**
- Detailed product descriptions, photos, and specifications from the listing at the time of purchase
- Third-party quality inspection reports or certifications proving the merchandise met specifications
- Correspondence with the cardholder showing they did not attempt to return or exchange the item
- Proof the cardholder agreed to accept a repair, replacement, or store credit
- Evidence the cardholder continued to use the merchandise after claiming it was defective

**Strategy Tips:**
- Maintain accurate and detailed product descriptions with high-quality photos; vague listings invite disputes
- Offer a clear return/exchange process and document that the cardholder was made aware of it
- Respond quickly to quality complaints — resolving issues before they become disputes has the highest win rate
- If the cardholder returns the merchandise, inspect and photograph it upon receipt to document its actual condition

**Common Mistakes:**
- Using stock photos that do not accurately represent the product
- Not having a documented return/exchange policy that was presented at purchase
- Ignoring cardholder complaints about product quality, pushing them to file a dispute
- Failing to document the condition of returned merchandise

---

## 13.4 — Counterfeit Merchandise

**Category:** Consumer Disputes (Collaboration workflow)
**Time Limit:** Issuer must file within 120 days of the date the cardholder identified the merchandise as counterfeit, not to exceed **540 days** from the transaction date. Merchant has 30 days to respond.

**Description:**
The cardholder claims the merchandise received is counterfeit — an unauthorized copy or imitation of a genuine product sold as authentic.

**Required Evidence:**
- Proof of authenticity: certificates of authenticity, authorized dealer/distributor documentation, brand authorization letters
- Supply chain documentation showing the product was sourced from legitimate channels
- Product listing clearly stating the item's brand and authenticity

**Compelling Evidence (improves win rate):**
- Letter from the brand owner or trademark holder confirming the merchandise is genuine
- Purchase invoices from authorized distributors or manufacturers
- Serial numbers or authentication codes that can be verified with the brand
- Third-party authentication or appraisal reports

**Strategy Tips:**
- Maintain authorization letters from brands you sell and keep them readily accessible
- Document your supply chain from manufacturer to customer for high-value or brand-name items
- Include certificates of authenticity with shipments of luxury or frequently counterfeited items
- If selling non-branded or generic items, clearly describe them as such to avoid counterfeit claims

**Common Mistakes:**
- Selling branded merchandise without proper authorization documentation
- Not maintaining provenance records for the supply chain
- Using brand names or logos in listings for generic or compatible products
- Failing to clearly distinguish between genuine, refurbished, and compatible items

---

## 13.5 — Misrepresentation

**Category:** Consumer Disputes (Collaboration workflow)
**Time Limit:** Issuer must file within 120 days of the date the cardholder became aware of the misrepresentation, not to exceed **540 days** from the transaction date. Merchant has 30 days to respond.

**Description:**
The cardholder claims the merchant misrepresented the product, service, or terms of the transaction. This includes misleading advertising, hidden fees, bait-and-switch tactics, or failure to disclose material terms. Common in industries like timeshares, debt consolidation, credit repair, and investment products.

**Required Evidence:**
- Complete and accurate product/service description as presented to the cardholder at time of purchase
- Terms and conditions the cardholder agreed to, with proof of acceptance (signature, click-through, checkbox)
- Marketing materials that were displayed to the cardholder
- Disclosure statements for all fees, terms, and conditions

**Compelling Evidence (improves win rate):**
- Screenshots or archived copies of the product listing/advertisement at the time of purchase
- Cardholder's signed or digitally accepted agreement showing all terms were disclosed
- Communication records showing the cardholder was informed of all material terms before purchase
- Third-party reviews or industry certifications validating your claims

**Strategy Tips:**
- Ensure all marketing materials accurately represent products/services with no exaggeration
- Disclose all fees, limitations, and terms prominently before purchase completion
- Archive product listings and advertisements with timestamps to prove what was shown at time of sale
- Use clear, plain language in terms and conditions; ambiguity will be interpreted against the merchant

**Common Mistakes:**
- Using exaggerated or misleading advertising claims
- Burying important terms in fine print
- Not archiving marketing materials and product listings over time
- Failing to disclose recurring charges, cancellation fees, or restocking fees upfront

---

## 13.6 — Credit Not Processed

**Category:** Consumer Disputes (Collaboration workflow)
**Time Limit:** Issuer must file within 120 days of the date the cardholder expected the credit. Merchant has 30 days to respond.

**Description:**
The cardholder claims they are owed a refund or credit that has not been processed. This occurs when the cardholder returned merchandise, cancelled a service, or was promised a credit, but the merchant has not issued the refund.

**Required Evidence:**
- Proof that the refund/credit has already been processed (credit transaction receipt, ARN, processing date)
- If no refund is owed: return policy showing the cardholder is not eligible for a refund, with proof the policy was presented before purchase
- Documentation showing the cardholder did not return the merchandise or meet refund conditions

**Compelling Evidence (improves win rate):**
- Credit card statement or processor record showing the refund was posted to the cardholder's account
- Acquirer Reference Number (ARN) for the refund transaction
- Communication with the cardholder showing they agreed no refund was owed
- Return policy with proof the cardholder acknowledged it at the time of purchase

**Strategy Tips:**
- Process refunds within 5-7 business days of receiving returned merchandise — delays cause disputes
- Send refund confirmation to the cardholder with the expected processing time
- If a refund is not warranted, communicate the reason clearly and document the conversation
- Keep your return policy visible at checkout and on receipts

**Common Mistakes:**
- Delaying refund processing for weeks after receiving the return
- Not sending refund confirmation to the cardholder
- Having unclear or inaccessible return and refund policies
- Promising a refund verbally but not following through in a timely manner

---

## 13.7 — Cancelled Merchandise/Services

**Category:** Consumer Disputes (Collaboration workflow)
**Time Limit:** Issuer must file within 120 days of the cancellation date or expected delivery date. Merchant has 30 days to respond.

**Description:**
The cardholder claims they cancelled an order for merchandise or services, or returned merchandise, but the merchant has not yet issued the corresponding credit or refund.

**Required Evidence:**
- Return/cancellation policy that was presented to and accepted by the cardholder before purchase
- Proof that the cardholder did not cancel within the allowed cancellation period
- Proof that the merchandise was not returned, or that it was returned outside the return window
- If a refund was issued, provide credit transaction documentation

**Compelling Evidence (improves win rate):**
- Timestamped cancellation policy acceptance by the cardholder
- Shipping records proving the merchandise was delivered and not returned
- Communication showing the cardholder acknowledged the return/cancellation policy
- Documentation that the cardholder continued to use the service after the alleged cancellation

**Strategy Tips:**
- Have a clear, written cancellation/return policy and ensure it is accepted before purchase
- Log all cancellation requests with timestamps and send confirmation to the cardholder
- If cancellation is received after the allowed window, communicate this clearly in writing
- Process legitimate cancellation refunds promptly to avoid disputes

**Common Mistakes:**
- Not documenting that the cancellation policy was presented and accepted
- Failing to process cancellation refunds promptly
- Not logging the date and time of cancellation requests
- Having inconsistent cancellation policies across different sales channels

---

## 13.8 — Original Credit Transaction Not Accepted

**Category:** Consumer Disputes (Collaboration workflow)
**Time Limit:** Issuer must file within 120 days of the transaction date. Merchant has 30 days to respond.

**Description:**
The cardholder did not accept or does not recognize an Original Credit Transaction (OCT) posted to their account. OCTs are used to push funds to a cardholder's account without a corresponding purchase transaction. This also occurs when the issuer does not permit OCTs on the card type due to local regulations.

**Required Evidence:**
- Documentation showing the cardholder requested or agreed to receive the OCT
- Proof of the original transaction or relationship that warranted the credit
- Communication records with the cardholder regarding the credit

**Compelling Evidence (improves win rate):**
- Signed agreement or correspondence from the cardholder requesting the funds transfer
- Proof the OCT was a legitimate refund tied to a prior purchase transaction
- Documentation showing the reversal of the OCT has already been processed

**Strategy Tips:**
- Always tie OCTs to a verifiable prior transaction or documented agreement
- Communicate with the cardholder before sending an OCT so they expect and recognize it
- Use standard refund processing (linked to the original transaction) instead of OCTs whenever possible

**Common Mistakes:**
- Sending OCTs without prior communication or agreement with the cardholder
- Using OCTs instead of standard refund transactions linked to the original purchase
- Not verifying that the issuer and card type accept OCTs before sending
- Failing to document the reason and authorization for each OCT

---

## 13.9 — Non-Receipt of Cash or Load Transaction Value

**Category:** Consumer Disputes (Collaboration workflow)
**Time Limit:** Issuer must file within 120 days of the transaction date. Merchant has 30 days to respond.

**Description:**
The cardholder claims they did not receive cash from an ATM withdrawal, or that the value of a prepaid card load transaction was not applied to their account. This code is primarily used by ATM operators and prepaid card load merchants.

**Required Evidence:**
- ATM transaction logs showing the cash was dispensed successfully
- ATM journal tape or electronic journal records for the transaction
- For prepaid loads: system records showing the value was successfully applied to the cardholder's account

**Compelling Evidence (improves win rate):**
- ATM surveillance video showing the cardholder receiving cash
- ATM cash reconciliation records showing no discrepancy for the transaction period
- Hardware diagnostic logs confirming the ATM dispensing mechanism was functioning correctly
- Prepaid platform records confirming the load was completed and the balance updated

**Strategy Tips:**
- Maintain ATM surveillance footage for at least 180 days and ensure cameras clearly capture the dispensing area
- Perform daily ATM cash reconciliation and document any discrepancies immediately
- For prepaid loads, keep real-time transaction logs and balance records
- Respond promptly with ATM journal records — delays can result in automatic loss

**Common Mistakes:**
- Not retaining ATM surveillance footage long enough to cover the dispute window
- Failing to perform regular ATM cash reconciliation
- Not maintaining detailed ATM hardware maintenance and diagnostic logs
- Delaying response because ATM journal retrieval is slow — start the process immediately upon receiving the dispute

---

## Quick Reference

| Category | Codes | Workflow |
|----------|-------|----------|
| Fraud (10.x) | 10.1–10.5 | Allocation |
| Authorization (11.x) | 11.1–11.3 | Allocation |
| Processing Errors (12.x) | 12.1–12.7 | Collaboration |
| Consumer Disputes (13.x) | 13.1–13.9 | Collaboration |

**Universal merchant response window: 30 days** (acquirers may impose shorter internal deadlines of 20-25 days).
