# Discover Chargeback Reason Codes

> Last updated: 2026-02. Discover organizes disputes into four categories:
> Fraud (UA codes), Processing Errors (IN, DA, DP, IC, IA, LP, AW, CD), Consumer Disputes (AA, AP, RG, RM, RN, AT),
> and Retrieve and Resolve (NF, NC). Discover codes use 2-letter abbreviations, some with numeric suffixes
> (e.g., UA01, UA02). Discover's dispute system uses a retrieval-then-chargeback process.
> Merchant response window: **30 days** for all codes.

---

## UA01 — Fraud — Card Present Transaction

**Category:** Fraud
**Time Limit:** Issuer must file within 120 days of the transaction date. Merchant has 30 days to respond.

**Description:**
The cardholder claims someone used their physical Discover card for an unauthorized in-store transaction. The card was present at the time of the transaction, but the cardholder denies authorizing or participating in the purchase.

**Required Evidence:**
- Card imprint or EMV chip transaction data proving the card was physically present and read
- Signed transaction receipt
- Proof the cardholder's identity was verified at the time of the transaction (photo ID check, PIN entry)
- Authorization approval code and response records

**Compelling Evidence (improves win rate):**
- Surveillance footage showing the cardholder at the point of sale
- EMV cryptogram data proving the chip was read and the transaction was authenticated
- AVS and CVV match records
- Prior undisputed transactions from the same card at the same location

**Strategy Tips:**
- Always process chip cards via the chip reader; do not allow fallback to magnetic stripe swipe
- Verify cardholder identity on high-value transactions by requesting government-issued photo ID
- Retain signed receipts and surveillance footage for at least 180 days

**Common Mistakes:**
- Processing chip cards by swipe or manual key entry when the chip reader is available
- Not retaining signed transaction receipts for the full dispute window
- Failing to train staff to verify cardholder identity on suspicious or high-value transactions

---

## UA02 — Fraud — Card Not Present Transaction

**Category:** Fraud
**Time Limit:** Issuer must file within 120 days of the transaction date. Merchant has 30 days to respond.

**Description:**
The cardholder claims they did not authorize or participate in a card-not-present transaction (online, phone, or mail order). This is the most common fraud dispute code for Discover e-commerce transactions.

**Required Evidence:**
- AVS (Address Verification Service) match confirmation
- CVV/CID match confirmation
- Proof of delivery to the cardholder's verified billing address
- Order details, IP address, and shipping information

**Compelling Evidence (improves win rate):**
- IP address, device fingerprint, and geolocation data from the transaction
- 3D Secure (ProtectBuy) authentication results
- Prior undisputed transactions from the same device, email, or IP address
- For digital goods: cardholder's email address, IP address, download timestamp, and electronic delivery logs
- Proof the cardholder registered for or confirmed electronic delivery of goods or services
- Communication logs (emails, chats) between the merchant and cardholder regarding the order

**Strategy Tips:**
- Use 3D Secure (Discover ProtectBuy) for online transactions to shift liability to the issuer
- Implement AVS, CVV, device fingerprinting, and velocity checks on all CNP transactions
- Ship only to AVS-verified billing addresses for high-risk orders
- For digital goods, log IP address, device data, and usage activity as proof of delivery

**Common Mistakes:**
- Not collecting or retaining IP address and device fingerprint data
- Shipping to an address that does not match the billing address without additional verification
- Failing to implement 3D Secure when it would shift liability to the issuer
- Not requiring CVV for all card-not-present transactions

---

## UA05 — Fraud — Chip Card Counterfeit Transaction

**Category:** Fraud
**Time Limit:** Issuer must file within 120 days of the transaction date. Merchant has 30 days to respond.

**Description:**
A counterfeit chip card was used at a terminal that did not process the transaction via the chip. Under the EMV liability shift, the merchant bears liability for counterfeit fraud when their terminal falls back to magnetic stripe instead of reading the chip. This code applies when a chip card was processed by swipe at a non-EMV-compliant terminal.

