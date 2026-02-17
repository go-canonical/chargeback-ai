# American Express Chargeback Reason Codes

> Last updated: 2026-02. American Express organizes disputes into five categories:
> Fraud (FR), Authorization (A), Consumer Disputes (C), Processing Errors (P), and Miscellaneous (M).
> Merchant response window: **20 days** for all codes.
> Amex uses an **inquiry-first process** before formal chargebacks. Respond to inquiries promptly to prevent escalation.
> Submit responses through the **American Express Online Merchant Center** or via fax.

---

## FR2 — Fraud Full Recourse Program

**Category:** Fraud
**Time Limit:** Merchant has 20 days to respond. However, merchants enrolled in this program are generally not eligible to submit compelling evidence for fraud claims.

**Description:**
The merchant has been placed in the American Express Fraud Full Recourse Program due to an excessive rate of fraudulent transactions. All fraud-related disputes are immediately charged back to the merchant without the standard inquiry process. This is a punitive program, not a per-transaction dispute.

**Required Evidence:**
- Merchants in this program typically cannot dispute individual fraud chargebacks with evidence
- The primary recourse is to improve fraud prevention practices to exit the program

**Compelling Evidence (improves win rate):**
- Not applicable; evidence submission is generally not permitted under FR2
- Focus efforts on program exit rather than individual dispute responses

**Strategy Tips:**
- Prioritize reducing fraud rates to exit the program by implementing AVS, CVV verification, 3D Secure, and third-party fraud screening tools
- Work directly with your acquirer to develop and document a remediation plan
- Audit your transaction mix to identify which product categories, geographies, or channels generate the most fraud
- Consider temporarily tightening fraud filters even if it means declining some legitimate orders

**Common Mistakes:**
- Attempting to fight individual FR2 chargebacks instead of addressing the systemic root cause
- Not implementing fraud prevention tools quickly enough after program enrollment
- Failing to communicate remediation progress to your acquirer
- Ignoring the program enrollment notification and continuing business as usual

---

## FR4 — Immediate Chargeback Program

**Category:** Fraud
**Time Limit:** Merchant has 20 days to respond.

**Description:**
The merchant has exceeded the 1% chargeback threshold and has been placed in the Immediate Chargeback Program. All disputes bypass the standard inquiry phase and are immediately processed as chargebacks. The underlying dispute reason still determines what evidence is needed to fight each chargeback.

**Required Evidence:**
- Standard evidence for the underlying dispute reason (same as the corresponding C-series or P-series code that the chargeback relates to)
- Documentation demonstrating the specific chargeback is invalid

**Compelling Evidence (improves win rate):**
- All compelling evidence applicable to the underlying dispute reason code
- Proof the transaction was legitimate and properly fulfilled
- Documentation showing the cardholder received the goods or services

**Strategy Tips:**
- Reduce your overall chargeback ratio to exit the program as quickly as possible
- Implement chargeback prevention alerts (Ethoca, Verifi) and rapid refund programs to intercept disputes before they become chargebacks
- Understand that the underlying dispute reason still determines your evidence strategy — treat each FR4 chargeback according to its root cause code
- Track and categorize incoming chargebacks to identify the most common reasons and address them systematically

**Common Mistakes:**
- Ignoring the program placement notification and not taking corrective action
- Not understanding that the underlying dispute reason still determines the required evidence
- Treating all FR4 chargebacks the same instead of responding to each based on its specific reason
- Failing to implement prevention measures that would reduce the overall chargeback rate

---

## FR6 — Partial Immediate Chargeback

**Category:** Fraud
**Time Limit:** Merchant has 20 days to respond.

**Description:**
Similar to FR4, but applies specifically to low-value disputes. The merchant has been placed in the Partial Immediate Chargeback Program, where low-value disputes skip the inquiry phase and proceed directly to chargeback. Higher-value disputes may still go through the standard inquiry process.

**Required Evidence:**
- Standard evidence for the underlying dispute reason
- Documentation proving the transaction was valid

**Compelling Evidence (improves win rate):**
- All applicable evidence for the underlying dispute reason code
- Transaction records, delivery confirmations, or service completion documentation

**Strategy Tips:**
- Prioritize reducing chargeback volume on low-ticket transactions, as the cumulative effect triggers this program
- Implement clear billing descriptors so cardholders recognize charges and do not dispute them
- Send order confirmation emails immediately after purchase to reduce friendly fraud on small transactions
- Review your low-value transaction mix to identify patterns driving chargebacks

**Common Mistakes:**
- Ignoring low-value chargebacks because they seem individually insignificant
- Not recognizing that cumulative low-value chargebacks triggered the program placement
- Failing to implement billing descriptor improvements that would reduce cardholder confusion
- Not tracking chargeback-to-transaction ratios separately for low-value orders

