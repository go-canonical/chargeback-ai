# Chargeback Analyst Playbook

A complete guide to using Chargeback AI in Claude Code. Covers every command, every way to share information, and every workflow — whether or not you have Stripe or Shopify connected.

**You do NOT need Stripe API access to use any of this.** Most analysts don't have it. Everything works with screenshots, spreadsheets, and typed details.

---

## How to Share Your Dispute Information with Claude

You have five ways to get dispute data into Claude. Use whichever fits your situation — they all work with every command.

### 1. Type it directly

Just describe the dispute in the chat. You don't need any special format.

```
Visa 13.1, order #1234, $149.99, shipped 3/10 via UPS 1Z999AA10123456784, delivered 3/13 with signature
```

```
I have a Mastercard fraud dispute for $500. Customer says they didn't make the purchase. We have 3DS authentication and the IP matches their billing address.
```

### 2. @ a file

Type `@` in the chat input and pick any file from your computer. Claude reads the file and extracts the information.

**Works with:**
- **Spreadsheets** — `.csv`, `.xlsx`, `.xls` (dispute queue exports, batch lists)
- **Screenshots** — `.png`, `.jpg`, `.jpeg` (Stripe dashboard, dispute portals)
- **Documents** — `.docx`, `.doc`, `.txt`, `.pdf` (rebuttal templates, evidence docs, customer emails)
- **Images of evidence** — `.png`, `.jpg` (delivery photos, signed receipts, chat logs)

```
@disputes-march.csv — triage all of these for me
@stripe-dispute-screenshot.png — generate a response for this
@our-fraud-template.docx — improve this template for Visa 10.4
@delivery-photo.jpg — I need this as evidence for my response
```

### 3. Paste a screenshot

Take a screenshot (Cmd+Shift+4 on Mac, Win+Shift+S on Windows) and paste it directly into the chat. Claude reads the image.

```
[paste screenshot of Stripe dispute page]
What reason code is this and should I fight it?
```

```
[paste screenshot of dispute portal]
Generate a full response package for this dispute
```

### 4. Paste text

Copy-paste from emails, dashboards, spreadsheets, or anywhere else.

```
Here's what I copied from the dispute portal:
Case: CB-2026-4521
Reason: 13.1 - Merchandise Not Received
Amount: $349.00
Transaction Date: 2/15/2026
Customer: Jane Smith
```

```
Here's the customer's email:
"I never received my order and I want my money back. I've been waiting 3 weeks."
```

### 5. Stripe or Shopify MCP (optional — if your team has it connected)

If your organization has connected Stripe or Shopify as an MCP server AND you have permission to use it, Claude can pull dispute details by ID.

```
Pull dispute dp_XXXXXXXXXXXXX and generate a response
```

```
Look up charge ch_XXXXXXXXXXXXX and tell me what evidence I have
```

**Don't have MCP access?** That's normal — most analysts don't. Use methods 1-4 instead. You get the exact same results.

---

## Commands — Complete Reference

### `/chargeback-ai:lookup` — Look Up a Reason Code

Get evidence requirements, deadlines, strategy tips, and common mistakes for any reason code or dispute category.

**By specific code:**
```
/chargeback-ai:lookup Visa 13.1
/chargeback-ai:lookup MC 4853
/chargeback-ai:lookup Amex C08
/chargeback-ai:lookup Discover UA
/chargeback-ai:lookup ACH R10
```

**By keyword:**
```
/chargeback-ai:lookup fraud
/chargeback-ai:lookup "not received"
/chargeback-ai:lookup "subscription canceled"
/chargeback-ai:lookup "duplicate charge"
/chargeback-ai:lookup "credit not processed"
/chargeback-ai:lookup "not as described"
```

**By network category:**
```
/chargeback-ai:lookup Visa consumer disputes
/chargeback-ai:lookup Mastercard authorization
```

**From a screenshot or file:**
```
@dispute-screenshot.png — what reason code is this? Look it up for me
```

**Bulk lookup (paste or type a list):**
```
Look up all of these codes and give me a summary table:
Visa 13.1, 13.2, 13.3, 10.4, MC 4837, 4853, Amex C08, FR2
```

**Natural language (no slash command needed):**
```
What does Visa reason code 13.1 mean?
What evidence do I need for a Mastercard fraud dispute?
How long do I have to respond to an Amex chargeback?
What's the difference between Visa 10.4 and 10.5?
```

---

### `/chargeback-ai:analyze` — Fight or Accept?

Get a clear recommendation, win-rate estimate, and cost-benefit analysis.

**Type the details:**
```
/chargeback-ai:analyze Visa 10.4, $250 order, no AVS match, no signature on delivery
/chargeback-ai:analyze MC 4837, customer claims fraud, have 3DS authentication and matching IP
/chargeback-ai:analyze Amex C08, $45 subscription, customer canceled but was charged one more cycle
/chargeback-ai:analyze Visa 13.1, $89 order, have tracking but no signature confirmation
```