**Required Evidence:**
- Proof the transaction was processed via EMV chip read (not magnetic stripe fallback)
- TC (Transaction Certificate) or cryptogram proving the chip was read
- Terminal EMV certification documentation from the acquirer or processor

**Compelling Evidence (improves win rate):**
- Full EMV transaction data including application cryptogram and AID (Application Identifier)
- Terminal configuration and certification logs showing EMV compliance at the time of the transaction
- Evidence the card's chip was malfunctioning if the terminal attempted chip read but fell back to swipe

**Strategy Tips:**
- Ensure all terminals are EMV-certified and maintain current certification records
- Never allow chip card fallback to magnetic stripe if the chip is functional
- If the chip read fails, request an alternative payment method rather than falling back to swipe

**Common Mistakes:**
- Operating terminals that are not EMV-certified
- Allowing fallback swipe transactions without attempting chip insertion first
- Not maintaining EMV certification records on file for each terminal

---

## UA06 — Fraud — Chip and PIN Transaction

**Category:** Fraud
**Time Limit:** Issuer must file within 120 days of the transaction date. Merchant has 30 days to respond.

**Description:**
The cardholder denies involvement in a transaction that was processed using a hybrid card at a stripe-only terminal or at a chip-capable terminal that lacks a PIN pad. Liability shifts to the merchant when PIN verification was required but the terminal did not support it.

**Required Evidence:**
- Proof the transaction used chip and PIN verification
- Terminal logs showing PIN was entered and verified
- CVM (Cardholder Verification Method) results showing PIN was used

**Compelling Evidence (improves win rate):**
- Full EMV transaction data including the application cryptogram
- Terminal certification documentation showing PIN pad capability and compliance
- Video surveillance showing the cardholder entering their PIN at the terminal

**Strategy Tips:**
- Ensure all terminals support both chip and PIN (not just chip and signature)
- Do not process hybrid cards via magnetic stripe when a chip reader is available
- Maintain up-to-date PIN pad certification; expired certifications leave you exposed

**Common Mistakes:**
- Using terminals without PIN pad capability for chip-and-PIN cards
- Processing chip cards without requiring PIN when the card preference is PIN
- Not upgrading PIN pad firmware when certification expires

---

## UA10 — Request for Copy Bearing Signature

**Category:** Fraud
**Time Limit:** Issuer must file within 120 days of the transaction date. Merchant has 30 days to respond.

**Description:**
This is a retrieval request where the card issuer requests supplementary documentation for a specific card-present transaction the cardholder claims was unauthorized. If the documents the merchant provides bear evidence suggesting fraud or improper authorization (missing signature, illegible imprint, or no authorization), the issuer escalates to a chargeback.

**Required Evidence:**
- Transaction receipt with a full and legible imprint of all required card security features
- Receipt showing a valid and legible signature from the cardholder or authorized card user
- Proof of valid authorization approval for the transaction

**Compelling Evidence (improves win rate):**
- Clear, high-quality copies of the signed transaction receipt
- EMV chip data or card swipe data proving the card was physically present
- Surveillance footage of the cardholder signing or completing the transaction
- ID verification records matching the cardholder name

**Strategy Tips:**
- Respond promptly to all retrieval requests with accurate, legible, and complete documentation
- Maintain high-quality digital copies of every transaction receipt; paper receipts fade over time
- Always obtain signatures for card-present transactions and verify them against the card

**Common Mistakes:**
- Ignoring or responding late to retrieval requests, which automatically triggers a chargeback
- Providing illegible or incomplete copies of transaction receipts
- Not maintaining digital backups of signed receipts
- Failing to obtain a signature at the point of sale

---

## UA11 — Cardholder Claims Fraud (No Signature)

**Category:** Fraud
**Time Limit:** Issuer must file within 120 days of the transaction date. Merchant has 30 days to respond.

**Description:**
The cardholder claims fraudulent activity on a card-present, swiped transaction where no signature was obtained. Without a signature, the merchant has limited proof that the legitimate cardholder was present and authorized the transaction.