---

## A01 — Charge Amount Exceeds Authorization Amount

**Category:** Authorization
**Time Limit:** Merchant has 20 days to respond.

**Description:**
The settled transaction amount exceeds the amount for which authorization approval was obtained. The cardholder was charged more than what was originally authorized. This commonly occurs when tips, surcharges, or additional items are added after the initial authorization.

**Required Evidence:**
- Valid authorization approval code for the full transaction amount
- POS or gateway logs showing the approval code, date, and time
- Proof the charge falls within an applicable industry exception (e.g., tips at restaurants, fuel dispenser tolerances)

**Compelling Evidence (improves win rate):**
- Itemized receipt showing the authorized amount matched the final charge
- Signed receipt or cardholder acknowledgment of the final amount, including any added amounts
- Documentation of industry-standard tolerance rules that apply to your merchant category

**Strategy Tips:**
- Always obtain authorization for the final amount, including tips or surcharges, before settling the transaction
- If your industry has variable-amount tolerances (fuel, hospitality), document that you operated within those tolerances and keep records of applicable rules
- For restaurants, ensure your POS system is configured to handle tip adjustments within Amex's allowed tolerance (typically 20% above the original authorization)
- Re-authorize the transaction if the final amount exceeds the tolerance threshold

**Common Mistakes:**
- Settling a transaction for more than the authorized amount without re-authorizing
- Failing to include the approval code and timestamp in the dispute response
- Not understanding the specific tolerance rules for your merchant category code
- Adding charges after authorization without cardholder consent or re-authorization

---

## A02 — No Valid Authorization

**Category:** Authorization
**Time Limit:** Merchant has 20 days to respond.

**Description:**
The merchant processed the transaction without obtaining a valid authorization approval, or the authorization request was declined and the merchant processed the transaction anyway. This is one of the most straightforward chargeback codes and is very difficult to defend without a valid approval code.

**Required Evidence:**
- Proof of a valid authorization approval (approval code, date, and time)
- If the card was expired at the time of the transaction, proof it was processed before expiration
- Gateway or terminal logs confirming real-time authorization was obtained

**Compelling Evidence (improves win rate):**
- Gateway or terminal logs confirming real-time authorization with matching transaction details
- Evidence the authorization was obtained within the required timeframe for your merchant category
- Processor records confirming the authorization was valid and matched the cleared transaction

**Strategy Tips:**
- Never process a transaction after receiving a decline response — ask the customer for an alternative payment method
- Ensure your POS system is configured to require authorization on every transaction regardless of amount
- If a customer insists the decline is an error, have them contact their card issuer directly rather than forcing the transaction through

**Common Mistakes:**
- Force-posting transactions after receiving a decline response
- Using an expired authorization code for a delayed shipment
- Processing transactions offline or using floor limits without real-time authorization
- Not retaining authorization response logs as evidence

---

## A08 — Authorization Approval Expired

**Category:** Authorization
**Time Limit:** Merchant has 20 days to respond.

**Description:**
The authorization approval expired before the merchant submitted the transaction for settlement. American Express authorizations have limited validity windows, and transactions must be settled within those windows. The specific validity period varies by merchant category but is generally 7 to 30 days.

**Required Evidence:**
- Proof the authorization was still valid at the time of settlement
- Documentation showing the transaction was submitted within the required timeframe
- Authorization and settlement timestamps demonstrating compliance

**Compelling Evidence (improves win rate):**
- Terminal or gateway logs with timestamps showing both the authorization and settlement dates
- Evidence of a delayed shipment or fulfillment that justified the timing gap, with re-authorization documentation
- Proof a new authorization was obtained before settlement if the original had expired

**Strategy Tips:**
- Submit transactions for settlement promptly, ideally on the same day as the sale
- For delayed-delivery orders (back-orders, pre-orders, custom items), obtain a new authorization before shipping
- Set up automated alerts for unsettled authorizations approaching expiration
- Know the authorization validity window for your merchant category and build settlement processes around it

**Common Mistakes:**
- Waiting too long to settle after obtaining authorization
- Not re-authorizing for back-ordered or delayed shipments
- Assuming authorizations remain valid indefinitely
- Not tracking authorization expiration dates in your order management system

---

## C02 — Credit Not Processed

**Category:** Consumer Disputes
**Time Limit:** Merchant has 20 days to respond.

**Description:**
The cardholder claims a refund or credit was promised by the merchant but was never issued to their American Express account. This commonly occurs when a merchant agrees to a refund verbally or in writing but fails to process it, or when there is a delay that causes the cardholder to file a dispute before the credit posts.

