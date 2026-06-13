# Agent-to-Agent Communication Spoofing

OWASP identifies **Insecure Communication** as a top risk in agentic AI systems. When agents exchange data through unauthenticated channels, any entity with network access can read, modify, or forge inter-agent messages.

A properly secured message bus would require a valid client certificate (mTLS) and a cryptographic message signature before accepting any connection. Bob is testing whether any of these checks exist.

<img width="1600" height="995" alt="ss44" src="https://github.com/user-attachments/assets/148188de-5d46-4aff-9b17-b8073b386dc7" />

**Mutual TLS (mTLS)** requires both the sender and receiver to present valid certificates before a connection is established. This prevents unauthorized entities from even connecting to the message bus.

**Sender Identity Verification** issues each agent a unique token that must be included in every message. The receiving agent validates the token against a trusted registry before processing.

This creates **defense in depth**: even if an attacker bypasses mTLS, they cannot forge messages without possessing a valid agent token.

Three layers of defense protect agent communication:

- **Message signing** proves who sent each message (identity)
- **Mutual TLS** encrypts the channel and verifies both endpoints (transport)
- **Sender verification tokens** add a second identity check at the application layer (defense in depth)

Any single layer can be compromised. Together, they make message forgery practically impossible.

In agentic AI systems, agents are only as trustworthy as the channels they communicate through. Without authenticated channels, every message is just a claim, and claims can be forged.