**Required Evidence:**
- Signed transaction receipt (if one exists)
- Card swipe or chip data proving the card was physically present
- Proof of cardholder identity verification

**Compelling Evidence (improves win rate):**
- Surveillance footage showing the cardholder at the point of sale
- AVS match records associated with the card
- Prior undisputed transactions from the same card at the same location
- PIN entry records if PIN was used as the CVM

**Strategy Tips:**
- Always obtain signatures for swiped transactions; unsigned receipts are nearly impossible to defend
- Transition to chip-based (EMV) processing to reduce liability for card-present fraud
- Retain surveillance footage for at least 180 days to cover the dispute window

**Common Mistakes:**
- Not collecting signatures on swiped transactions
- Relying solely on magnetic stripe swipe data without additional cardholder verification
- Discarding surveillance footage before the chargeback window closes

---

## IN — Invalid Card Number

**Category:** Processing Errors
**Time Limit:** Issuer must file within 120 days of the transaction date. Merchant has 30 days to respond.

**Description:**
The card number used for the transaction was not assigned to a valid Discover account, or the account number in the clearing record does not match any account in the issuer's records. This typically occurs with manually keyed transactions where the card number is entered incorrectly.

**Required Evidence:**
- Proof the correct card number was used (transaction receipt, POS logs)
- Authorization approval record with matching card number
- Proof the card was electronically read (chip or swipe) rather than manually entered

**Compelling Evidence (improves win rate):**
- EMV chip data or magnetic stripe read confirmation proving the card number was captured electronically
- Authorization and clearing records showing matching account numbers throughout the transaction lifecycle
- Proof that a refund has already been issued to the correct account

**Strategy Tips:**
- Minimize manual key entry; always swipe, insert chip, or tap when the physical card is present
- For CNP transactions, use tokenization to reduce account number errors
- Implement Luhn check validation on manually entered card numbers before submitting

**Common Mistakes:**
- Manually keying card numbers and transposing digits
- Not verifying the last four digits on the receipt match the physical card
- Using stored card numbers that may be outdated or incorrect

---

## DA — Declined Authorization

**Category:** Processing Errors
**Time Limit:** Issuer must file within 120 days of the transaction date. Merchant has 30 days to respond.

**Description:**
The merchant processed a transaction after the authorization request received a "decline" response from the issuer. This is one of the most clear-cut chargebacks and is very difficult to defend unless the merchant obtained a subsequent valid approval.

**Required Evidence:**
- Proof of a valid authorization approval (if the decline claim is incorrect)
- Full authorization response log from the gateway showing the approval response code
- Transaction logs showing the timeline of authorization attempts

**Compelling Evidence (improves win rate):**
- Complete authorization log showing the initial request and a successful approval response (not a decline)
- Proof that a subsequent authorization request was submitted and approved after any initial decline
- Documentation from the processor confirming the final authorization was valid

**Strategy Tips:**
- Never force a transaction through after receiving a decline response
- Train staff to request an alternative payment method when a card is declined
- If the customer wants to retry, have them use a different card or contact their bank first

**Common Mistakes:**
- Force-posting transactions after receiving a decline response
- Re-attempting authorization multiple times and processing on a partial approval
- Splitting a declined transaction into smaller amounts to get approvals

---

## DP — Duplicate Processing

**Category:** Processing Errors
**Time Limit:** Issuer must file within 120 days of the transaction date. Merchant has 30 days to respond.

**Description:**
The cardholder was charged more than once for the same transaction, or the same transaction was submitted multiple times in the settlement batch.

**Required Evidence:**
- Proof each charge represents a separate, legitimate purchase
- Unique transaction identifiers (different order numbers, dates, items) for each charge
- If a duplicate did occur, proof that a credit has already been issued for the duplicate

