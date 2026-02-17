# Mastercard Chargeback Reason Codes

> Last updated: 2026-02. Mastercard organizes disputes into four categories under the Mastercard Dispute Resolution process:
> Authorization (48xx), Point-of-Interaction Errors (48xx), Cardholder Disputes (48xx), and Fraud (48xx).
> All codes use the 48xx numeric series. Mastercard has consolidated many legacy codes into umbrella codes (4808, 4834, 4853).
> Merchant response window: **45 days** for all codes.

---

## 4807 — Warning Bulletin File

**Category:** Authorization
**Time Limit:** Issuer must file within 120 days of the transaction processing date. Merchant has 45 days to respond. *Status: Retired — merged into 4808. Legacy chargebacks under this code are still valid and must be contested.*

**Description:**
A transaction was processed on a card listed in Mastercard's Warning Bulletin File (a list of cards reported as lost, stolen, or otherwise flagged as high-risk). The merchant failed to check the bulletin or ignored a warning before completing the transaction.

**Required Evidence:**
- Proof the cardholder knowingly authorized the transaction
- Authorization approval code showing the issuer approved the transaction at the time of processing
- Evidence the chargeback does not comply with Mastercard's dispute rules
- Documentation of a refund if one has already been issued

**Compelling Evidence (improves win rate):**
- EMV chip transaction data proving the physical card was present and validated
- Signed receipt or delivery confirmation
- Documentation from your processor confirming the Warning Bulletin was checked and the card was not listed at the time of transaction

**Strategy Tips:**
- This code is retired; new disputes should arrive under 4808. If you still receive a 4807, treat it identically to 4808 and respond with the same evidence
- Modern POS systems check the Warning Bulletin automatically during authorization; ensure your system is configured to do so
- Always obtain real-time electronic authorization rather than using stored or offline approvals

**Common Mistakes:**
- Ignoring the chargeback because the code is "retired" — chargebacks filed under legacy codes are still valid and must be contested within the 45-day deadline
- Using floor limits or offline authorization that bypasses Warning Bulletin checking
- Not obtaining authorization for every transaction regardless of amount

---

## 4808 — Authorization-Related Chargeback

**Category:** Authorization
**Time Limit:** Issuer must file within 120 days of the transaction processing date. Merchant has 45 days to respond.

**Description:**
The merchant did not obtain proper authorization for the transaction, the authorization was declined but the transaction was processed anyway, or the authorization request was submitted after the transaction date. This is the primary active authorization dispute code, incorporating former codes 4807 and 4812.

**Required Evidence:**
- Valid authorization approval code for the transaction
- Proof the transaction was presented within 7 days of authorization (or within 30 days for pre-authorizations)
- Evidence the transaction was submitted against a valid account number in good standing
- Authorization request and response logs with timestamps

**Compelling Evidence (improves win rate):**
- Full authorization response log showing approval code, date, amount, and account number match
- Evidence that a re-authorization was obtained if the original authorization expired
- Documentation showing the transaction amount did not exceed the maximum authorized amount
- Processor confirmation that the authorization was valid and matched the cleared transaction

**Strategy Tips:**
- Never process a transaction after receiving a decline response, even if the customer insists — have them use a different card or contact their bank
- Submit transactions within 7 days of authorization; use pre-authorization holds for delayed fulfillment
- Keep all authorization logs with timestamps for at least 18 months
- If the transaction amount changes (e.g., tip added, quantity adjusted), obtain a new authorization for the final amount

**Common Mistakes:**
- Processing transactions on expired authorizations (authorizations typically expire after 7-30 days depending on merchant category)
- Force-posting transactions after receiving a decline response
- Failing to re-authorize when the transaction amount increases beyond the original authorization
- Settling a different amount than what was authorized without re-authorizing

---

## 4812 — Account Number Not on File

**Category:** Point-of-Interaction Errors
**Time Limit:** Issuer must file within 120 days of the transaction processing date. Merchant has 45 days to respond. *Status: Retired — merged into 4808. Legacy chargebacks under this code are still valid.*

**Description:**
The issuer does not have the account number in its records. The card number used for the transaction does not correspond to any active account. This typically results from manual key-entry errors, use of a closed account, or a fabricated card number.

**Required Evidence:**
- Evidence of appropriate transaction authorization with required data records (ACCOUNT NOT CLOSED, AUTH MMDDYY, or PREAUTH MMDDYY)
- Proof the account number on the transaction receipt matches a valid card number
- Authorization approval code from the transaction
- For card-present transactions: evidence the card was swiped, dipped, or tapped using EMV protocols

**Compelling Evidence (improves win rate):**
- Online authorization approval showing the issuer approved the transaction with the exact account number used
- Transaction receipt showing the full PAN matched the physical card presented
- EMV chip data or magnetic stripe read confirmation proving the card number was captured electronically (not manually keyed)

**Strategy Tips:**
- Always obtain real-time electronic authorization; avoid manually keying card numbers unless absolutely necessary
- For e-commerce transactions, use tokenization to avoid storing or transmitting incorrect account numbers
- Verify that the last four digits on the receipt match the physical card before completing card-present transactions

**Common Mistakes:**
- Manual key-entry errors transposing digits in the card number
- Processing transactions on accounts that were recently closed or transferred to a new number
- Not verifying that the authorization response account number matches the card presented
- Failing to implement Luhn check validation on manually entered card numbers

---

## 4831 — Transaction Amount Differs

**Category:** Point-of-Interaction Errors
**Time Limit:** Issuer must file within 120 days of the transaction processing date. Merchant has 45 days to respond. *Status: Retired — merged into 4834.*

**Description:**
The cardholder disputes a transaction because the final charged amount is higher than the amount they authorized. Common causes include unapproved surcharges, tips added incorrectly, or the merchant failing to notify the customer of a price change before completing the transaction.

**Required Evidence:**
- Signed receipt showing the cardholder agreed to the charged amount
- Documentation that the cardholder agreed to an amount range and the transaction did not exceed it
- Itemized receipt showing the breakdown of all charges
- Proof of a refund if one has already been issued

