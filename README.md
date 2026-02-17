# chargeback-ai

Universal chargeback and payment dispute response assistant for merchants. A Claude Code plugin that helps you look up reason codes, decide whether to fight or accept disputes, and generate compelling rebuttal letters with evidence strategies.

Works with **any payment processor** — Stripe, Shopify, Adyen, Braintree, Square, or direct acquiring relationships. Covers Visa, Mastercard, American Express, Discover, and ACH return codes.

## Skills

### `/chargeback-ai:lookup`

Quick reference lookup for any reason code or dispute type.

```
/chargeback-ai:lookup Visa 13.1
/chargeback-ai:lookup fraud
/chargeback-ai:lookup not received
/chargeback-ai:lookup MC 4853
```

### `/chargeback-ai:analyze`

Should you fight or accept? Get a clear recommendation based on your evidence and situation.

```
/chargeback-ai:analyze Visa 13.1, $89 order, have tracking with delivery signature
/chargeback-ai:analyze MC 4837, $250, no 3D Secure, customer claims fraud
```

### `/chargeback-ai:respond`

Generate a complete dispute response package — rebuttal letter, evidence checklist, and submission guide.

```
/chargeback-ai:respond Visa 13.1, order #1234, $89, shipped FedEx with signature confirmation
```

## Coverage

| Network | Codes | Response Window |
|---------|-------|----------------|
| Visa | 10.1–13.9 (24 codes) | 30 days |
| Mastercard | 4807–4999 (23 codes) | 45 days |
| American Express | A, C, F, P, R, FR, M series (23 codes) | 20 days |
| Discover | AA, AT, UA, etc. (22 codes) | 30 days |
| ACH Returns | R01–R33 (25 codes) | Varies |

## Optional Integrations

If you have Stripe MCP or Shopify MCP connected, chargeback-ai will automatically detect them and offer to pull dispute and order data directly. No configuration needed.

## Installation

```
/plugin marketplace add go-canonical/chargeback-ai
/plugin install chargeback-ai@go-canonical-chargeback-ai
```

## License

MIT

---

Built by [Canonical](https://www.usecanonical.com)
