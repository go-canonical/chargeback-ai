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

### How to Give Me Your Dispute Info

You have several ways to share dispute details with me:

| Method | How | Example |
|--------|-----|---------|
| **Type it** | Just describe the dispute in chat | `Visa 13.1, order #1234, shipped with tracking` |
| **`@` a file** | Type `@` and pick a file from your computer | `@disputes.csv` or `@screenshot.png` |
| **Paste a screenshot** | Drag or paste an image into the chat | Screenshot of Stripe dashboard, dispute portal, etc. |
| **Stripe/Shopify MCP** | If connected, I pull details by ID | `dispute dp_XXXXXXXXXXXXX` |

You do **not** need Stripe or Shopify API access — everything works with typed details, files, or screenshots.

### Tips

- You can also just ask me about chargebacks naturally — e.g., "what do I do about a fraud dispute on Visa?"
- Use `@` to point me at CSV exports, Excel files, screenshots, PDFs, or rebuttal templates — I can read them all
- If you have **Stripe** or **Shopify** MCP tools connected, I can pull dispute details directly from your account

---

Do not add anything else to the response. Do not include the disclaimer for the help command.