**Compelling Evidence (improves win rate):**
- Signed tip line or gratuity authorization with the cardholder's handwritten total
- Written or digital agreement to price changes or surcharges
- Authorization and clearing records showing matching amounts

**Strategy Tips:**
- This code is now handled under 4834; treat accordingly
- Always ensure the final transaction amount matches what the cardholder authorized
- If the amount changes after authorization (e.g., tip added), obtain a new authorization or ensure the tip does not exceed the percentage allowed under Mastercard rules

**Common Mistakes:**
- Adding tips or surcharges without re-authorization when required by Mastercard rules
- Not providing itemized receipts showing how the total was calculated
- Changing transaction amounts after the cardholder has left without notification
- Settling a higher amount than authorized without the cardholder's signed consent

---

## 4834 — Point-of-Interaction Error

**Category:** Point-of-Interaction Errors
**Time Limit:** Issuer must file within 120 days of the transaction processing date. Merchant has 45 days to respond.

**Description:**
An umbrella code covering various processing errors at the point of interaction. Mastercard has consolidated codes 4831, 4842, 4846, and 4857 under this code. The specific sub-reason is indicated in the dispute details and determines what evidence is required.

### Sub-Reason Codes:

**Duplicate Processing** — The same transaction was processed more than once, the merchant deposited both copies of a receipt, a batch was submitted multiple times, or the merchant deposited a receipt with more than one acquirer.

**Transaction Amount Differs** — The charged amount differs from what the cardholder agreed to. Covers unauthorized tips, surcharges, or price changes applied without consent.

**Late Presentment** — The clearing record was submitted more than 7 days after the transaction date and the account has been closed, or more than 180 days after the original transaction date.

**Currency Code Error** — Dynamic currency conversion was applied without cardholder consent, or the cardholder was not given the option to select their currency.

**Card-Activated Telephone Transaction** — The cardholder denies authorizing a transaction activated through a telephone system.

**Paid by Other Means** — The cardholder paid for the same goods or services through another method (cash, check, different card) and was also charged on this card.

**Required Evidence (varies by sub-reason):**
- **Duplicate processing:** Proof each transaction was separate and legitimate with unique order numbers, items, or dates; or proof a credit was already issued
- **Transaction amount differs:** Signed receipt showing the agreed amount with itemized breakdown; signed tip line or gratuity authorization
- **Late presentment:** Proof the transaction was submitted within 7 calendar days of the transaction date; proof the account was not permanently closed
- **Currency code error:** Documentation that correct currency conversion was applied, the cardholder was given a clear choice of currency, and the exchange rate and fees were disclosed
- **Card-activated telephone:** Call recordings or authentication logs showing the cardholder initiated the transaction
- **Paid by other means:** Proof no alternate payment was received for the same purchase
- **General:** Evidence a credit was already issued; proof the chargeback does not comply with Mastercard rules; original ARD in DE 72 (Data Record)

**Compelling Evidence (improves win rate):**
- Detailed transaction logs with timestamps, authorization codes, and system audit trails showing the complete transaction lifecycle
- Separate itemized invoices or receipts for each charge if accused of duplicate processing
- Batch submission timestamp logs showing timely processing
- DCC disclosure receipt signed or acknowledged by the cardholder with both currencies and exchange rate displayed
- Terminal configuration records showing correct currency settings
- Proof of alternate payment records showing no duplicate payment was received

**Strategy Tips:**
- Implement batch reconciliation processes that flag potential duplicates before submission
- Submit transactions within 24 hours of authorization when possible; never exceed 7 days
- Always provide customers with itemized receipts showing the exact amount charged
- For dynamic currency conversion, always give the cardholder a clear choice and disclose the exchange rate and any fees before processing
- Set up automated alerts for any transactions not settled within 48 hours
- Identify the specific sub-reason before preparing your response; evidence requirements differ significantly between sub-reasons

**Common Mistakes:**
- Submitting the same batch twice due to timeout errors or system glitches
- Depositing both the merchant and customer copies of a receipt
- Adding gratuities or surcharges without fresh authorization when required
- Delaying transaction submission beyond 7 days from the transaction date
- Not reconciling daily batches to catch duplicate entries
- Auto-applying dynamic currency conversion without explicit cardholder consent
- Processing duplicate transactions from a single telephone authorization

---

## 4835 — Card Not Valid

**Category:** Point-of-Interaction Errors
**Time Limit:** Issuer must file within 120 days of the transaction processing date. Merchant has 45 days to respond.

**Description:**
The card used for the transaction was not valid at the time of the transaction. This may mean the card had not yet been activated, was expired, or was otherwise flagged as invalid by the issuer. The merchant processed the transaction despite the card's invalid status.

**Required Evidence:**
- Authorization approval code showing the issuer approved the transaction with the card number used
- Proof the card was valid at the time of the transaction (authorization response showing approval, not decline)
- Transaction receipt showing the card details matched an active card
- Evidence of a refund if one has already been issued

**Compelling Evidence (improves win rate):**
- Full authorization response log showing the card was accepted and approved at the time of transaction
- EMV chip data confirming the card was electronically validated during the transaction
- Proof the card's expiration date had not passed at the time of the transaction

**Strategy Tips:**
- Always obtain real-time electronic authorization, which validates card status automatically
- Check the expiration date printed on the card against the current date for card-present transactions
- If the terminal returns a "card not valid" or "restricted card" response, do not override it

**Common Mistakes:**
- Processing transactions on expired cards without checking the expiration date
- Overriding terminal warnings about invalid or restricted cards
- Manually entering card details and failing to validate card status through the authorization system
- Not training staff to recognize and respond to "card not valid" authorization responses

---

## 4837 — No Cardholder Authorization

**Category:** Fraud
**Time Limit:** Issuer must file within 120 days of the transaction processing date. Merchant has 45 days to respond.

**Description:**
The cardholder claims they did not authorize, approve, or participate in the transaction. This is one of the most common fraud-related chargeback codes and can result from true fraud, friendly fraud, or merchant error. It applies to both card-present and card-not-present transactions.