**Required Evidence:**
- Proof that a credit has already been processed (credit transaction receipt, settlement report, ARN)
- Documentation that the cardholder is not entitled to a credit under the return/refund policy
- Copy of the return/refund policy the cardholder agreed to at the time of purchase

**Compelling Evidence (improves win rate):**
- Evidence the cardholder was made aware of the return/refund policy before purchase
- Correspondence showing the refund was issued or that the cardholder agreed no refund was owed
- Settlement records with the credit transaction date and reference number
- Proof the cardholder did not meet the conditions for a refund (e.g., did not return merchandise)

**Strategy Tips:**
- Process refunds promptly (within 5-7 business days of the return) and retain confirmation records
- Always communicate refund timelines to cardholders and document those communications
- If a refund was issued by check or store credit instead of back to the card, document the cardholder's agreement to that arrangement
- Send refund confirmation emails with expected processing times to prevent premature disputes

**Common Mistakes:**
- Issuing a refund by check or other means without documenting it and informing Amex
- Failing to respond with proof that the credit was already processed
- Delaying refund processing for weeks, causing the cardholder to file a dispute
- Not having a clear, written return policy accessible to cardholders at checkout

---

## C04 — Goods/Services Returned or Refused

**Category:** Consumer Disputes
**Time Limit:** Merchant has 20 days to respond.

**Description:**
The cardholder returned merchandise or refused delivery and claims the merchant did not issue a corresponding refund. This applies both to goods sent back by mail and goods refused at the point of delivery.

**Required Evidence:**
- Proof the goods were not actually returned (carrier tracking showing items were not shipped back, no return receipt on file)
- Copy of the return policy and proof the cardholder was aware of it before purchase
- Proof a refund was already issued (credit transaction receipt, settlement report)

**Compelling Evidence (improves win rate):**
- Signed delivery confirmation showing the cardholder accepted the goods without noting damage or refusal
- Documentation that the return did not comply with the merchant's stated return policy (e.g., outside the return window, item was used or damaged)
- Correspondence with the cardholder about the return or refund
- Proof the returned merchandise was received in a condition that does not qualify for a refund

**Strategy Tips:**
- Require return tracking numbers from cardholders and inspect returned goods promptly upon receipt
- Make your return policy clearly visible at checkout, on receipts, and on your website
- Process refunds immediately upon receiving and inspecting returned goods
- If a return does not meet your policy requirements, communicate the denial clearly in writing

**Common Mistakes:**
- Not having a documented return policy accessible to the cardholder at time of purchase
- Failing to provide proof the cardholder accepted delivery
- Not inspecting returned merchandise and documenting its condition
- Delaying the refund after receiving a valid return

---

## C05 — Goods/Services Cancelled

**Category:** Consumer Disputes
**Time Limit:** Merchant has 20 days to respond.

**Description:**
The cardholder claims they cancelled an order for goods or services and the merchant did not issue a refund. This applies when the cardholder asserts they cancelled before fulfillment, or when the merchant did not deliver within the expected timeframe, triggering a cancellation right.

**Required Evidence:**
- Copy of the cancellation policy and proof the cardholder agreed to it at time of purchase
- Documentation showing the cancellation request was received after the allowed cancellation window
- Proof the goods or services were already delivered before the cancellation request
- Proof a credit was already issued

**Compelling Evidence (improves win rate):**
- Evidence the goods or services were delivered before the cardholder attempted to cancel
- Correspondence showing the cardholder did not cancel within the allowed cancellation window
- Timestamped cancellation policy acceptance by the cardholder
- Proof the cardholder used the service or goods after the alleged cancellation

**Strategy Tips:**
- Clearly state cancellation terms at the time of purchase, including deadlines and any non-refundable components
- Log all cancellation requests with timestamps and send written confirmation to the cardholder
- If the cancellation is outside the allowed window, communicate this to the cardholder in writing immediately
- For services, document that the service was rendered before the cancellation request

**Common Mistakes:**
- Having unclear or hidden cancellation policies
- Not providing evidence that the cancellation request was received after the allowed window
- Failing to log cancellation request dates and times
- Not sending cancellation confirmation or denial to the cardholder in writing

---

## C08 — Goods/Services Not Received or Only Partially Received

**Category:** Consumer Disputes
**Time Limit:** Merchant has 20 days to respond.

**Description:**
The cardholder claims they did not receive the purchased goods or services, or received only a partial fulfillment. This is one of the most common consumer dispute codes for both e-commerce and service-based transactions.