**Compelling Evidence (improves win rate):**
- Itemized receipts for each transaction showing different products, services, or dates
- Distinct order confirmation emails with unique order numbers sent to the cardholder
- Separate delivery tracking numbers or delivery confirmations for each charge
- Payment records showing no other payment method was used for the same transaction

**Strategy Tips:**
- Implement duplicate transaction detection in your POS or payment system to flag same-card, same-amount charges within a short time window
- Only submit each settlement batch once; track batch IDs to prevent resubmission
- Review batch reports for duplicate entries before settlement

**Common Mistakes:**
- Re-running a transaction when the terminal times out without verifying the first attempt went through
- Submitting the same batch multiple times due to timeout errors or system glitches
- Not providing separate invoices or order numbers for legitimately separate transactions

---

## IC — Incorrect Currency

**Category:** Processing Errors
**Time Limit:** Issuer must file within 120 days of the transaction date. Merchant has 30 days to respond.

**Description:**
The transaction was processed in a currency different from what the cardholder agreed to, or Dynamic Currency Conversion (DCC) was applied without the cardholder's consent. The settled currency does not match what was presented to the cardholder at the time of sale.

**Required Evidence:**
- Proof the transaction was processed in the correct currency as agreed by the cardholder
- Authorization and settlement records showing matching currency codes
- If DCC was used: signed receipt or digital consent showing the cardholder chose DCC and was shown the exchange rate and markup

**Compelling Evidence (improves win rate):**
- DCC consent form or screen capture showing the cardholder was offered a choice and selected DCC
- Terminal configuration records showing correct currency settings
- Proof the displayed price matched the currency of the transaction
- Screenshots of checkout pages showing the currency displayed to the cardholder

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

## IA — Incorrect Transaction Amount

**Category:** Processing Errors
**Time Limit:** Issuer must file within 120 days of the transaction date. Merchant has 30 days to respond.

**Description:**
The cardholder claims the transaction amount is incorrect -- the charged amount differs from what they agreed to pay. The transaction amount submitted for authorization does not match the final amount settled. This includes data entry errors, incorrect tip amounts, or unauthorized add-on charges.

**Required Evidence:**
- Signed receipt or order confirmation showing the cardholder agreed to the charged amount
- Itemized invoice or receipt matching the transaction amount
- Authorization record showing the approved amount matches the settled amount

**Compelling Evidence (improves win rate):**
- Signed receipt with the total amount clearly written by the cardholder (especially for tip-adjusted amounts)
- Digital order confirmation email or screenshot sent to the cardholder showing the exact amount
- If the amount includes additional charges (shipping, tax, tips), provide itemized documentation
- Authorization log matching the settled amount

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

## LP — Late Presentment

**Category:** Processing Errors
**Time Limit:** Issuer must file within 120 days of the transaction date. Merchant has 30 days to respond.

**Description:**
The merchant did not submit the transaction for processing within the required timeframe. The transaction was presented for settlement too late, and the cardholder's account may no longer be in good standing.

**Required Evidence:**
- Proof the transaction was submitted within the applicable deadline
- Valid authorization approval obtained within the applicable number of calendar days prior to the ship date, expected delivery date, or processing date
- Transaction receipt or processing records showing the original transaction date and presentment date

**Compelling Evidence (improves win rate):**
- Batch settlement timestamps from your processor
- Proof of delayed delivery that justified the timing (e.g., back-ordered item, custom manufacturing)
- Evidence of technical issues (system outages, processor delays) that caused the late submission
- Proof that a refund has already been issued

**Strategy Tips:**
- Submit transactions for settlement on the same day as the sale; never let transactions sit for more than 24 hours
- Set up automated batch settlement at end of each business day
- Do not charge until goods have shipped; if a delay is unavoidable, re-authorize before settling

**Common Mistakes:**
- Holding transactions in an open batch for days or weeks
- Not settling after weekends or holidays, causing multi-day delays
- Charging before fulfillment and then delaying shipment
- Forgetting to process transactions from backup or offline terminals

---

## AW — Altered Amount