**Required Evidence:**
- Signed receipt, work order, or delivery confirmation signed by the cardholder (for card-present, include "will call" or "in-store pickup" documentation)
- Proof the cardholder downloaded, used, or accessed digital goods or services
- Documentation that CVC2 was provided and validated in the authorization response
- Evidence that 3D Secure (Mastercard SecureCode / Identity Check) authentication was used
- Authorization approval code and AVS match confirmation

**Compelling Evidence (improves win rate):**
- Device fingerprint or IP address matching the cardholder's known profile
- Prior undisputed transactions from the same device, IP address, or shipping address
- Delivery confirmation with signature to the cardholder's verified billing address
- Communication records (emails, chat logs) with the cardholder acknowledging the purchase
- Login or session data showing the cardholder accessed their account to place the order
- Evidence from Mastercard's First-Party Trust Program data-sharing

**Strategy Tips:**
- Implement 3D Secure (Mastercard Identity Check) to shift liability to the issuer for authenticated card-not-present transactions
- For CNP transactions, always collect and transmit CVV2, AVS data, and use device fingerprinting
- Maintain a clear, recognizable billing descriptor so cardholders recognize charges on their statements; this is the single most effective prevention measure
- Use Mastercard's First-Party Trust Program data-sharing requirements when available to prevent friendly fraud disputes

**Common Mistakes:**
- Not collecting CVV2 for card-not-present transactions
- Using a billing descriptor that does not match your business name or website URL
- Shipping to an address that differs from the billing address without additional verification
- Failing to implement 3D Secure when it is available for your merchant category
- Not retaining signed receipts or delivery confirmations for at least 18 months

---

## 4840 — Fraudulent Processing of Transactions

**Category:** Fraud
**Time Limit:** Issuer must file within 120 days of the transaction processing date. Merchant has 45 days to respond.

**Description:**
The cardholder placed one authorized card-present transaction but received one or more additional unauthorized transactions within the next fifteen minutes. This code primarily addresses suspected merchant-side fraud (running a card multiple times without consent) but can also result from terminal errors or honest merchant mistakes.

**Required Evidence:**
- Proof that each transaction was for a separate, distinct purchase authorized by the cardholder
- Proof that the cardholder's PIN was entered for each transaction and sent with the authorization request
- Separate itemized receipts or invoices for each charge showing different goods or services
- Documentation explaining why multiple transactions were appropriate (e.g., separate items, separate invoices)

**Compelling Evidence (improves win rate):**
- Separate signed receipts for each charge, each with unique authorization codes
- Surveillance footage showing the cardholder present and consenting to each transaction
- Written correspondence from the cardholder acknowledging the multiple charges
- Proof a refund was already issued if the duplicate was an error

**Strategy Tips:**
- If a customer needs to make multiple purchases in quick succession, process them as a single transaction where possible
- If multiple transactions are necessary, clearly explain to the customer that they will see multiple charges and obtain explicit consent for each
- Maintain detailed logs of each transaction with separate authorization codes and timestamps

**Common Mistakes:**
- Accidentally submitting the same batch twice due to terminal timeout or connectivity issues
- Running a card multiple times due to terminal errors without voiding the duplicate transactions
- Not explaining multiple charges to the cardholder at the point of sale
- Splitting a single purchase into multiple transactions without the cardholder's knowledge or consent

---

## 4841 — Cancelled Recurring or Digital Goods Transaction

**Category:** Cardholder Disputes
**Time Limit:** Issuer must file within 120 days of the transaction processing date. Merchant has 45 days to respond. *Status: Being merged into 4853; may still appear independently.*

**Description:**
A recurring payment was charged after the cardholder claims to have cancelled the subscription, or a digital goods transaction was billed without adequate on-screen purchase controls. Covers subscription billing disputes, auto-renewal charges after cancellation, and digital content purchases where the cardholder did not consent to the recurring charge.

**Required Evidence:**
- Signed recurring billing agreement or terms of service with cancellation policy
- Proof the cardholder did not cancel according to the agreed terms and conditions
- Proof the cardholder is still using the goods or services after the alleged cancellation date
- Timestamped cancellation request logs showing no valid cancellation was received before the charge date
- Proof of a refund if one has already been issued

**Compelling Evidence (improves win rate):**
- Cancellation policy as agreed to by the cardholder at sign-up, with the cardholder's acceptance documented
- Login or usage logs showing the cardholder continued to access the service after the disputed charge date
- Confirmation emails sent at subscription sign-up showing terms and cancellation policy
- Billing reminder notification sent before the disputed charge
- Communication records showing the cardholder was informed of renewal terms

**Strategy Tips:**
- Process cancellation requests promptly and send written confirmation immediately upon receipt
- Maintain detailed logs of all cancellation requests, including timestamps, channels, and resolution
- Provide at least 10 days' notice before any price increase per Mastercard rules, and obtain clear consent for the new amount
- Make your cancellation process easy and obvious; difficult cancellation processes drive chargebacks and attract regulatory scrutiny
- Send billing reminders before each recurring charge, especially before annual renewals

**Common Mistakes:**
- Not processing cancellation requests in a timely manner, resulting in one more charge after the request
- Having a convoluted or hidden cancellation process (e.g., requiring phone calls when sign-up was online)
- Continuing to bill after a cancellation request was received but misrouted to the wrong department
- Not sending cancellation confirmation to the customer
- Raising subscription prices without the required notice period

---

## 4842 — Late Presentment

**Category:** Cardholder Disputes
**Time Limit:** Issuer must file within 120 days of the transaction processing date. Merchant has 45 days to respond. *Status: Retired — merged into 4834.*

**Description:**
The merchant submitted the transaction for processing too long after the transaction date. Mastercard considers a transaction late if submitted more than 7 days after the transaction date and the cardholder's account has since been closed, or if submitted more than 180 days after the original transaction date regardless of account status.