**Required Evidence:**
- Proof of delivery: tracking number, signed delivery confirmation, carrier records showing delivery to the cardholder's address
- For services: documentation showing the service was rendered (signed work order, completion report, access logs)
- For digital goods: download logs, access timestamps, or email delivery confirmation

**Compelling Evidence (improves win rate):**
- Delivery confirmation signed by the cardholder or an authorized representative at the delivery address
- IP address, email, or download logs confirming digital goods were accessed
- Photos of delivered items at the delivery location (provided by the carrier)
- Post-delivery communication from the cardholder acknowledging receipt
- GPS-confirmed delivery data from the carrier

**Strategy Tips:**
- Always use trackable shipping methods with delivery confirmation for physical goods
- For high-value orders, require signature on delivery — this is the single strongest piece of evidence
- Ship to the billing address whenever possible; alternate shipping addresses increase dispute risk
- For digital goods, log download timestamps, IP addresses, and usage data as proof of delivery

**Common Mistakes:**
- Using untrackable shipping methods or shipping without delivery confirmation
- Providing a tracking number that shows shipment but not confirmed delivery
- Not retaining delivery confirmation records for the full dispute window
- Charging the cardholder before shipping the merchandise

---

## C14 — Paid by Other Means

**Category:** Consumer Disputes
**Time Limit:** Merchant has 20 days to respond.

**Description:**
The cardholder claims the transaction was already paid for using a different payment method (cash, check, another credit card, gift card, etc.) and the Amex charge is a duplicate payment for the same purchase.

**Required Evidence:**
- Transaction records showing only one payment was received for the order
- Proof that no duplicate payment exists for the same order or invoice
- Itemized invoice matching the single Amex charge

**Compelling Evidence (improves win rate):**
- Itemized invoice tied to the specific Amex charge with a unique order number
- Bank or POS records showing only one payment was collected for the transaction
- Correspondence with the cardholder confirming the Amex charge was the sole payment
- Payment reconciliation report showing no other payment method was used for the order

**Strategy Tips:**
- Cross-reference all payment records when a dispute is received to rule out duplicate billing
- Keep detailed records linking each payment to a specific order number or invoice
- When a customer switches payment methods during checkout, void the original card transaction immediately
- Implement reconciliation processes that flag potential duplicate payments across payment methods

**Common Mistakes:**
- Not checking internal records for a duplicate payment before responding to the dispute
- Failing to provide itemized documentation tying the Amex charge to a specific order
- Not voiding the original transaction when a customer pays by another means
- Lacking the ability to search for payments across different payment methods for the same order

---

## C18 — "No Show" or CARDeposit Cancelled

**Category:** Consumer Disputes
**Time Limit:** Merchant has 20 days to respond.

**Description:**
The cardholder disputes a lodging "no-show" charge or claims a CARDeposit (guaranteed reservation deposit) was not refunded after proper cancellation. This code applies primarily to the travel and hospitality industry, including hotels, resorts, and car rental companies.

**Required Evidence:**
- Copy of the reservation policy, including no-show and cancellation terms
- Proof the cardholder was informed of the policy at the time of booking
- Proof the cancellation was made outside the allowed cancellation window, or that the cardholder did not cancel at all
- The confirmation number and reservation details

**Compelling Evidence (improves win rate):**
- Reservation confirmation sent to the cardholder that prominently displays the cancellation policy
- Cancellation log showing no valid cancellation was received before the deadline
- Evidence the guest actually checked in or used the service
- Proof the cardholder was provided a cancellation number (demonstrating they were familiar with the cancellation process)

**Strategy Tips:**
- Always provide a cancellation number and written confirmation to the guest at the time of booking
- Include cancellation terms prominently in reservation confirmations — do not bury them in fine print
- Log all cancellation requests with timestamps and cancellation reference numbers
- If you offer a grace period for cancellations, document it and enforce it consistently

**Common Mistakes:**
- Not recording or retaining cancellation confirmation numbers and timestamps
- Failing to prove the cardholder was made aware of the no-show policy at the time of booking
- Not including the cancellation policy in the booking confirmation email
- Charging no-show fees when the cardholder cancelled within the allowed window

---

## C28 — Cancelled Recurring Billing

**Category:** Consumer Disputes
**Time Limit:** Merchant has 20 days to respond.

**Description:**
The cardholder claims they cancelled a recurring billing arrangement but continued to be charged, or that they were unable to cancel through the merchant's available cancellation mechanisms. This is a high-volume dispute code for subscription-based businesses.

**Required Evidence:**
- Proof the cardholder did not cancel (system logs showing no cancellation request was received)
- Copy of the recurring billing agreement signed or accepted by the cardholder, including cancellation terms
- Proof a credit was already issued for charges billed after cancellation

