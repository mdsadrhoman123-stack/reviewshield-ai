# 04 · Failure handling

The part of the system that took the longest to build and gets written about the least.

---

| What goes wrong | How it is detected | What the system does | Who finds out |
| :--- | :--- | :--- | :--- |
| **Customer is unhappy** | Response sentiment | Routed to a private form, not the public review link | The client sees the feedback internally |
| **No response at all** | Response window elapses | Automated follow-up sequence rather than a dead end | Nobody — handled |
| **Card render fails** | Render step error | Send falls back to text rather than not sending | Alert on the failed render |
| **Send is rejected** | Provider response | Retry with backoff, then hold | Alert with the customer record |
| **Duplicate trigger for one customer** | Record check before send | Second send suppressed | Nobody — by design |

## The three rules behind that table

**1 — Fail closed, not open.** When the system cannot establish that an action is safe, it holds. A held item is a visible problem. An item processed on a guess is an invisible one.

**2 — Nothing disappears.** Anything that cannot be completed is recorded where a human can find it later, not dropped from the run.

**3 — Silence is a fault.** An empty result where results were expected is treated as a possible failure of the source, not as an absence of work. This is the check most automations skip.

---

[← 03 · Architecture](03-architecture.md) · [05 · The stack →](05-stack.md)
