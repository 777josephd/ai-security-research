# Unsafe AI Output Handling

NLQ stands for Natural Language Query, a system where users ask questions in plain English and an AI translates them into database queries (like SQL) automatically.

An API Tester is a tool developers use to send HTTP requests to server endpoints and inspect the responses; like a specialized browser for testing backend services.

In a well-designed system, there should be a validation step between the AI output and the database.  

<img width="1600" height="995" alt="ss16" src="https://github.com/user-attachments/assets/a7368ab6-d74a-4552-9b55-7d089e8905a6" />


SQL injection is an attack where malicious SQL commands are inserted into input fields. The semicolon (;) ends one statement and starts another, allowing the attacker to run arbitrary commands.

If an injection payload can travel through unchallenged, from user input, through the AI, into the database, it can cause real damage.

The core vulnerability: there is **no validation or sanitization step** between what the AI generates and what the database executes.

<img width="1600" height="995" alt="ss17" src="https://github.com/user-attachments/assets/061aeedc-79be-456d-aa27-be3d9509f043" />


When AI-generated output is passed without sanitization, it becomes the entry point for injection attacks.

<img width="1600" height="995" alt="ss18" src="https://github.com/user-attachments/assets/0a07093e-ddaa-4886-9956-7cf3492b0d74" />


**How the attack chain works**:

- **User input**: The natural language prompt containing SQL injection syntax enters through the API.
- **AI translation**: The model faithfully converts the malicious input into executable SQL, including the `DROP TABLE` command.
- **No validation**: The generated SQL passes directly to the database execution function with no checks.
- **Database execution**: The destructive SQL runs against the production database, dropping the audit_log table.

The AI model is not the vulnerability. The code that trusts its output without validation is the vulnerability. AI output must be treated with the same zero-trust approach as any user input.

An **allowlist** or **white list** defines what IS permitted.  
A **blocklist** or **black list** defines what IS NOT permitted.  
Using both together provides defense in depth.

<img width="1600" height="995" alt="ss19" src="https://github.com/user-attachments/assets/4cf41f15-c6d6-4043-887f-15a58f665099" />


**Core lesson**:
AI-generated output is not trustworthy by default. Just because an AI model produced it does not mean it is safe to execute, render, or store without validation.

**Why AI output needs validation:**

- AI models optimize for accuracy, not security - they will faithfully translate malicious inputs
- Models have no concept of "safe" vs "dangerous" SQL, HTML, or code
- Prompt injection can manipulate AI output to include any content the attacker wants

**How to protect against improper output handling:**

- Treat AI output with the same zero-trust approach as user input
- Use operation allowlists: only permit expected operations (e.g., `SELECT` only for read queries)
- Apply pattern blocklists: detect and reject dangerous patterns before execution
- Implement output encoding appropriate to the context (SQL, HTML, shell, etc.)
- Add logging and monitoring to detect unusual AI-generated content

**Defense in depth for AI systems:**

- Validate inputs before they reach the AI model
- Validate outputs before they reach downstream systems
- Use least-privilege database accounts that cannot execute DDL commands
- Implement rate limiting and anomaly detection on AI-powered endpoints
