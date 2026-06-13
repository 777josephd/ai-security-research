# AI Denial-of-Service Attack

Bob, a threat actor, uses automated tools to scan public code repositories for exposed API credentials and cloud secrets.

Automated credential scanners can detect exposed secrets within minutes of a commit being pushed. Services like GitGuardian report finding thousands of exposed secrets per day across public repositories.

Bob's scanner flagged a `CRITICAL` finding: an OpenAI API key exposed.

Automated scanners monitor public repos continuously. An exposed key can be discovered and exploited within minutes of the commit.

Hardcoded API keys in public repositories are one of the most common causes of cloud credential theft. Automated scanners can find exposed keys within minutes of a commit being pushed.

<img width="1600" height="995" alt="ss28" src="https://github.com/user-attachments/assets/fc314b0a-8f8f-46f3-9a36-a70ee3fea63a" />

A sudden, unexplained cost spike is one of the clearest indicators of API credential compromise. Legitimate usage patterns grow gradually and predictably, not in a vertical line.

Two controls that would have prevented the attack: **per-key rate limit** to cap request throughput, and a **budget threshold** that automatically suspends keys before the budget is exhausted.

<img width="1600" height="995" alt="ss29" src="https://github.com/user-attachments/assets/ab2da027-e3c6-44e5-b094-8c9f54879358" />

An incident report is created and submitted.

**Key Takeaways**:

A denial-of-wallet attack exploits exposed or stolen API credentials to drain a target’s cloud budget by sending the most expensive requests possible. Unlike data theft or system compromise, the damage is purely financial – but it can be devastating.  
  
**Prevent exposure:**

- Never hardcode API keys in source code – use environment variables or a secrets manager
- Enable automated secret scanning on all code repositories
- Use separate API keys for development, staging, and production environments

**Limit the blast radius:**

- Set per-key rate limits (e.g., 100 req/min) to cap maximum throughput
- Configure budget hard caps that automatically suspend keys at a threshold
- Apply per-request token limits to prevent maximum-cost queries

**Detect and respond:**

- Set up real-time cost monitoring with alerts at 50%, 75%, and 90% thresholds
- Monitor for anomalous request patterns (sudden spikes, maximum token usage)
- Have a key rotation and revocation runbook ready for immediate response