**Required Evidence:**
- Proof that presentment occurred within 7 calendar days of the transaction date
- Proof the cardholder's account has not been permanently closed at the time of presentment
- Batch submission timestamp logs from your processor
- Evidence the chargeback does not comply with Mastercard rules

**Compelling Evidence (improves win rate):**
- Processor records showing the exact date and time the transaction was submitted for clearing
- Authorization hold documentation showing the transaction was pre-authorized within the valid window
- Evidence of technical issues (system outages, processor delays) that caused late submission

**Strategy Tips:**
- Process and submit transactions within 24 hours of authorization whenever possible
- Use authorization holds (pre-authorizations) for delayed fulfillment scenarios such as back-orders or custom items
- Set up automated alerts for any transactions not settled within 48 hours
- This code is now handled under 4834; treat accordingly if received

**Common Mistakes:**
- Holding transactions for days or weeks before submitting them to the acquirer
- Forgetting to submit manual or offline transactions from backup terminals
- Not re-authorizing transactions when fulfillment is delayed beyond 7 days
- Waiting to ship before settling — settle at authorization time and re-authorize if the shipment is delayed

---

## 4846 — Correct Transaction Currency Code Not Provided

**Category:** Cardholder Disputes
**Time Limit:** Issuer must file within 120 days of the transaction processing date. Merchant has 45 days to respond. *Status: Retired — merged into 4834.*

**Description:**
The cardholder was not given the option to select their preferred currency, or dynamic currency conversion (DCC) was applied without the cardholder's explicit consent or was applied incorrectly. The settled currency or amount does not match what the cardholder expected based on the point-of-sale experience.

**Required Evidence:**
- Proof the cardholder was given a clear choice of currency and chose the converted currency
- Signed receipt or screen capture showing the currency selection by the cardholder
- Documentation of the exchange rate and any fees disclosed before the transaction was completed

**Compelling Evidence (improves win rate):**
- DCC disclosure receipt signed or digitally acknowledged by the cardholder, showing amounts in both currencies plus the exchange rate and markup
- Terminal log showing the cardholder actively selected the converted currency
- Screenshots or printouts of the DCC opt-in screen as displayed to the cardholder

**Strategy Tips:**
- Never automatically apply dynamic currency conversion; always present it as an option the cardholder can explicitly accept or decline
- Display the exchange rate, any fees or markup percentage, and the final amount in both currencies before the cardholder confirms
- Keep signed DCC consent receipts for at least 18 months to cover the dispute window
- This code is now handled under 4834; treat accordingly if received

**Common Mistakes:**
- Auto-applying dynamic currency conversion without explicit cardholder consent
- Not providing a clear opt-in/opt-out mechanism for currency conversion at the terminal
- Failing to disclose conversion fees and exchange rates before the cardholder confirms the transaction
- Configuring terminals with an incorrect default currency

---

## 4849 — Questionable Merchant Activity

**Category:** Fraud
**Time Limit:** Issuer must file within 180 days of the Mastercard Security Bulletin date. Merchant has 45 days to respond.

**Description:**
Mastercard has flagged the merchant under its Global Merchant Audit Program (GMAP) or Questionable Merchant Audit Program (QMAP) for suspected fraudulent or non-compliant activity. Only merchants placed under these monitoring programs should receive this code. This is the most serious chargeback code as it indicates Mastercard itself suspects the merchant may have acted improperly.

**Required Evidence:**
- Proof that the transactions were legitimate and that goods or services were delivered as described
- Documentation showing full compliance with Mastercard rules and operating regulations
- Evidence specifically refuting the allegations in the audit finding
- Complete transaction records, delivery confirmations, and customer correspondence
- Proof of refund if applicable

**Compelling Evidence (improves win rate):**
- Evidence of legitimate business operations: business licenses, supplier invoices, inventory records, and fulfillment documentation
- Third-party compliance audit or certification reports
- Customer testimonials or reviews confirming legitimate transactions
- Trend data showing declining chargeback ratios and improved compliance metrics
- Documentation of remediation steps taken since the audit notification

**Strategy Tips:**
- This code signals that Mastercard itself suspects merchant fraud; engage legal counsel immediately if you receive it
- Monitor Mastercard Global Security Bulletins regularly to identify if your business has been flagged
- Work with your acquirer immediately to develop and implement a remediation plan
- Maintain transparent advertising, accurate product descriptions, and clear refund policies
- Do not ignore GMAP/QMAP notifications — non-response can lead to merchant account termination

**Common Mistakes:**
- Ignoring GMAP/QMAP notifications from your acquirer or processor
- Continuing business practices that triggered the audit without implementing changes
- Not engaging your acquirer proactively when chargeback ratios begin increasing
- Selling goods or services that do not match their descriptions or advertisements
- Failing to engage legal counsel for what is essentially an accusation of merchant fraud

---

## 4850 — Installment Billing Dispute

**Category:** Cardholder Disputes
**Time Limit:** Issuer must file within 120 days of the transaction processing date. Merchant has 45 days to respond. *Status: Retired — merged into 4853.*

**Description:**
The cardholder disputes an installment billing transaction, claiming the number of installments, the amount billed, or the billing schedule differs from the original agreement. Covers acquirer- or merchant-financed installment billing arrangements, including "buy now, pay later" type programs.

**Required Evidence:**
- Signed installment agreement showing the total sale price, number of payments, each installment amount, and exact billing dates
- Proof the installments matched the agreed schedule and amounts
- Documentation of any notices sent to the cardholder about billing changes
- Proof of a refund if one has already been issued

**Compelling Evidence (improves win rate):**
- Original signed contract (electronic or paper signatures both accepted under Mastercard rules)
- Complete payment schedule with a comparison to actual charges showing they match
- Communication records showing any billing changes were disclosed and acknowledged by the cardholder
- Billing notification emails or SMS sent before each installment charge

**Strategy Tips:**
- Keep signed installment agreements accessible for at least the duration of the payment plan plus 18 months
- Send payment reminders before each installment is processed, including the amount and date
- Never accelerate installment processing without explicit cardholder and issuer consent
- This code is now handled under 4853; treat accordingly if received