**Compelling Evidence (improves win rate):**
- Logs showing the cardholder continued to use the service after the alleged cancellation date
- Communication records showing no cancellation request was received through any channel
- Timestamped evidence the cardholder actively used the subscription (login activity, feature usage, downloads)
- Cancellation policy excerpt showing the steps required and proof those steps were not taken

**Strategy Tips:**
- Provide clear, easy-to-use cancellation mechanisms — do not bury the cancel button or require phone calls
- Send cancellation confirmation emails immediately upon processing a cancellation request and retain them
- Stop billing immediately upon receiving a cancellation request; even one extra billing cycle will likely lose the dispute
- Send advance billing reminders before each recurring charge, especially before annual renewals

**Common Mistakes:**
- Making cancellation difficult, hidden, or requiring excessive steps
- Continuing to charge after receiving a cancellation request, even by one billing cycle
- Not retaining timestamped cancellation request logs as evidence
- Failing to send billing reminders before recurring charges

---

## C31 — Goods/Services Not as Described

**Category:** Consumer Disputes
**Time Limit:** Merchant has 20 days to respond.

**Description:**
The cardholder claims the received goods or services materially differed from what was described at the time of purchase. This covers discrepancies in quality, features, specifications, color, size, or any other material attribute that was part of the purchase decision.

**Required Evidence:**
- Copy of the product or service description as presented to the cardholder at time of purchase
- Proof the goods or services matched the description (photos, specifications, inspection reports)
- Evidence the cardholder did not attempt to return the merchandise or resolve the issue with the merchant before filing a dispute

**Compelling Evidence (improves win rate):**
- Product listing screenshots or catalog pages matching the delivered items, timestamped at the time of sale
- Inspection reports or quality control documentation confirming the goods met specifications
- Correspondence where the cardholder acknowledged receipt without complaint
- Proof the cardholder continued to use the goods or services after claiming they were not as described
- Evidence a return, exchange, or repair was offered but refused by the cardholder

**Strategy Tips:**
- Ensure all product and service descriptions are accurate, detailed, and include high-quality representative photos
- Document the condition of goods before shipping with photographs and retain those records
- Respond to cardholder complaints quickly — resolving issues before they escalate to disputes has the highest success rate
- Archive product listing pages with timestamps so you can prove what was displayed at the time of purchase

**Common Mistakes:**
- Using stock photos that do not accurately represent the actual product
- Not keeping historical records of product descriptions at the time of sale
- Ignoring cardholder complaints about product quality, pushing them to file a dispute
- Failing to offer a return or exchange before the cardholder contacts Amex

---

## C32 — Goods/Services Damaged or Defective

**Category:** Consumer Disputes
**Time Limit:** Merchant has 20 days to respond.

**Description:**
The cardholder claims the goods or services received were damaged upon arrival or are defective and do not function as intended. This code covers both shipping damage and manufacturing defects.

**Required Evidence:**
- Proof the goods were shipped in good condition (pre-shipment photos, quality inspection records)
- Documentation of packaging methods showing adequate protection for the product
- Proof a replacement, repair, or refund was already offered and accepted by the cardholder

**Compelling Evidence (improves win rate):**
- Carrier claim documentation if damage occurred in transit (filed claim with the shipping carrier)
- Signed acceptance by the cardholder upon delivery without noting damage on the delivery receipt
- Evidence the cardholder did not return the merchandise for inspection as required
- Pre-shipment quality inspection or testing records
- Proof the cardholder was offered a resolution (replacement, repair, or refund) but did not respond or refused

**Strategy Tips:**
- Use adequate packaging and insure high-value shipments against transit damage
- Offer a clear, easy process for reporting damaged or defective goods and follow through on repairs or replacements promptly
- Photograph items before packaging and retain those records for the dispute window
- If damage occurred in transit, file a carrier claim and share the claim information with the cardholder

**Common Mistakes:**
- Not offering to resolve the issue before a chargeback is filed
- Failing to document the condition of goods before shipment with photos or inspection records
- Not filing a carrier claim for shipping damage
- Requiring the cardholder to pay return shipping for damaged or defective items

---

## P01 — Unassigned Card Number

**Category:** Processing Errors
**Time Limit:** Merchant has 20 days to respond.

**Description:**
The card number used to process the transaction does not belong to a valid American Express account or is assigned to a different cardholder. This typically occurs with manually keyed transactions where the card number is entered incorrectly, or when a card number is fabricated.

**Required Evidence:**
- Proof the correct card number was used (transaction receipt, POS logs)
- Valid authorization approval with a matching card number
- Evidence the card was electronically read (chip, swipe, or contactless) rather than manually entered

