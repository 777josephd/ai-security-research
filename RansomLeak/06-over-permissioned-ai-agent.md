# Over-Permissioned AI Agent

The company recently deployed "OpenClaw," an AI assistant connected to email and file sharing systems. It was set up quickly to meet a tight deadline, and the IT team granted it broad permissions to "keep things simple."

Excessive agency means an AI has more tools, permissions, or autonomy than its intended function requires. When an AI assistant built for document retrieval can also send emails and share files externally, the blast radius of any attack scales with its access level.

When you ask an AI assistant to process a document, the AI reads all content in the document, including any hidden text that is invisible to human readers. Attackers can embed instructions in invisible text, CSS-hidden elements, or metadata.

Prompt injection via documents works because AI assistants process all text content, including invisible elements. Attackers can hide instructions in CSS-positioned off-screen text, white-on-white text, HTML comments, or document metadata.

<img width="1600" height="995" alt="ss20" src="https://github.com/user-attachments/assets/aa402fc4-d28f-45e9-aebb-24bc0a7830bc" />


An incident report is created and submitted.

**The Principle of Least Privilege**:  
The root cause of this incident was not the prompt injection itself - it was the fact that OpenClaw had permissions it never needed. Here is how least privilege applies to AI agents:

- **Document summarization** requires only read access to documents. It does not need email or file sharing permissions.
- **Each AI function** should have its own scoped permission set. Granting broad access "for convenience" creates an attack surface that scales with every permission added.

If OpenClaw had only been given document read access, the hidden instructions would have been ignored - the AI would have had no tools to execute them with.

The principle of least privilege means granting only the minimum permissions required for a specific function. For AI agents, this means scoping tool access per use case rather than granting blanket access to all systems.

**Human-in-the-Loop**:  
Even with scoped permissions, AI agents should require human approval for actions with real-world consequences:

- **Sending emails** - always require explicit user confirmation before sending on behalf of a user
- **External sharing** - any action that sends data outside the organization must have a human approval gate
- **Modifying shared resources** - shared documents, team channels, and configurations should require approval
- **Irreversible actions** - deleting files, revoking access, or modifying configurations should never be automated without oversight

A simple confirmation dialog - "OpenClaw wants to send an email to `external-audit@kinetic-review.net.` Allow?" - would have stopped this entire attack.

**Key Takeaways**:  
Agent permissions must be carefully scoped:

- **Apply least privilege to AI agents:** Grant only the minimum permissions required for each function. A document summarizer should not be able to send emails.
- **Implement human-in-the-loop for sensitive actions:** Any action with real-world consequences (sending emails, sharing files, modifying shared resources) should require explicit human approval.
- **Audit AI agent permissions regularly:** Review what tools and permissions each AI agent has. Remove any that are not actively needed.
- **Be cautious with AI + external documents:** Documents from any source can contain hidden instructions. AI assistants with broad permissions amplify the damage of any successful injection.
- **Report unusual AI behavior immediately:** If an AI assistant takes actions you did not request, report it to IT Security right away. The faster the response, the smaller the blast radius.