**Common Mistakes:**
- Not retaining the signed installment agreement for the full required period
- Changing installment amounts or schedules without written cardholder consent
- Processing installments early or out of the agreed sequence
- Failing to notify the cardholder before each installment charge is processed

---

## 4853 — Cardholder Dispute

**Category:** Cardholder Disputes
**Time Limit:** Issuer must file within 120 days of the transaction processing date (or the expected delivery/service date for non-receipt claims). Merchant has 45 days to respond.

**Description:**
The primary umbrella code for cardholder disputes. Mastercard has consolidated codes 4841, 4850, 4855, 4859, and 4860 under this code. It covers goods or services not provided, goods not as described or defective, counterfeit merchandise, misrepresentation, cancelled recurring transactions, credit not processed, addendum disputes, and other cardholder complaints. The specific sub-reason is indicated in the dispute details.

### Sub-Categories:

**Not Received** — The cardholder paid for goods or services that were never delivered.

**Not as Described or Defective** — The goods or services received did not match the description, were defective, damaged, or materially different from what was advertised.

**Counterfeit Merchandise** — The merchandise received is an unauthorized copy or imitation sold as authentic.

**Misrepresentation** — The merchant misrepresented the product, service, or terms of the transaction through misleading advertising, hidden fees, or failure to disclose material terms.

**Cancelled Recurring Transaction** — A recurring charge was processed after the cardholder cancelled the subscription or recurring billing agreement.

**Credit Not Processed** — The cardholder was promised a refund or credit that has not been issued.

**Addendum / No-Show** — Additional fees were charged beyond what was agreed, or a no-show penalty was applied for a reservation the cardholder disputes.

**Required Evidence (varies by sub-category):**

*Not Received:*
- Delivery confirmation with tracking number and recipient signature
- Proof the cardholder picked up goods in-store (signed pickup receipt, "will call" documentation)
- Proof the service was performed and completed (service records, appointment logs, completion forms)
- For digital goods: download logs, access timestamps, email delivery confirmation

*Not as Described or Defective:*
- Original product description, listing, and specifications as advertised at time of purchase
- Evidence the goods matched the description and were not defective
- Proof the deficiency was corrected (replacement shipped, repair completed)
- Return policy documentation showing the cardholder did not follow the return process

*Counterfeit Merchandise:*
- Certificates of authenticity, authorized dealer documentation, or brand authorization letters
- Supply chain documentation showing the product was sourced from legitimate channels
- Serial numbers or authentication codes that can be verified with the brand owner

*Misrepresentation:*
- Complete and accurate product or service description as presented at time of purchase
- Terms and conditions the cardholder agreed to, with proof of acceptance
- Marketing materials and disclosure statements showing all fees, terms, and conditions were transparent

*Cancelled Recurring Transaction:*
- Proof the cardholder did not cancel per the agreed terms
- Proof the cardholder continued using the service after the alleged cancellation date
- Subscription agreement with cancellation terms and the cardholder's acceptance
- Timestamped cancellation request logs showing no valid cancellation was received

*Credit Not Processed:*
- Proof the refund was already issued (credit transaction receipt, Acquirer Reference Number)
- Proof the cardholder is not entitled to a refund per the disclosed terms of sale
- Refund timeline documentation showing the credit was processed within a reasonable period

**Compelling Evidence (improves win rate):**
- Carrier tracking with delivery confirmation and signature to the cardholder's verified address
- Photographs of goods as shipped (for "not as described" disputes)
- Usage or access logs showing the cardholder used the product or service after purchase
- Complete communication history with the cardholder showing resolution attempts
- Clear, published return/refund policy that was disclosed before purchase
- Evidence from Mastercard's First-Party Trust Program
- Brand authorization letters or third-party authentication reports (for counterfeit claims)
- Archived product listings with timestamps proving what was advertised at time of sale (for misrepresentation claims)
- Refund transaction record with ARN showing the credit was posted (for credit not processed claims)
- Login or session data showing the cardholder accessed the service after the disputed charge (for cancelled recurring claims)

**Strategy Tips:**
- Identify the specific sub-reason before preparing your response; evidence requirements differ significantly between sub-categories
- For "not received" disputes, always use tracked shipping with delivery confirmation and require signatures for items above your risk threshold (typically $100+)
- For recurring billing, implement Mastercard's Account Updater to ensure continued authorization even after card replacements
- For "credit not processed" claims, process refunds within 5-7 business days and send the cardholder confirmation with the expected posting timeframe
- Maintain comprehensive documentation of the full customer lifecycle: order, delivery, communications, returns, and refunds
- Archive product listings and marketing materials with timestamps to defend against "not as described" and misrepresentation claims
- Respond to quality complaints quickly — resolving issues before they become chargebacks has the highest win rate

**Common Mistakes:**
- Not identifying the specific sub-reason and submitting generic, non-targeted evidence
- Shipping without tracking or delivery confirmation
- Not having a clearly published refund/return policy accessible before purchase
- Taking too long to process refunds after agreeing to them
- Not keeping records of customer communication attempts and resolution offers
- Failing to respond to customer complaints before they escalate to chargebacks
- Using stock photos that do not accurately represent the product
- Not maintaining provenance records for branded merchandise

---

## 4854 — Cardholder Dispute — Not Elsewhere Classified

**Category:** Cardholder Disputes
**Time Limit:** Issuer must file within 120 days of the transaction processing date. Merchant has 45 days to respond. *Applies to U.S. region disputes only.*

**Description:**
A catch-all code for cardholder disputes in the United States when no other specific reason code applies. The cardholder claims their demands were unmet and the merchant refused to address the issue. This is the fallback code for US-region disputes that do not fit standard categories.

**Required Evidence:**
- Proof that a refund was already issued (if applicable)
- Written correspondence proving the cardholder no longer wishes to dispute the charge (if resolved directly)
- Evidence the chargeback does not comply with Mastercard rules
- Documentation specifically addressing the complaint raised in the dispute narrative