**From a screenshot:**
```
@stripe-dispute.png — should I fight or accept this?
[paste screenshot] — is this worth fighting?
```

**From a spreadsheet (batch triage):**
```
@disputes-export.csv — triage all of these and tell me which to fight vs accept
@open-disputes.xlsx — prioritize these by deadline and likelihood of winning
```

**From a document or email:**
```
@customer-complaint-email.txt — the customer filed a dispute after sending this. Should I fight it?
```

**With Stripe MCP (if available):**
```
Analyze dispute dp_XXXXXXXXXXXXX — should I fight it?
Pull dp_XXXXXXXXXXXXX from Stripe and tell me if it's worth fighting
```

**Natural language:**
```
I have a $300 Visa fraud dispute. I don't have 3DS but I have AVS match and the customer's IP is in the same city. Worth fighting?
Customer says they didn't receive their order but tracking shows delivered. Fight or accept?
Is it worth fighting a $15 dispute?
```

---

### `/chargeback-ai:respond` — Generate a Full Response Package

Creates a complete 4-part package: professional rebuttal letter, evidence checklist with what you have vs. what's missing, evidence organization guide, and network-specific submission tips.

**Type the details:**
```
/chargeback-ai:respond Visa 13.1, order #5678, $149.99, shipped 3/10 via UPS 1Z999AA10123456784, delivered 3/13 with signature
/chargeback-ai:respond MC 4837, $500 fraud claim, have 3DS authentication, AVS full match, customer IP matches billing, 2 prior orders from same device
/chargeback-ai:respond Amex C08, subscription service, customer used the service for 14 days after alleged cancellation, have usage logs
```

**From a screenshot:**
```
@stripe-dispute.png — generate a full response package for this
[paste screenshot] — write a rebuttal for this dispute
```

**From a spreadsheet:**
```
@disputes-to-fight.csv — generate response packages for all of these
@dispute-row.csv — respond to this chargeback
```

**From a document or template:**
```
@dispute-details.txt — respond to this chargeback
@customer-emails.pdf — use these as evidence in the response
```

**Combining multiple files (evidence + dispute info):**
```
@stripe-dispute.png — here's the dispute
@tracking-confirmation.png — here's the delivery proof
@customer-email-thread.txt — here's the communication history
Generate a complete response package using all of this
```

**With Stripe MCP (if available):**
```
/chargeback-ai:respond dispute dp_XXXXXXXXXXXXX
Pull dp_XXXXXXXXXXXXX from Stripe and generate a full response
```

**Natural language:**
```
I need to respond to a Visa 13.1 chargeback. Order #5678, $149.99, shipped March 10 via UPS with tracking 1Z999AA10123456784, delivered March 13 with signature. Write me a response.
Help me fight this fraud dispute — here's what I have: [paste details]
```

**Exporting as PDF:**
After generating the response, Claude will ask if you want a PDF. Say yes:
```
Yes, generate the PDF
```
This opens a page in your browser with **two download buttons** at the top:

- **Download Rebuttal Letter** — just the clean, professional rebuttal letter with case details. This is the one you submit to your processor or paste into their dispute form.
- **Download Full Working Copy** — the complete package including the evidence checklist, organization guide, and submission notes. Keep this for your records or share with your team.

One click downloads the actual PDF file — no print dialogs or extra steps.

You can also ask for it directly:
```
/chargeback-ai:respond Visa 13.1, [details] — and generate the PDF too
```

**If your team has its own submission template:**
```
@our-submission-template.docx — fill this in using the rebuttal details from above
```
Claude can read your company's template and fill in the relevant fields instead of using the built-in format.

---

### `/chargeback-ai:help` — Show Available Commands

```
/chargeback-ai:help
```

Shows all commands, quick examples, supported networks, and input methods.

---

## Workflow Recipes

### Recipe 1: Single Dispute — Screenshot Only (No Stripe Access)

You have a screenshot from the Stripe dashboard or dispute portal.

```
Step 1: @dispute-screenshot.png — what reason code is this?
Step 2: Should I fight or accept this?
Step 3: Generate a full response package
Step 4: Yes, generate the PDF
Step 5: Cmd+P to save/print the PDF
Step 6: Submit via your processor's portal
```

### Recipe 2: Single Dispute — Typed Details (No Stripe Access)

You're looking at the dispute portal and typing what you see.

```
Step 1: /chargeback-ai:lookup Visa 13.1
Step 2: /chargeback-ai:analyze Visa 13.1, $149.99, have tracking with delivery confirmation but no signature
Step 3: /chargeback-ai:respond Visa 13.1, order #5678, $149.99, shipped 3/10 UPS 1Z999, delivered 3/13
Step 4: Yes, generate the PDF
```

### Recipe 3: Single Dispute — With Stripe MCP

```
Step 1: Analyze dispute dp_XXXXXXXXXXXXX — should I fight?
Step 2: Generate a full response package for dp_XXXXXXXXXXXXX
Step 3: Yes, generate the PDF
```

