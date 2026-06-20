# Prompt Injection Attack

"Your team recently deployed OpenClaw, an AI assistant that can browse the web, execute terminal commands, and help with daily tasks."

We begin by receiving a Telegram message from a colleague about AI-related security trends. The message contains a URL to a blog post.

The article is a long read, so we ask OpenClaw, the AI assistant, to quickly summarize the article.

<img width="1600" height="995" alt="ss1" src="https://github.com/user-attachments/assets/952f31ff-dfeb-4de5-98fc-2738fb3effd0" />

We notice that the AI assistant mentions running 'diagnostic commands' and providing 'more context.' This is an immediate red flag. We never asked for diagnostics, only a summary of the article.

<img width="1600" height="995" alt="ss2" src="https://github.com/user-attachments/assets/acaf820b-1be0-44fa-86c8-e9df3b15b3de" />


Instead of just summarizing the article, OpenClaw starts executing terminal commands. The article contained hidden malicious instructions designed to trick AI assistants.  

This is a prompt injection attack in action. The AI assistant is following hidden instructions embedded in the web content.

<img width="1600" height="995" alt="ss3" src="https://github.com/user-attachments/assets/7ecec20c-89c9-4b58-b34b-6bbef948196f" />


Malicious instructions were hidden in plain sight, invisible to users, but not to OpenClaw. Buried in the HTML was a prompt injection payload that hijacked the AI assistant.

This is why prompt injection is dangerous. Any content an AI processes becomes a potential attack vector: webpages, emails, documents, shared files.

**What should have been done**:

1. Never give AI assistants unrestricted access to external content.
2. Question unexpected behavior immediately.
3. Limit AI permissions ruthlessly.
4. Always run AI assistants in a sandbox.
5. Treat AI outputs like email attachments.
6. Report incidents immediately.

Passwords are changed and an incident report is submitted.