**Compelling Evidence (improves win rate):**
- Complete transaction records and order details
- Delivery tracking and confirmation
- Full customer communication history showing resolution attempts and offers made
- Refund logs with timestamps if a refund was processed
- Evidence the cardholder used or benefited from the goods or services

**Strategy Tips:**
- Carefully review the dispute details from your acquirer to understand the specific complaint; this code is a catch-all and the actual issue varies widely
- Proactive customer service is the best prevention; respond to all complaints promptly through multiple channels
- Maintain thorough records of every customer interaction across all channels (phone, email, chat, social media)
- Do not assume this code is unwinnable; a well-documented response addressing the specific complaint can succeed

**Common Mistakes:**
- Treating this as unwinnable because it is a "catch-all" code
- Not reading the actual dispute narrative to understand the specific issue the cardholder raised
- Failing to provide evidence targeted to the cardholder's stated complaint
- Not attempting to resolve the issue directly with the cardholder before the chargeback escalates

---

## 4855 — Goods or Services Not Provided

**Category:** Cardholder Disputes
**Time Limit:** Issuer must file within 120 days of the expected delivery date or service date. Merchant has 45 days to respond. *Status: Retired — merged into 4853.*

**Description:**
The cardholder paid for goods or services but claims they were never received. Applies to both card-present and card-not-present transactions, including in-store, online, phone, and mail-order purchases. Common causes include delivery delays, packages lost in transit, unfulfilled orders, and services never rendered.

**Required Evidence:**
- Delivery confirmation with tracking number showing delivery to the cardholder's address
- Proof the cardholder picked up the goods (signed receipt for in-store pickup or will-call)
- Proof the service was rendered (service records, appointment logs, completion forms)
- For digital goods: download logs, access timestamps, IP address at time of access
- Proof of a refund if one has already been issued

**Compelling Evidence (improves win rate):**
- Carrier tracking showing delivery to the cardholder's verified address with signature confirmation
- GPS delivery confirmation or photographs from the carrier showing the package at the delivery address
- Email or SMS delivery notification acknowledged by the cardholder
- Post-delivery communication from the cardholder acknowledging receipt (emails, reviews, support tickets)
- Login or access data showing the cardholder used the digital product or service after delivery

**Strategy Tips:**
- This code is now handled under 4853, but may still appear on legacy disputes; treat accordingly
- Always use tracked, insured shipping with delivery confirmation for physical goods
- For digital goods, log access timestamps, IP addresses, and device identifiers as proof of delivery
- Proactively communicate delays to the customer; a cardholder who knows a package is delayed is less likely to file a chargeback
- Ship to the AVS-verified billing address whenever possible; shipping to alternate addresses increases dispute risk

**Common Mistakes:**
- Shipping without tracking or delivery confirmation
- Not insuring high-value shipments against loss or damage
- Not following up on delivery exceptions or failed delivery attempts
- Marking an order as "shipped" when only a label was created but the package was not tendered to the carrier
- Charging the cardholder before shipping the merchandise

---

## 4857 — Card-Activated Telephone Transaction

**Category:** Cardholder Disputes
**Time Limit:** Issuer must file within 120 days of the transaction processing date. Merchant has 45 days to respond. *Status: Retired — merged into 4834.*

**Description:**
The cardholder denies authorizing a transaction activated through a telephone system (PIN entry, token, phone call, or security question). May involve a stolen phone used to activate a card, a forgotten legitimate transaction, or duplicate processing of a telephone-initiated charge.

**Required Evidence:**
- Proof the transaction is not a card-activated telephone transaction, or proof the cardholder authorized it
- Call recordings or logs showing the cardholder initiated the transaction
- Authentication records (PIN entry, security question responses)
- Proof a credit or refund was already processed

**Compelling Evidence (improves win rate):**
- Full call recording with the cardholder's voice authorizing the transaction
- Caller ID or ANI records matching the cardholder's registered phone number
- Transaction confirmation sent to the cardholder's email or phone after the call

**Strategy Tips:**
- This code is retired; new disputes fall under 4834. If received, treat as a 4834 POI error
- For telephone-activated transactions, always maintain call recordings and authentication logs for at least 18 months
- Send transaction confirmation via email or SMS immediately after telephone-initiated purchases

**Common Mistakes:**
- Not retaining call recordings or authentication logs for the required retention period
- Processing duplicate transactions from a single phone authorization
- Not sending written confirmation of telephone-initiated transactions
- Failing to verify the caller's identity before processing the transaction

---

## 4859 — Services Not Rendered

**Category:** Cardholder Disputes
**Time Limit:** Issuer must file within 120 days of the transaction processing date. Merchant has 45 days to respond. *Status: Being merged — addendum/no-show scenarios into 4853, ATM disputes into 4834.*

**Description:**
Covers three scenarios: (1) Services that were paid for but never provided. (2) No-show charges where the cardholder was billed a penalty for failing to cancel or honor a reservation, primarily in the hospitality industry. (3) ATM payout errors. Also covers addendum disputes where additional fees were charged beyond the agreed amount.

**Required Evidence:**
- **Services not rendered:** Proof the service was performed (service logs, appointment records, signed completion forms)
- **No-show:** Signed registration card or online booking confirmation showing the cancellation and no-show policy; proof the cardholder agreed to the penalty fee
- **Addendum:** Signed authorization for the additional charges beyond the original amount
- **ATM:** ATM transaction records and journal tape for the disputed transaction
- Proof of a refund if one has already been issued

**Compelling Evidence (improves win rate):**
- Copy of the booking confirmation email with cancellation policy and deadline highlighted
- Screenshots of the cancellation policy as displayed during online booking
- Proof the cardholder was notified of the cancellation deadline and no-show policy before the deadline passed
- Registration card or checkout page with the cardholder's signature or digital acceptance of the no-show fee
- Service completion photos or records with timestamps

**Strategy Tips:**
- For hotels and hospitality: always include cancellation policies in booking confirmations and display them prominently during checkout
- Obtain cancellation policy acknowledgment as a separate, explicit step in the booking process
- Send a reminder before the cancellation deadline with the policy terms
- For services, have the customer sign a completion form or acknowledgment when the service is delivered