**Category:** Processing Errors
**Time Limit:** Issuer must file within 120 days of the transaction date. Merchant has 30 days to respond.

**Description:**
The cardholder claims the authorized transaction amount does not match the actual processed amount, or that the transaction documentation was altered after the cardholder signed. The amount on the receipt was changed after the fact.

**Required Evidence:**
- Proof the transaction documentation was not altered in any way
- Proof the cardholder agreed to the amount printed on the receipt for the transaction, cash advance, or ATM withdrawal
- Signed receipt matching the processed amount
- Proof the cardholder is responsible for the amount charged to the card

**Compelling Evidence (improves win rate):**
- Original and unaltered receipt or invoice with matching authorization records
- Authorization log showing the approved amount matches the settled amount exactly
- If the cardholder requested cash back, proof that the cardholder received the requested cash

**Strategy Tips:**
- Ensure the authorization amount matches the settlement amount exactly
- Disclose all additional charges (tips, surcharges, service fees) before processing
- Never modify a receipt after the cardholder has signed it

**Common Mistakes:**
- Settling for a different amount than what was authorized without re-authorizing
- Modifying receipts after the cardholder has completed the transaction
- Not getting explicit cardholder acknowledgment for additional charges like tips or surcharges

---

## CD — Credit/Debit Posted Incorrectly

**Category:** Processing Errors
**Time Limit:** Issuer must file within 120 days of the transaction date. Merchant has 30 days to respond.

**Description:**
A credit was posted as a charge, or a charge was posted as a credit. The transaction type was reversed from what the cardholder expected. The merchant may have processed a refund as a sale, or processed a sale when it should have been a refund.

**Required Evidence:**
- Proof the transaction was posted correctly (matching the intended transaction type)
- Proof the cardholder agreed to the debit or credit as posted
- Transaction receipt showing the correct transaction type

**Compelling Evidence (improves win rate):**
- POS logs and settlement reports showing the correct transaction type was submitted
- Signed receipt confirming the transaction type
- Proof that a correcting transaction (reversal or credit) has already been processed
- Proof the chargeback does not adhere to Discover's requirements

**Strategy Tips:**
- Double-check transaction types (sale vs. refund) before submitting each batch
- Use your POS system's dedicated refund function rather than manually keying credits to avoid code errors
- Reconcile daily batch reports to catch mismatched transaction types before settlement

**Common Mistakes:**
- Confusing sale and refund functions on the terminal
- Manually keying a refund as a sale transaction
- Not catching errors in the daily batch reconciliation
- Processing a return as a new purchase instead of a credit

---

## AA — Cardholder Does Not Recognize

**Category:** Consumer Disputes
**Time Limit:** Issuer must file within 120 days of the transaction date (extendable by 30 days if a retrieval request was filed first). Merchant has 30 days to respond.

**Description:**
The cardholder does not recognize the charge on their statement. This may be caused by an unclear billing descriptor, friendly fraud, or genuine unauthorized use. The cardholder is not necessarily claiming fraud; they simply do not know what the charge is for.

**Required Evidence:**
- Proof the cardholder received the goods or services paid for with the disputed transaction
- Proof the cardholder's identity was verified at the time of the transaction and that authorization approval was received
- Copies of the card imprint and/or signature or PIN entry records
- If a refund has already been provided, proof that the cardholder's account was credited

**Compelling Evidence (improves win rate):**
- Delivery confirmation to the cardholder's address
- Prior undisputed transactions from the same cardholder at your business
- Communication records with the cardholder about the transaction (order confirmations, shipping notifications)
- Usage or access logs showing the cardholder used the product or service after delivery
- Proof a refund was already issued (if applicable)

**Strategy Tips:**
- Use a clear, recognizable billing descriptor that matches your business name as known by customers
- Send order confirmation and shipping notification emails for every transaction
- Implement fraud screening tools to catch suspicious orders before fulfillment