**Compelling Evidence (improves win rate):**
- Physical card imprint or EMV chip data showing the correct card number was captured
- Gateway logs confirming the card number submitted matched the authorization request
- Proof the authorization was approved by Amex for the card number in question

**Strategy Tips:**
- Always verify card numbers before processing, especially for manual key-entry transactions
- Use chip, contactless, or swipe reads to avoid manual entry errors whenever possible
- Implement Luhn check validation for manually entered card numbers before submitting for authorization

**Common Mistakes:**
- Transposing digits during manual card entry
- Not verifying the card number on the authorization response matches the card presented
- Processing transactions with card numbers provided verbally without verification
- Not implementing basic card number validation checks in your payment system

---

## P03 — Credit Processed as Charge

**Category:** Processing Errors
**Time Limit:** Merchant has 20 days to respond.

**Description:**
A transaction that should have been processed as a credit or refund was instead processed as a charge to the cardholder's account. The cardholder was debited when they should have been credited.

**Required Evidence:**
- Proof the transaction was correctly processed as a charge and not a credit (if the charge was intentional)
- Or proof a correcting credit has already been issued to fix the error
- Transaction records showing the original charge and any subsequent credits

**Compelling Evidence (improves win rate):**
- POS system logs showing the transaction type that was submitted
- Settlement reports showing the correcting credit was processed
- Correspondence with the cardholder confirming the correction was made

**Strategy Tips:**
- Double-check the transaction type (sale vs. refund) before processing, especially on manual terminals
- Train staff thoroughly on the difference between charge and credit functions on the POS terminal
- Review batch settlement reports before submission to catch transaction type errors

**Common Mistakes:**
- Accidentally processing a refund as a sale on the terminal
- Not issuing the correcting credit promptly after discovering the error
- Not training staff on proper refund procedures
- Failing to review batch reports for transaction type discrepancies before settlement

---

## P04 — Charge Processed as Credit

**Category:** Processing Errors
**Time Limit:** Merchant has 20 days to respond.

**Description:**
A transaction that should have been a charge was incorrectly processed as a credit to the cardholder's account. The cardholder received a credit when they should have been charged for a purchase.

**Required Evidence:**
- Proof the transaction was correctly processed as a charge (if it was)
- Documentation showing the credit was intentional (e.g., a legitimate refund for a prior purchase)
- Transaction records linking the credit to a valid prior charge

**Compelling Evidence (improves win rate):**
- POS logs and settlement reports showing the transaction history
- Correspondence with the cardholder regarding the credit
- Documentation of the prior transaction that warranted the refund

**Strategy Tips:**
- Review batch settlement reports daily for anomalies, including unexpected credits
- Use terminal prompts that require staff confirmation of the transaction type before processing
- Implement reconciliation checks that flag credits without a corresponding prior charge

**Common Mistakes:**
- Not catching the error before batch settlement
- Failing to reconcile daily transactions to identify misprocessed credits
- Not implementing confirmation prompts for credit transactions on the terminal
- Lacking an audit trail linking credits to their originating charges

---

## P05 — Incorrect Charge Amount

**Category:** Processing Errors
**Time Limit:** Merchant has 20 days to respond.

**Description:**
The amount charged to the cardholder does not match the amount the cardholder agreed to pay or the amount in the authorization. This can result from data entry errors, incorrect tip calculations, unauthorized surcharges, or system glitches.

**Required Evidence:**
- Signed receipt or order confirmation showing the cardholder agreed to the charged amount
- Authorization log matching the settled amount
- Itemized invoice or receipt for the transaction

**Compelling Evidence (improves win rate):**
- Itemized receipt showing the breakdown of the charge (subtotal, tax, tip, shipping, etc.)
- Correspondence where the cardholder agreed to the final amount
- Signed tip line or cardholder-written total on the receipt
- Digital order confirmation sent to the cardholder showing the exact amount before processing

**Strategy Tips:**
- Always review transaction amounts before settlement to catch data entry errors
- Inform cardholders of any additional charges (tips, taxes, surcharges, shipping) clearly before processing
- If you discover an amount error after processing, proactively issue a partial refund before a dispute is filed
- Retain signed receipts with the total amount clearly documented by the cardholder

**Common Mistakes:**
- Settling a different amount than what was authorized without re-authorizing
- Not disclosing additional fees (surcharges, convenience fees) before processing the transaction
- Making arithmetic errors when adding tips or calculating totals
- Not retaining signed receipts showing the cardholder-approved amount

---

## P07 — Late Submission

**Category:** Processing Errors
**Time Limit:** Merchant has 20 days to respond.

