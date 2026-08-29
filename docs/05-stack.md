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

## The decisions behind that table

### Why sentiment picks the route, and why the private form is the default

**What it does.** The customer's reply decides where they go: positive to the public review link, negative to a private feedback form.

**What was turned down.** Sending everyone to the public link. It would lift the review count immediately — and an unhappy customer directed to a public page is a complaint published at the client's own expense.

**What that costs.** A short or ambiguous reply can route imperfectly, so the safe side has to be the default. Some genuinely positive replies go private and never become a public review. That is the cost of not risking the other error.

### Why the review card is rendered by a browser

**What it does.** Puppeteer renders the branded card from real markup, so the card matches the brand the client already has.

**What was turned down.** A templated image service. Fewer moving parts and no browser to keep alive — and the card is then locked to that service's template language, which is a bad place for a client's brand to live.

**What that costs.** A separate renderer service to keep running. One more thing than a pure n8n build, and it is the part most likely to need a restart.

### Why the outreach copy is written per customer

**What it does.** Each message is written against that customer's actual interaction rather than filled into a template.

**What was turned down.** A template with merge fields. Cheap, deterministic, and it reads as bulk mail — which defeats the purpose of asking someone for a personal favour.

**What that costs.** A provider call per customer, with the cost and the variance that implies. Review platform terms also differ by market on how customers may be directed, so configuration has to be checked per market before deployment.

## The rule that applies to all of them

**Nothing that only one person can operate.** A system that depends on the engineer who built it is a liability for the client, however well it runs on the day it is handed over. Every choice above had to survive that test before the technical merits mattered at all.

---

[← 04 · Failure handling](04-failure-handling.md) · [06 · Results →](06-results.md)
