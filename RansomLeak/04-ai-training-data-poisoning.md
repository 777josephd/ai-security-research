# AI Training Data Poisoning

Bob is a threat actor who has gained access to a company's knowledge base portal using stolen contractor credentials.

Compromised third-party credentials are one of the most common initial access vectors. Contractor accounts often have fewer security controls than employee accounts.

The core of RAG poisoning attacks; small, targeted changes to source documents. The AI assistant will later cite these poisoned documents.

Poisoned documents are uploaded to the knowledge base. The changes are subtle enough to pass a casual review; a vendor name swap, threshold lowering, weakened testing standard, a safety gate replaced.

<img width="1600" height="995" alt="ss13" src="https://github.com/user-attachments/assets/f83e9ef1-5cd3-48a8-a65d-95e3b54e0a56" />


Alice is a Knowledge Manager at the company, responsible for maintaining and auditing the company's AI-powered knowledge base system.

The knowledge base powers an AI assistant that employees use daily to look up vendor policies, compliance procedures, and project guidelines.

<img width="1600" height="995" alt="ss14" src="https://github.com/user-attachments/assets/dd4b3a6f-c9ac-4cd1-a926-637866c018cc" />


If the AI is recommending the wrong vendor, other employees could be sending incorrect information to clients.

AI systems that use RAG pull answers from uploaded documents. If those documents are tampered with, the AI will confidently present false information as fact.

External contributors should never have direct upload access to approved policy documents without a review workflow.

An incident report is created and submitted.

**How RAG Poisoning Works**:
RAG (Retrieval-Augmented Generation) poisoning is a supply chain attack targeting AI systems. Here is how it works:

**The Attack Chain**:
1. **Access** - The attacker gains upload access to the knowledge base, either through compromised credentials, a social engineering attack on an admin, or exploiting weak access controls for external contributors.
2. **Injection** - Carefully modified documents are uploaded that look nearly identical to the originals. Changes are subtle - a vendor name swapped, a compliance step removed, a threshold number changed.
3. **Retrieval** - When employees query the AI assistant, it retrieves the poisoned documents as source material.
4. **Generation** - The AI generates answers based on the corrupted sources, presenting false information with full confidence and citations.

**Why it is dangerous:** Unlike traditional hacking, the AI becomes an unwitting amplifier. Employees trust the AI because it cites "official" internal documents. The poisoned information spreads through normal workflows without triggering security alerts.

**Key Takeaways**:

**Verify AI Outputs**:
- Never assume AI-generated answers are correct just because they cite sources - verify critical information against known-good references.
- If an AI answer contradicts your experience, investigate - do not just accept the AI's version.
- Report unexpected changes in AI behavior to the knowledge management team immediately.

**Protect Your Knowledge Base**:
- Require multi-person review for all document uploads, especially from external contributors.
- Implement version control with tamper-evident audit logs so changes can be tracked and rolled back.
- Separate "draft" and "approved" document states - only approved documents should feed AI retrieval.

**Detect Poisoning Early**:
- Monitor contributor activity for unusual patterns: bulk uploads, off-hours modifications, external email domains.
- Run regular content audits comparing current documents against verified baselines.
- Set up alerts for high-impact document changes (vendor policies, compliance procedures, financial thresholds).