**Common Mistakes:**
- Using an obscure, generic, or abbreviated billing descriptor the cardholder cannot recognize
- Not sending transaction confirmation emails or receipts
- Failing to respond with complete documentation within the 30-day window

---

## AP — Recurring Payments

**Category:** Consumer Disputes
**Time Limit:** Issuer must file within 120 days of the transaction date. Merchant has 30 days to respond.

**Description:**
The cardholder claims they were charged for a recurring transaction after they had already canceled the subscription or recurring billing agreement. This also applies when the cardholder was not properly informed of recurring charges or the billing terms changed without notice.

**Required Evidence:**
- Signed or digitally accepted recurring billing agreement with the cardholder
- Records showing no cancellation request was received prior to the disputed charge
- Communication logs showing the cardholder was informed of the recurring billing terms and cancellation policy
- Cancellation request logs with timestamps (proving when or whether the cardholder actually canceled)

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

## RG — Non-Receipt of Goods or Services

**Category:** Consumer Disputes
**Time Limit:** Issuer must file within 120 days of the expected delivery date or service date. Merchant has 30 days to respond.

**Description:**
The cardholder claims they did not receive the purchased merchandise or services, even though the transaction was paid for. This is one of the most common consumer dispute codes for both e-commerce and service-based transactions.

**Required Evidence:**
- Signed proof of delivery is the strongest evidence -- carrier tracking with recipient signature confirmation
- Delivery tracking number and carrier confirmation showing delivery to the cardholder's address
- For services: proof the service was performed on the agreed date (signed service completion form, work orders, access logs, usage records)
- For digital goods: proof of delivery (download logs, access timestamps, email delivery confirmation)

**Compelling Evidence (improves win rate):**
- Signed delivery confirmation matching the cardholder's name and billing/shipping address
- GPS delivery confirmation from the carrier
- Photographs of the delivered package at the cardholder's address (provided by carrier)
- Post-delivery communication from the cardholder acknowledging receipt (emails, reviews, support tickets)
- Usage or access logs showing the cardholder used the product or service after delivery

**Strategy Tips:**
- Always use tracked shipping with signature confirmation for orders above your risk threshold (typically $100+)
- Ship to the AVS-verified billing address whenever possible; shipping to alternate addresses increases dispute risk
- For digital goods, log download timestamps, IP addresses, and usage data as proof of delivery
- Send shipping confirmation emails with tracking numbers as evidence the cardholder was notified

**Common Mistakes:**
- Shipping without tracking or signature confirmation
- Shipping to an address that does not match the billing address without additional verification
- Charging the cardholder before shipping the merchandise
- Not retaining delivery confirmation records for the full dispute window

---

## RM — Quality Discrepancy

**Category:** Consumer Disputes
**Time Limit:** Issuer must file within 120 days of the date the cardholder first became aware of the issue. Merchant has 30 days to respond.

**Description:**
The cardholder claims the received merchandise or services did not match the description, were defective, damaged, or were otherwise materially different from what was advertised or agreed upon. The quality of goods or services was significantly below what was represented.

**Required Evidence:**
- Original product listing, description, or service agreement showing what was promised
- Proof of what was actually delivered (photos, specifications, shipping records)
- Return/exchange policy that was presented to and agreed upon by the cardholder before purchase

**Compelling Evidence (improves win rate):**
- Proof the cardholder approved the quality of goods or services at delivery or completion
- Signed work order proving a correction or repair was completed to satisfaction
- Evidence the cardholder never attempted to return, cancel, or reject the goods
- Correspondence with the cardholder where the complaint was resolved
- Evidence the cardholder continued to use the merchandise after claiming it was defective

**Strategy Tips:**
- Maintain accurate and detailed product descriptions with high-quality photos; vague listings invite disputes
- Offer a clear return/exchange process and document that the cardholder was made aware of it
- Respond quickly to quality complaints; resolving issues before they become disputes has the highest win rate
- If the cardholder returns the merchandise, inspect and photograph it upon receipt to document its actual condition