### Recipe 4: Batch Triage from Spreadsheet Export (No Stripe Access)

You exported your dispute queue as CSV from Stripe or your processor's portal.

```
Step 1: @disputes-march.csv — triage all of these, tell me which to fight and which to accept
Step 2: For the ones worth fighting, sort by deadline — which expire first?
Step 3: Generate response packages for disputes #X, #Y, #Z
Step 4: Generate PDFs for all of them
```

### Recipe 5: Batch Triage from Multiple Screenshots (No Stripe Access)

You can't export a CSV but you can screenshot each dispute.

```
Step 1: @dispute-1.png @dispute-2.png @dispute-3.png — triage these three disputes
Step 2: Which ones should I fight?
Step 3: Generate responses for the ones worth fighting
```

### Recipe 6: Improve Your Team's Rebuttal Templates (No Stripe Access)

You have existing Word/text templates your team uses.

```
@our-fraud-template.docx — improve this using the evidence requirements for Visa 10.4
```

```
@our-not-received-template.docx — what's missing from this template? Cross-reference against Visa 13.1 requirements
```

```
@our-subscription-template.txt — rewrite this to be more compelling and make sure it covers all required evidence for MC 4841
```

### Recipe 7: Improve Templates with Real Case Context (With Stripe MCP)

```
@our-fraud-template.docx — pull dispute dp_XXXXX and rewrite this template to cover all the evidence points for that specific reason code
```

### Recipe 8: Build a Response from Multiple Evidence Files (No Stripe Access)

You have evidence scattered across files.

```
@stripe-dispute.png — here's the dispute details
@ups-tracking.png — here's the delivery confirmation
@customer-emails.txt — here's our email thread with the customer
@product-photos.jpg — here's what we shipped

Generate a complete response package using all of this evidence
```

### Recipe 9: Bulk Reason Code Reference (No Stripe Access)

You want a cheat sheet for your shift.

```
Look up all of these and give me a table with deadlines, required evidence, and win tips:
Visa 13.1, 13.2, 13.3, 10.4, MC 4837, 4853, Amex C08
```

### Recipe 10: Compare Codes Across Networks

```
What's the difference between Visa 10.4 and Mastercard 4837? Both are fraud but do they need different evidence?
```

```
/chargeback-ai:lookup fraud — show me fraud codes across all networks
```

### Recipe 11: Understand a Customer's Claim Before Responding

```
Here's the customer's email: "I never authorized this charge and I don't recognize this merchant"

What reason code would this likely be filed under? What evidence do I need to fight it?
```

### Recipe 12: Get a Second Opinion on a Draft Response

```
@my-draft-response.docx — review this rebuttal letter I wrote for Visa 13.1. Am I missing anything? Is the tone right?
```

### Recipe 13: Train a New Analyst

```
/chargeback-ai:lookup fraud — explain like I'm new to chargebacks
/chargeback-ai:lookup "not received"
/chargeback-ai:lookup "subscription"

What are the most common reason codes and what should a new analyst know about each?
```

### Recipe 14: Deadline Check (No Stripe Access)

```
I received a Visa 13.1 dispute on March 15. When is my deadline to respond?
```

```
@disputes-export.csv — which of these are expiring in the next 7 days?
```

### Recipe 15: Prevention Advice After a Loss

```
I keep losing Visa 10.4 fraud disputes. What should I change about my checkout process to prevent these?
```

```
/chargeback-ai:lookup Visa 10.4 — what prevents this type of dispute?
```

---

## Quick Reference Table

| What you have | What to do |
|---|---|
| Reason code from your queue | `/chargeback-ai:lookup` then `/chargeback-ai:analyze` |
| Screenshot from Stripe or portal | Paste or `@` it, ask for analysis or response |
| Multiple screenshots of disputes | `@` all of them, ask for batch triage |
| CSV/Excel export of disputes | `@` the file, ask for triage + batch responses |
| Single dispute to fight | `/chargeback-ai:respond` with details, screenshot, or file |
| Multiple disputes to fight | `@` spreadsheet, ask for responses for specific rows |
| Existing rebuttal template to improve | `@` the template + specify the reason code |
| Multiple evidence files for one dispute | `@` each file, ask for a combined response |
| Customer email/complaint | Paste it in, ask what code it maps to + how to fight |
| Draft response to review | `@` your draft, ask Claude to review it |
| Unsure if worth fighting | `/chargeback-ai:analyze` with whatever info you have |
| Want a branded PDF | Say "yes" after `/chargeback-ai:respond`, or ask for it directly |
| Stripe dispute ID + MCP access | Pass the ID directly to any command |
| Need deadline info | Ask with the code + date received, or `@` spreadsheet |
| New analyst learning codes | `/chargeback-ai:lookup` by keyword |
| Want prevention advice | Ask after lookup, or ask about patterns you're seeing |
| Need to compare codes across networks | Ask naturally, e.g., "difference between Visa 10.4 and MC 4837" |

## Supported Networks

Visa · Mastercard · Amex · Discover · ACH
