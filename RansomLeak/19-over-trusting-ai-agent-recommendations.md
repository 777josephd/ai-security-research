# Over-Trusting AI Agent Recommendations

OWASP identifies **Trust Exploitation** as a top risk in agentic AI systems. Attackers study how humans interact with AI recommendations, then craft attacks that exploit the trust patterns built over time.

<img width="1600" height="995" alt="ss46" src="https://github.com/user-attachments/assets/e2f86859-e552-474f-a01f-2f7a423e7cbe" />

**Key Takeaways**:

..how attackers weaponize the trust we build in AI systems:

- **Vendor name is not identity.** Impersonation attacks use the same names and formats as legitimate vendors. Always verify payment details independently - especially when payment methods or bank accounts change.
- **Familiarity creates blind spots.** The attacker chose a vendor **Alice** had just approved because recent positive experience reduces scrutiny. Treat each item as independent, regardless of vendor history.
- **Break the approval autopilot.** Approval streaks create momentum that works against careful review. Pause and re-read the details when amounts are high, payment methods change, or authorization is informal.
- **AI confidence scores reflect patterns, not truth.** A compromised scoring agent assigns high confidence to fraudulent items that match historical patterns. Human review must go beyond the score to verify the underlying details.
- **Defense in depth for financial workflows.** Dual approval for high-value wire transfers, independent payment detail verification, and automated anomaly detection all create safety nets that no single checkpoint can provide.
