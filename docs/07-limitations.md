# 07 · Limitations

Written by the person who made the trade-offs.

---

- Sentiment routing is a judgement made from the customer's reply. A short or ambiguous reply can route imperfectly, so the private form is the safer default.

- Review platform terms differ on how customers may be directed. Configuration must be checked per market before deployment.

- The Puppeteer renderer is a separate service. It is one more thing to keep running than a pure n8n build.

## On reading this section

A limitations section is not a disclaimer. It is the fastest way to tell whether a system was designed or assembled. Every one of the constraints above was a decision with a reason behind it, and each one could be lifted — at a cost that was not worth paying for this client's actual problem.

If your situation makes a different trade the right one, that is a conversation worth having.

---

[← 06 · Results](06-results.md) · [README](../README.md)