**Common Mistakes:**
- Using stock photos that do not accurately represent the product
- Not having a documented return/exchange policy that was presented at purchase
- Ignoring cardholder complaints about product quality, pushing them to file a dispute
- Using exaggerated product descriptions or advertising claims

---

## RN — Credit Not Received

**Category:** Consumer Disputes
**Time Limit:** Issuer must file within 120 days of the date the cardholder expected the credit. Merchant has 30 days to respond.

**Description:**
The cardholder returned merchandise or refused delivery and claims a refund or credit has not been issued. The cardholder believes they are owed money but the merchant has not processed the refund.

**Required Evidence:**
- Proof that the refund/credit has already been processed (credit transaction receipt, ARN, processing date)
- If no refund is owed: return policy showing the cardholder is not eligible for a refund, with proof the policy was presented before purchase
- Documentation showing the cardholder did not return the merchandise or meet refund conditions

**Compelling Evidence (improves win rate):**
- Credit card statement or processor record showing the refund was posted to the cardholder's account
- Acquirer Reference Number (ARN) for the refund transaction
- Communication with the cardholder showing they agreed no refund was owed
- Return policy with proof the cardholder acknowledged it at the time of purchase
- Proof the merchandise was never returned to the merchant

**Strategy Tips:**
- Process refunds within 5-7 business days of receiving returned merchandise; delays cause disputes
- Send refund confirmation to the cardholder with the expected processing time
- If a refund is not warranted, communicate the reason clearly and document the conversation
- Keep your return policy visible at checkout and on receipts

**Common Mistakes:**
- Delaying refund processing for weeks after receiving the return
- Not sending refund confirmation to the cardholder
- Having unclear or inaccessible return and refund policies
- Issuing refunds via a different method (check, store credit) without documenting it to the card network

---

## AT — Authorization Noncompliance

**Category:** Consumer Disputes
**Time Limit:** Issuer must file within 120 days of the transaction date. Merchant has 30 days to respond.

**Description:**
The merchant was required to request authorization but failed to do so, or did not follow proper authorization procedures as required by Discover's rules. This differs from DA (Declined Authorization) in that no authorization was attempted or the process was not followed correctly.

**Required Evidence:**
- Proof of valid authorization (approval code, date, time, response code)
- Gateway or terminal logs showing the authorization request and response
- Transaction records demonstrating proper authorization procedures were followed

**Compelling Evidence (improves win rate):**
- Detailed authorization log with request and response codes showing proper approval
- Processor records confirming the authorization was valid and matched the cleared amount
- Documentation from the processor that all authorization procedures were followed correctly

**Strategy Tips:**
- Always obtain authorization before processing any transaction, regardless of amount
- Retain all authorization records including approval codes, timestamps, and response codes
- Ensure your POS system is configured to require real-time authorization on every transaction

**Common Mistakes:**
- Processing transactions without obtaining authorization
- Not retaining authorization approval codes and response logs
- Using offline authorization or floor limits inappropriately
- Relying on voice authorization without properly recording the approval code

---

## NF — Non-Receipt of Cash at ATM

**Category:** Retrieve and Resolve
**Time Limit:** Issuer must file within 120 days of the transaction date. Merchant has 30 days to respond.

**Description:**
The cardholder claims they did not receive cash from an ATM withdrawal, even though their account was debited for the amount. This code is primarily used by ATM operators.

**Required Evidence:**
- ATM transaction logs showing the cash was dispensed successfully
- ATM journal tape or electronic journal records for the specific transaction
- ATM balancing records showing no cash discrepancy for the transaction period

**Compelling Evidence (improves win rate):**
- ATM surveillance video showing the cardholder receiving cash
- ATM cash reconciliation records showing no excess cash at the end of the period
- Hardware diagnostic logs confirming the ATM dispensing mechanism was functioning correctly at the time
- Electronic journal with timestamps matching the disputed transaction