**Common Mistakes:**
- Not including the cancellation or no-show policy in the booking confirmation
- Burying the policy in fine print that the cardholder did not explicitly accept
- Charging a no-show fee that exceeds one night's rate or the agreed penalty amount
- Not sending a cancellation deadline reminder to the cardholder
- Failing to document service completion with signed forms or records

---

## 4860 — Credit Not Processed

**Category:** Cardholder Disputes
**Time Limit:** Issuer must file within 120 days of the date the merchant agreed to refund or the date the cardholder expected to see the credit, whichever is later. Merchant has 45 days to respond. *Status: Retired — merged into 4853.*

**Description:**
The cardholder claims they were promised a refund or credit that has not been processed. The promise may have been written, verbal, or implied by the merchant's published return and refund policy. This is one of the most preventable chargeback codes.

**Required Evidence:**
- Proof the credit or refund was already issued (Acquirer Reference Number, credit transaction receipt, settlement record)
- Proof the cardholder is not entitled to a refund per the disclosed terms and conditions of sale
- Date and amount of the refund if already processed
- Proof the issue was resolved directly with the cardholder

**Compelling Evidence (improves win rate):**
- Refund transaction record with ARN (Acquirer Reference Number) showing the credit was posted to the cardholder's account
- Complete timeline of events: return received, refund processed, credit posted
- Email communication showing the cardholder was informed of the refund amount and expected posting timeframe
- Bank settlement records confirming the credit was delivered to the issuer

**Strategy Tips:**
- Process refunds within 5-7 business days of agreeing to issue them; delays are the primary cause of this chargeback
- Send the cardholder an email confirming the refund has been processed, including the expected posting timeframe (typically 5-10 business days)
- Track refund ARNs and retain them for at least 18 months
- This code is now handled under 4853; treat accordingly if received

**Common Mistakes:**
- Promising a refund but delaying processing for weeks
- Not informing the cardholder of the expected refund posting timeline
- Issuing store credit when the cardholder requested a refund to their card
- Not retaining proof of the refund transaction (ARN)
- Refunding to a different card or payment method than the original without the cardholder's explicit agreement

---

## 4862 — Counterfeit Transaction — Magnetic Stripe

**Category:** Fraud
**Time Limit:** Issuer must file within 120 days of the transaction processing date. Merchant has 45 days to respond.

**Description:**
A transaction was made with a counterfeit card using the magnetic stripe. The full magnetic stripe data was not transmitted to or approved by the issuer. The cardholder claims possession of their legitimate card at the time of the fraudulent transaction, indicating the card was cloned or skimmed.

**Required Evidence:**
- Imprinted or swiped sales draft signed by the cardholder
- Proof that the full, unaltered magnetic stripe data was read and transmitted during the transaction
- Evidence that a credit or refund has been issued (if applicable)

**Compelling Evidence (improves win rate):**
- EMV chip read data proving the terminal had chip capability and it was used (this effectively proves it was not a magnetic stripe fallback)
- Surveillance footage from the point of sale showing the transaction
- Proof the first four digits of the embossed account number on the front of the card matched the pre-printed BIN digits

**Strategy Tips:**
- Upgrade all terminals to EMV chip-enabled devices; chip transactions are far more resistant to counterfeiting than magnetic stripe
- If a magnetic stripe cannot be read, get a manual imprint of the front of the card and obtain the customer's signature
- Compare the first four digits on the front of the card with the pre-printed BIN digits to detect cloned cards
- Train staff to inspect physical card security features (hologram, embossing quality, signature panel)

**Common Mistakes:**
- Falling back to magnetic stripe swipe when the chip reader fails without taking additional verification steps (imprint, ID check)
- Not checking physical card security features such as the hologram, embossing quality, and BIN match
- Processing key-entered transactions as a fallback without obtaining a card imprint and signature
- Continuing to use non-EMV terminals, which leaves the merchant fully liable for counterfeit fraud

---

## 4863 — Cardholder Does Not Recognize — Potential Fraud

**Category:** Fraud
**Time Limit:** Issuer must file within 120 days of the transaction processing date. Merchant has 45 days to respond. *Status: Retired in some regions; may still appear on disputes.*

**Description:**
The cardholder does not recognize a card-not-present transaction on their statement and believes it may be fraudulent. This applies exclusively to CNP transactions (online, phone, mail order). May involve true fraud, intentional friendly fraud, or the cardholder simply failing to recognize a legitimate charge due to an unclear billing descriptor.

**Required Evidence:**
- Signed receipt or email acknowledgment from the cardholder
- Proof of positive AVS (Address Verification Service) match
- Proof that Mastercard SecureCode or Identity Check (3D Secure) was submitted with the authorization
- Documentation of delivery to the cardholder's verified address
- Proof of a refund if one has already been issued

**Compelling Evidence (improves win rate):**
- Device fingerprint, IP address, or browser data matching the cardholder's known profile
- Prior successful undisputed transactions from the same device, IP address, or account
- Email or chat communication with the cardholder referencing the specific purchase
- Login activity showing the cardholder accessed their account or used the product after purchase
- Evidence from Mastercard's First-Party Trust Program data-sharing

**Strategy Tips:**
- Use a clear, recognizable billing descriptor that matches your business name and website; this is the single most effective prevention measure for "does not recognize" disputes
- Implement 3D Secure (Mastercard Identity Check) to shift fraud liability to the issuer
- Send order confirmation and shipping notification emails immediately to create a paper trail the cardholder will recognize
- Include your customer service phone number in the billing descriptor so cardholders can contact you before filing a dispute

**Common Mistakes:**
- Using an obscure, abbreviated, or corporate-entity billing descriptor that does not match your consumer-facing storefront name
- Not sending transaction confirmation emails with clear descriptions of what was purchased
- Failing to implement AVS and CVV2 checks for card-not-present transactions
- Not maintaining records of customer communication and purchase history

---

