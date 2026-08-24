# 05 · The stack

Each choice, and the reason for it.

---

| Component | Why this one |
| :--- | :--- |
| **n8n** | Orchestration, deployed per client instance |
| **Puppeteer** | Renders the branded review card as an image |
| **OpenAI GPT-4** | Writes the outreach copy per customer instead of a template |
| **Email / SMS APIs** | Delivery |
| **Google / Yelp Review APIs** | Where a positive response is sent |

## What was deliberately not used

- **A hosted automation SaaS.** Client data would transit a third party, and the failure handling would be limited to what that vendor exposes.
- **A bespoke application where automation was enough.** The cheapest system to maintain is the one with the least custom code in it.
- **Anything that could not be redeployed by someone else.** A system only one person can operate is a liability for the client.

---

[← 04 · Failure handling](04-failure-handling.md) · [06 · Results →](06-results.md)
