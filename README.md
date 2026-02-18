# chargeback-ai

**Stop losing money to chargebacks you should be winning.**

A [Claude Code](https://docs.anthropic.com/en/docs/claude-code) plugin that gives you instant access to every card network's reason codes, tells you whether to fight or accept a dispute, and generates professional response packages ready for submission.

Works with **any payment processor** — Stripe, Shopify, Adyen, Braintree, Square, or direct acquiring relationships.

## Installation

```
/plugin marketplace add go-canonical/chargeback-ai
/plugin install chargeback-ai@chargeback-ai
```

Restart Claude Code after installing. That's it — four skills are now available in every session.

> **Note:** For some users, plugin skills won't appear when typing `/` in the autocomplete menu. Type the full command instead. Start with `/chargeback-ai:help` to see all available commands.

To check for updates:
```
claude plugin update chargeback-ai@chargeback-ai
```

---

## Skills

### `/chargeback-ai:help` — Getting Started

See all available commands with examples.

```
/chargeback-ai:help
```

---

### `/chargeback-ai:lookup` — Reason Code Reference

Instant lookup for any reason code or keyword across all card networks.

```
/chargeback-ai:lookup Visa 13.1
```

**Example output:**

```
### VISA 13.1 — Merchandise/Services Not Received

Category: Consumer Disputes
Response Deadline: 30 days

What this means: The cardholder claims they did not receive the
purchased merchandise or services.

Required Evidence:
- Proof of delivery (carrier tracking with delivery confirmation)
- Delivery address matching the AVS-verified address
- Description of merchandise or services provided

Compelling Evidence (improves win rate):
- Signed delivery confirmation or signature on file
- Photos of delivered package
- Communication with cardholder confirming receipt or delivery attempt
- GPS delivery confirmation from carrier

Strategy Tips:
- Delivery confirmation to the AVS-verified address is usually
  sufficient to win this dispute
- If shipped to a different address, provide proof the cardholder
  requested that address

Common Mistakes to Avoid:
- Submitting tracking numbers without actual delivery confirmation
- Missing the 30-day response deadline
```

You can also search by keyword — it finds matching codes across all networks:

```
/chargeback-ai:lookup fraud
/chargeback-ai:lookup not received
/chargeback-ai:lookup cancelled subscription
/chargeback-ai:lookup MC 4853
```

---

### `/chargeback-ai:analyze` — Fight or Accept?

Gives you a clear, reasoned recommendation on whether to fight a dispute based on your evidence and situation.

```
/chargeback-ai:analyze Visa 13.1, $89 order, have tracking with delivery signature
```

**Example output:**

```
## Recommendation: FIGHT

Reason Code: VISA 13.1 — Merchandise/Services Not Received
Dispute Amount: $89
Confidence: High

### Why Fight

You have signed delivery confirmation, which is the strongest possible
evidence for a "not received" dispute. Visa's own guidelines state that
delivery confirmation to the AVS-verified address is sufficient to
overturn this reason code.

### Key Factors

| Factor              | Status | Impact  |
|---------------------|--------|---------|
| Delivery tracking   | Have   | Helps   |
| Signature confirm.  | Have   | Helps   |
| AVS match           | Unknown| Verify  |

### If You Fight

Evidence to prioritize:
1. Signed delivery confirmation from carrier
2. Order details showing AVS-verified shipping address

Estimated win likelihood: High
Time investment: Low — have everything needed

### Next Steps

- Export the tracking page showing delivery + signature from FedEx
- Confirm the delivery address matches the billing/AVS address
- Submit within 30 days of the dispute notification
```

More examples:

```
/chargeback-ai:analyze MC 4837, $250, no 3D Secure, customer claims fraud
/chargeback-ai:analyze Amex FR2, $1200, have 3DS and IP logs
/chargeback-ai:analyze Discover UA, $45, digital goods, no delivery proof
```

---

### `/chargeback-ai:respond` — Full Response Package

Generates everything you need to submit a dispute response: a professional rebuttal letter, evidence checklist, organization guide, and network-specific submission tips.

```
/chargeback-ai:respond Visa 13.1, order #1234, $89, shipped FedEx with signature confirmation
```

**What you get:**

| Section | What it includes |
|---------|-----------------|
| **Rebuttal Letter** | Professional, ready-to-submit letter addressing the specific reason code. References each exhibit. 500-800 words. |
| **Evidence Checklist** | Table of required vs. compelling evidence, what you have, what's missing, and how to get it. |
| **Organization Guide** | Exact order to compile exhibits, formatting tips, file type recommendations. |
| **Submission Notes** | Network-specific instructions for how and where to submit. |

**Example rebuttal letter excerpt:**

```
Re: Dispute Case #CB-2024-78901
    Transaction Date: January 15, 2024
    Transaction Amount: $89.00
    Reason Code: Visa 13.1 (Merchandise/Services Not Received)

Dear Dispute Resolution Team,

We respectfully request reversal of the above-referenced chargeback.
The merchandise was delivered to and signed for at the cardholder's
verified billing address. The evidence below demonstrates that the
cardholder received the goods as described.

Exhibit A — FedEx Tracking & Delivery Confirmation
Tracking number 7489-2847-0193 confirms delivery on January 18, 2024
at 2:47 PM to the address on file. The package was signed for by
"J. Smith," matching the cardholder name.

Exhibit B — Order Confirmation & AVS Verification
...
```

---

## Coverage

117 reason codes across 5 networks, with evidence requirements, deadlines, and win strategies for each.

| Network | Codes | Response Window | Examples |
|---------|-------|-----------------|----------|
| **Visa** | 10.1–13.9 (24 codes) | 30 days | Fraud, not received, not as described, credit not processed |
| **Mastercard** | 4807–4999 (23 codes) | 45 days | Unauthorized, point-of-interaction error, cardholder disputes |
| **American Express** | A, C, F, P, R, FR, M series (23 codes) | 20 days | Fraud, authorization, processing errors, card member disputes |
| **Discover** | AA, AT, UA, etc. (22 codes) | 30 days | Fraud, authorization, consumer disputes, processing errors |
| **ACH Returns** | R01–R33 (25 codes) | Varies | Insufficient funds, unauthorized, account closed |

## Optional Integrations

If you have **Stripe MCP** or **Shopify MCP** connected to Claude Code, chargeback-ai automatically detects them and offers to pull dispute and order data directly. No configuration needed — just run any skill and it will ask if you want to pull data from your connected services.

## When to Use

| Scenario | Skill |
|----------|-------|
| "What commands are available?" | `/chargeback-ai:help` |
| "What does reason code 13.1 mean?" | `/chargeback-ai:lookup Visa 13.1` |
| "I got a chargeback — should I fight it?" | `/chargeback-ai:analyze` + your details |
| "I need to write a dispute response" | `/chargeback-ai:respond` + your details |
| "What evidence do I need for fraud chargebacks?" | `/chargeback-ai:lookup fraud` |
| "Customer says they didn't get the package" | `/chargeback-ai:lookup not received` |

## Requirements

- [Claude Code](https://docs.anthropic.com/en/docs/claude-code) v1.0.33 or later
- That's it. No API keys, no configuration, no external services required.

## Disclaimer

This plugin is for informational purposes only and does not constitute legal, financial, or professional advice. Chargeback rules and evidence requirements change frequently. Always verify current requirements with your payment processor or acquirer before submitting a dispute response. You are responsible for the accuracy of any information submitted.

## License

MIT

---

Built by [Canonical](https://www.usecanonical.com)