## 4870 — Chip Liability Shift

**Category:** Fraud
**Time Limit:** Issuer must file within 120 days of the central processing date. Merchant has 45 days to respond.

**Description:**
A counterfeit card was used at a card-present merchant that did not process the EMV chip. Because the merchant's terminal did not read the chip (falling back to magnetic stripe swipe instead), the liability for the counterfeit fraud shifts from the issuer to the merchant under EMV liability shift rules. This code applies specifically to counterfeit card fraud at non-chip-compliant terminals.

**Required Evidence:**
- Proof that the EMV chip was properly read during the transaction (TC/cryptogram data)
- Proof that the card did not contain an EMV chip (if applicable)
- Documentation that the cardholder authorized the transaction
- Evidence the chargeback does not comply with Mastercard rules

**Compelling Evidence (improves win rate):**
- Terminal transaction log showing the chip read was attempted and completed successfully
- Application cryptogram or Transaction Certificate from the chip read
- Technical evidence of a chip malfunction forcing a fallback to magnetic stripe (terminal error logs)
- EMV terminal certification records from the acquirer or processor showing the terminal was chip-compliant

**Strategy Tips:**
- Upgrade all terminals to EMV chip-enabled devices; this is the only reliable prevention for this chargeback code
- Train staff to always insert the chip first; only fall back to swipe if the chip reader fails after multiple attempts, and document the fallback with terminal error logs
- If the chip read fails, consider declining the transaction rather than falling back to magnetic stripe, especially for high-value purchases
- Maintain up-to-date EMV terminal certification records

**Common Mistakes:**
- Using non-EMV terminals or having EMV chip capability disabled on the terminal
- Staff routinely swiping cards instead of using the chip reader for convenience
- Not documenting chip fallback scenarios when a genuine chip malfunction occurs
- Failing to maintain EMV certification records for each terminal
- Assuming contactless tap is the same as chip insert — verify your terminal processes both correctly

---

## 4871 — Chip/PIN Liability Shift

**Category:** Fraud
**Time Limit:** Issuer must file within 120 days of the transaction processing date. Merchant has 45 days to respond.

**Description:**
A chip-enabled card that was lost, stolen, or never received by the cardholder was used at a merchant that did not require PIN verification. Because the merchant's terminal did not enforce Chip and PIN verification, the liability shifts to the merchant. This differs from 4870 in that it involves lost, stolen, or never-received cards rather than counterfeit cards.

**Required Evidence:**
- Proof that PIN was verified during the transaction
- Proof that the EMV chip was read and PIN entry was required and completed
- Terminal log showing successful chip read and PIN verification
- Documentation showing the chargeback does not comply with Mastercard rules
- Evidence of a refund if one has already been issued

**Compelling Evidence (improves win rate):**
- Terminal transaction log showing both successful chip read and successful PIN entry
- Cardholder Verification Method (CVM) results from the transaction showing PIN was used
- Surveillance footage showing the individual entering a PIN at the terminal
- Proof of additional ID verification performed at point of sale for high-value transactions

**Strategy Tips:**
- Always require PIN entry when processing chip cards in PIN-priority markets
- Train staff to never bypass PIN entry, even if the customer claims they forgot their PIN — have them contact their bank instead
- For high-value transactions, consider requesting additional photo ID as a supplementary verification step
- Ensure terminals are configured for PIN-priority processing, not signature-priority

**Common Mistakes:**
- Allowing signature fallback when PIN should be required for the card type and market
- Staff bypassing PIN entry to speed up the checkout process
- Not verifying that the terminal is properly configured for PIN-priority processing
- Assuming that chip read alone is sufficient — PIN verification is required for protection against this liability shift
- Not maintaining terminal PIN pad certification records

---

## Quick Reference

| Code | Title | Category | Status |
|------|-------|----------|--------|
| 4807 | Warning Bulletin File | Authorization | Retired (merged into 4808) |
| 4808 | Authorization-Related Chargeback | Authorization | **Active** |
| 4812 | Account Number Not on File | Point-of-Interaction Errors | Retired (merged into 4808) |
| 4831 | Transaction Amount Differs | Point-of-Interaction Errors | Retired (merged into 4834) |
| 4834 | Point-of-Interaction Error | Point-of-Interaction Errors | **Active** |
| 4835 | Card Not Valid | Point-of-Interaction Errors | **Active** |
| 4837 | No Cardholder Authorization | Fraud | **Active** |
| 4840 | Fraudulent Processing of Transactions | Fraud | **Active** |
| 4841 | Cancelled Recurring or Digital Goods | Cardholder Disputes | Being merged into 4853 |
| 4842 | Late Presentment | Cardholder Disputes | Retired (merged into 4834) |
| 4846 | Correct Transaction Currency Code Not Provided | Cardholder Disputes | Retired (merged into 4834) |
| 4849 | Questionable Merchant Activity | Fraud | **Active** |
| 4850 | Installment Billing Dispute | Cardholder Disputes | Retired (merged into 4853) |
| 4853 | Cardholder Dispute | Cardholder Disputes | **Active** |
| 4854 | Cardholder Dispute — Not Elsewhere Classified | Cardholder Disputes | **Active** (U.S. only) |
| 4855 | Goods or Services Not Provided | Cardholder Disputes | Retired (merged into 4853) |
| 4857 | Card-Activated Telephone Transaction | Cardholder Disputes | Retired (merged into 4834) |
| 4859 | Services Not Rendered | Cardholder Disputes | Being merged into 4853/4834 |
| 4860 | Credit Not Processed | Cardholder Disputes | Retired (merged into 4853) |
| 4862 | Counterfeit Transaction — Magnetic Stripe | Fraud | **Active** |
| 4863 | Cardholder Does Not Recognize — Potential Fraud | Fraud | Retired in some regions |
| 4870 | Chip Liability Shift | Fraud | **Active** |
| 4871 | Chip/PIN Liability Shift | Fraud | **Active** |

**Universal merchant response window: 45 days** (acquirers may impose shorter internal deadlines of 20-30 days).