**Description:**
The transaction was submitted for processing after American Express's required deadline. Amex generally requires transactions to be submitted within 181 days of the transaction date, though earlier submission is expected. Late submissions create risk because the cardholder's account status may have changed.

**Required Evidence:**
- Proof the transaction was submitted within the required timeframe
- Documentation of extenuating circumstances for any delayed submission (system outage, processor error)
- Batch settlement timestamps from your processor

**Compelling Evidence (improves win rate):**
- Processor records with timestamps showing the batch was submitted on time
- Proof of delayed delivery that justified the late submission (e.g., custom-made goods, back-order)
- Documentation of technical issues that caused the processing delay

**Strategy Tips:**
- Submit transactions for settlement on the same day as the sale whenever possible
- For pre-orders or back-orders, do not charge until the item ships — this avoids late submission issues entirely
- Set up automated daily batch settlement to prevent transactions from sitting unsettled
- Monitor your batch reports for any transactions that have not settled within 24 hours

**Common Mistakes:**
- Holding transactions in the terminal without settling for extended periods
- Charging before goods are shipped, then shipping much later
- Not settling batches over weekends or holidays, causing multi-day delays
- Forgetting to process transactions from backup or offline terminals

---

## P08 — Duplicate Charge

**Category:** Processing Errors
**Time Limit:** Merchant has 20 days to respond.

**Description:**
The same transaction was processed more than once, resulting in multiple charges to the cardholder for a single purchase. This commonly occurs due to terminal errors, batch resubmission, or staff accidentally processing a transaction twice.

**Required Evidence:**
- Proof each charge represents a separate, legitimate transaction (distinct order numbers, dates, items)
- Itemized receipts or invoices for each charge showing different purchases
- If a duplicate did occur, proof a credit was already issued for the duplicate charge

**Compelling Evidence (improves win rate):**
- Distinct order numbers, timestamps, and product descriptions for each charge
- Separate delivery confirmations for separate shipments
- POS logs showing the transactions were initiated at different times for different purchases
- Proof the cardholder was notified of and agreed to multiple charges

**Strategy Tips:**
- Implement duplicate-detection logic in your payment processing system to flag same-card, same-amount charges within a short time window
- Review batch reports for duplicate entries before settlement
- Train staff to check whether the first transaction attempt succeeded before re-swiping or re-submitting
- When a terminal times out or shows an error, check the transaction status before retrying

**Common Mistakes:**
- Re-swiping or re-submitting when the terminal appears to error without checking if the first attempt went through
- Submitting the same batch multiple times due to timeout errors or system glitches
- Not providing separate invoices or order numbers for legitimately separate transactions
- Failing to issue a prompt credit when a genuine duplicate is identified

---

## P22 — Non-Matching Card Number

**Category:** Processing Errors
**Time Limit:** Merchant has 20 days to respond.

**Description:**
The card number submitted in the transaction does not match the card number on file with American Express, or does not align with the authorization details. The clearing record contains a different card number than what was authorized.

**Required Evidence:**
- Proof the correct card number was used (POS logs, gateway records)
- Authorization approval matching the submitted card number
- Transaction receipt showing the card number used

**Compelling Evidence (improves win rate):**
- Physical card imprint or chip transaction data confirming the card number
- Screenshot or log from the payment gateway showing the card number submitted and authorized
- Proof the card number discrepancy was caused by a processor or system error, not the merchant

**Strategy Tips:**
- Use chip or contactless technology to avoid manual entry errors that cause number mismatches
- Verify the last four digits of the card on every receipt against the physical card
- Implement automated checks that compare the authorization card number with the settlement card number before batch submission

**Common Mistakes:**
- Manually entering card numbers incorrectly, causing mismatches between authorization and settlement
- Not verifying card data against the authorization response before completing the transaction
- Using stored or tokenized card numbers that have become outdated
- Not reconciling authorization and settlement card numbers before batch processing

---

## P23 — Currency Discrepancy

**Category:** Processing Errors
**Time Limit:** Merchant has 20 days to respond.

**Description:**
The transaction was processed in a currency different from what the cardholder agreed to or expected. This includes situations where Dynamic Currency Conversion (DCC) was applied without consent, or where the settlement currency did not match the displayed price currency.

**Required Evidence:**
- Proof the cardholder agreed to the currency used for the transaction
- Transaction receipt showing the correct currency
- Authorization and settlement records with matching currency codes

**Compelling Evidence (improves win rate):**
- Screenshots of the checkout page showing the currency displayed to the cardholder at time of purchase
- Cardholder confirmation or consent for the currency used (signed DCC disclosure, digital acceptance)
- DCC consent form showing the exchange rate, markup, and final amounts in both currencies

