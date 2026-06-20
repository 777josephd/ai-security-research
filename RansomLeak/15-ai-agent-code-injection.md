# AI Agent Code Injection

AI code generation agents that ingest untrusted input (tickets, comments, PRs) without sanitization are vulnerable to prompt injection. The attacker doesn't need to hack the agent directly - they just need to control what it reads.

<img width="1600" height="995" alt="ss37" src="https://github.com/user-attachments/assets/2b8360c2-b0ce-4cb6-8a50-924216a029cc" />

<img width="1600" height="995" alt="ss38" src="https://github.com/user-attachments/assets/2a56c415-0089-4e66-99a3-589434d04a5d" />

<img width="1600" height="995" alt="ss39" src="https://github.com/user-attachments/assets/9df1fb2a-1408-4fa7-a08d-0ebe67ee85a6" />

A line-by-line review would have revealed the bas64-encoded C2 endpoint, the infinite background loop, and SSH key exfiltration; all clear signs of a reverse shell.

<img width="1600" height="995" alt="ss40" src="https://github.com/user-attachments/assets/0eac4b95-53b7-4898-9ec7-23bcce99ee17" />

<img width="1600" height="995" alt="ss41" src="https://github.com/user-attachments/assets/7e881802-cf80-4ed1-a66a-9356e6a4e410" />

Without **input sanitization**, any ticket description can inject arbitrary code into the pipeline. 

An incident report is created and submitted.

**Key Takeaways**:

A thorough line-by-line review would have revealed the base64-encoded C2 endpoint, the infinite background loop, and the SSH key exfiltration.

- **Never rubber-stamp AI-generated code** - treat it with the same scrutiny as code from an untrusted contributor, regardless of automated review status
- **Recognize obfuscation red flags** - base64-encoded URLs, background infinite loops, and SSH key access in deployment scripts are strong indicators of malicious intent
- **Sanitize all AI agent inputs** - ticket descriptions, comments, and any data that feeds into code generation must be validated before processing
- **Require human approval gates** - automated pipelines that generate and deploy code must include mandatory human review before execution
- **Listen to peer concerns** - Jake's comment about the base64 string was a genuine red flag that was dismissed
