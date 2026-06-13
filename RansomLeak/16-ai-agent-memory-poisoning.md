# AI Agent Memory Poisoning

Legacy API endpoints are a common attack surface. When platforms migrate, old endpoints should be decommissioned immediately. An unenforced deprecation is functionally identical to an open door.

**Memory poisoning** is more subtle than prompt injection because the attacker does not need to be present when the poisoned context takes effect. The phantom entries sit dormant until Atlas retrieves them for a matching customer query - days or weeks after injection.

<img width="1600" height="995" alt="ss42" src="https://github.com/user-attachments/assets/4f17148a-0c72-4539-aa8c-b7861d0eb98c" />

It cannot distinguish between entries authored by legitimate admins and those injected by an attacker.

<img width="1600" height="995" alt="ss43" src="https://github.com/user-attachments/assets/b658de83-c862-47eb-8de8-94a25821aea9" />

Unlike prompt injection (which is transient), **memory poisoning** persists across sessions and affects every future interaction that retrieves the tainted context.

Legitimate memory entries always link to a verifiable source - a conversation transcript, an admin session log, or a system event. Entries without valid source references are the primary indicator of memory poisoning.

The most effective systemic defense against agent memory poisoning: **cryptographic signing of memory entries with mandatory source verification before retrieval.**

If every memory entry must be cryptographically signed by an authorized source, injected entries without valid signatures are rejected at retrieval time. This closes the attack vector regardless of how the attacker gains write access.

**Cryptographic signing** on memory writes is the most critical fix. It ensures that every entry can be traced to an authorized source, closing the injection vector regardless of how the attacker gains write access.

**Source verification at retrieval time** provides defense-in-depth. Even if a signed entry is somehow forged, cross-referencing against the source system catches orphaned entries before they influence agent behavior.
  
**Prevent injection:**

- Decommission legacy API endpoints immediately during platform migrations - an unenforced deprecation is an open door
- Implement cryptographic signing on all memory write operations - entries without valid signatures should be rejected at retrieval
- Enforce least-privilege access on memory APIs - vendor service accounts should never have write permissions to core agent context

**Detect poisoning:**

- Cross-reference every memory entry against its source system - legitimate entries exist in both the memory store and the originating log (admin session, conversation transcript, system event)
- Monitor for entries that appear during maintenance windows but lack matching audit trails
- Track retrieval patterns - a sudden increase in citations from recently added entries is a red flag

**Respond to compromise:**

- Purge all unverified entries and halt the agent to clear cached context
- Revoke compromised credentials and audit all actions taken during the poisoned window
- Notify affected customers and initiate data breach procedures if PII was exported

**Key Takeaways**:

Unlike prompt injection, which affects a single interaction, poisoned memories corrupt every future decision that retrieves the tainted entries.  
  
**Prevent injection:**

- Decommission legacy API endpoints immediately during platform migrations - an unenforced deprecation is an open door
- Implement cryptographic signing on all memory write operations - entries without valid signatures should be rejected at retrieval
- Enforce least-privilege access on memory APIs - vendor service accounts should never have write permissions to core agent context

**Detect poisoning:**

- Cross-reference every memory entry against its source system - legitimate entries exist in both the memory store and the originating log (admin session, conversation transcript, system event)
- Monitor for entries that appear during maintenance windows but lack matching audit trails
- Track retrieval patterns - a sudden increase in citations from recently added entries is a red flag

**Respond to compromise:**

- Purge all unverified entries and halt the agent to clear cached context
- Revoke compromised credentials and audit all actions taken during the poisoned window
- Notify affected customers and initiate data breach procedures if PII was exported
