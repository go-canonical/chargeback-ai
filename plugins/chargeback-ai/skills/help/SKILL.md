---
name: help
description: Use when the user asks what this plugin can do, needs help getting started with chargebacks, or asks about available commands. Shows all available skills with examples.
argument-hint: (no arguments needed)
---

# Chargeback AI — Help

Show the user what's available. Present the following exactly:

---

## 🛡️ Chargeback AI

Your chargeback and payment dispute assistant. Here's what I can do:

### Available Commands

| Command | What it does |
|---------|-------------|
| `/chargeback-ai:lookup` | Look up any reason code or search by keyword |
| `/chargeback-ai:respond` | Generate a full dispute response package |
| `/chargeback-ai:analyze` | Get a fight-or-accept recommendation |
| `/chargeback-ai:help` | Show this help menu |

### Quick Examples

**Look up a reason code:**
```
/chargeback-ai:lookup Visa 13.1
/chargeback-ai:lookup MC 4853
/chargeback-ai:lookup fraud
```

**Generate a dispute response:**
```
/chargeback-ai:respond Visa 13.1, order #1234, shipped via FedEx with signature
```

**Should I fight or accept?**
```
/chargeback-ai:analyze Visa 13.1, $89 order, have tracking with signature
```

### Supported Networks

Visa · Mastercard · Amex · Discover · ACH

### Tips

- You can also just ask me about chargebacks naturally — e.g., "what do I do about a fraud dispute on Visa?"
- If you have **Stripe** or **Shopify** MCP tools connected, I can pull dispute details directly from your account.

---

Do not add anything else to the response. Do not include the disclaimer for the help command.