**Strategy Tips:**
- Clearly display the transaction currency (including any conversion rates and fees) before the cardholder confirms the purchase
- Use Dynamic Currency Conversion (DCC) disclosures where applicable and obtain explicit cardholder consent
- Ensure your terminal and e-commerce platform are configured with the correct default currency for your region
- For international transactions, display prices in the cardholder's currency option clearly

**Common Mistakes:**
- Not disclosing conversion fees or the settlement currency to the cardholder
- Processing in the merchant's local currency without the cardholder's knowledge when DCC was expected
- Auto-applying Dynamic Currency Conversion without explicit cardholder consent
- Configuring terminals or websites with incorrect currency settings

---

## M01 — Chargeback Authorization

**Category:** Miscellaneous
**Time Limit:** N/A (merchant-initiated).

**Description:**
The merchant authorized American Express to process the chargeback. This is essentially a merchant acceptance of the dispute — the merchant agrees the cardholder's claim is valid and consents to the chargeback. No evidence submission is needed because the merchant has voluntarily accepted the dispute.

**Required Evidence:**
- None required; the merchant has accepted the chargeback

**Compelling Evidence (improves win rate):**
- Not applicable; the merchant has consented to the chargeback

**Strategy Tips:**
- Only authorize chargebacks when you genuinely agree the cardholder's claim is valid and a refund is warranted
- Use this code strategically when fighting the chargeback would cost more than the transaction amount (cost-benefit analysis)
- Track M01 chargebacks to ensure your team is not accepting disputes that could have been won
- Even though you accept the chargeback, analyze the root cause to prevent similar disputes in the future

**Common Mistakes:**
- Accidentally authorizing chargebacks that could have been successfully defended with available evidence
- Using M01 as a default response because of the short response window without evaluating the dispute
- Not tracking accepted chargebacks to identify patterns that could be prevented
- Failing to distinguish between disputes worth fighting and those where acceptance is the correct business decision

---

## Quick Reference

| Code | Name | Category | Time Limit |
|------|------|----------|------------|
| FR2 | Fraud Full Recourse Program | Fraud | 20 days |
| FR4 | Immediate Chargeback Program | Fraud | 20 days |
| FR6 | Partial Immediate Chargeback | Fraud | 20 days |
| A01 | Charge Amount Exceeds Authorization Amount | Authorization | 20 days |
| A02 | No Valid Authorization | Authorization | 20 days |
| A08 | Authorization Approval Expired | Authorization | 20 days |
| C02 | Credit Not Processed | Consumer Disputes | 20 days |
| C04 | Goods/Services Returned or Refused | Consumer Disputes | 20 days |
| C05 | Goods/Services Cancelled | Consumer Disputes | 20 days |
| C08 | Goods/Services Not Received or Only Partially Received | Consumer Disputes | 20 days |
| C14 | Paid by Other Means | Consumer Disputes | 20 days |
| C18 | "No Show" or CARDeposit Cancelled | Consumer Disputes | 20 days |
| C28 | Cancelled Recurring Billing | Consumer Disputes | 20 days |
| C31 | Goods/Services Not as Described | Consumer Disputes | 20 days |
| C32 | Goods/Services Damaged or Defective | Consumer Disputes | 20 days |
| P01 | Unassigned Card Number | Processing Errors | 20 days |
| P03 | Credit Processed as Charge | Processing Errors | 20 days |
| P04 | Charge Processed as Credit | Processing Errors | 20 days |
| P05 | Incorrect Charge Amount | Processing Errors | 20 days |
| P07 | Late Submission | Processing Errors | 20 days |
| P08 | Duplicate Charge | Processing Errors | 20 days |
| P22 | Non-Matching Card Number | Processing Errors | 20 days |
| P23 | Currency Discrepancy | Processing Errors | 20 days |
| M01 | Chargeback Authorization | Miscellaneous | N/A |

| Category | Codes | Process |
|----------|-------|---------|
| Fraud (FR) | FR2, FR4, FR6 | Program-based (bypass inquiry) |
| Authorization (A) | A01, A02, A08 | Inquiry then chargeback |
| Consumer Disputes (C) | C02, C04, C05, C08, C14, C18, C28, C31, C32 | Inquiry then chargeback |
| Processing Errors (P) | P01, P03, P04, P05, P07, P08, P22, P23 | Inquiry then chargeback |
| Miscellaneous (M) | M01 | Merchant-authorized |

**Universal merchant response window: 20 days.** Respond to inquiries promptly to prevent escalation to formal chargebacks. Submit through the American Express Online Merchant Center or via fax.