**Strategy Tips:**
- Maintain ATM surveillance footage for at least 180 days and ensure cameras clearly capture the dispensing area
- Perform daily ATM cash reconciliation and document any discrepancies immediately
- Respond promptly with ATM journal records; delays can result in automatic loss
- Keep detailed ATM hardware maintenance and diagnostic logs

**Common Mistakes:**
- Not retaining ATM surveillance footage long enough to cover the dispute window
- Failing to perform regular ATM cash reconciliation
- Not maintaining detailed ATM hardware maintenance and diagnostic logs
- Delaying response because ATM journal retrieval is slow; start the process immediately upon receiving the dispute

---

## NC — Not Classified

**Category:** Retrieve and Resolve
**Time Limit:** Issuer must file within 120 days of the transaction date. Merchant has 30 days to respond.

**Description:**
This is a catch-all reason code used when the dispute does not fit neatly into any other Discover reason code category. It may be used for unusual or complex dispute scenarios. Note: Discover has retired this code in some documentation revisions, but it may still appear on historical or processor-specific disputes.

**Required Evidence:**
- All available transaction documentation (receipts, invoices, contracts, authorization records)
- Proof of delivery or service completion
- Any communication records with the cardholder
- Proof of valid authorization

**Compelling Evidence (improves win rate):**
- Comprehensive documentation package addressing all aspects of the transaction
- Signed receipts, delivery confirmations, and authorization records
- Evidence that the cardholder received value for the transaction
- Proof a refund was already issued (if applicable)

**Strategy Tips:**
- Because this is a catch-all code, read the chargeback notification carefully to understand the specific claim being made
- Provide as much documentation as possible since the dispute reason is not clearly categorized
- Contact your acquirer or processor for guidance on the specific dispute details
- Treat this code with the same rigor as any other dispute; provide complete documentation

**Common Mistakes:**
- Providing a generic or incomplete response because the reason code is vague
- Not reading the chargeback notification carefully to understand the actual claim
- Failing to contact the acquirer for clarification on what evidence is needed
- Assuming the code is unimportant because it says "not classified"

---

## Quick Reference

| Code | Title | Category | Response Window |
|------|-------|----------|-----------------|
| UA01 | Fraud -- Card Present Transaction | Fraud | 30 days |
| UA02 | Fraud -- Card Not Present Transaction | Fraud | 30 days |
| UA05 | Fraud -- Chip Card Counterfeit Transaction | Fraud | 30 days |
| UA06 | Fraud -- Chip and PIN Transaction | Fraud | 30 days |
| UA10 | Request for Copy Bearing Signature | Fraud | 30 days |
| UA11 | Cardholder Claims Fraud (No Signature) | Fraud | 30 days |
| IN | Invalid Card Number | Processing Errors | 30 days |
| DA | Declined Authorization | Processing Errors | 30 days |
| DP | Duplicate Processing | Processing Errors | 30 days |
| IC | Incorrect Currency | Processing Errors | 30 days |
| IA | Incorrect Transaction Amount | Processing Errors | 30 days |
| LP | Late Presentment | Processing Errors | 30 days |
| AW | Altered Amount | Processing Errors | 30 days |
| CD | Credit/Debit Posted Incorrectly | Processing Errors | 30 days |
| AA | Cardholder Does Not Recognize | Consumer Disputes | 30 days |
| AP | Recurring Payments | Consumer Disputes | 30 days |
| RG | Non-Receipt of Goods or Services | Consumer Disputes | 30 days |
| RM | Quality Discrepancy | Consumer Disputes | 30 days |
| RN | Credit Not Received | Consumer Disputes | 30 days |
| AT | Authorization Noncompliance | Consumer Disputes | 30 days |
| NF | Non-Receipt of Cash at ATM | Retrieve and Resolve | 30 days |
| NC | Not Classified | Retrieve and Resolve | 30 days |

**Universal merchant response window: 30 days** (acquirers may impose shorter internal deadlines of 20-25 days).
**Cardholder filing window: 120 calendar days** from the transaction processing date (extendable by 30 days if a retrieval request was filed first).
