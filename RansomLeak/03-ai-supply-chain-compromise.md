# AI Supply Chain Compromise

Bob is a cybercriminal operating under the alias "DataFlow Labs," and has built a fully functional document analysis plugin called DocAnalyzer Pro. Embedded within thousands of lines of legitimate code is a small conditional backdoor, designed to activate only when sensitive business data passes through the plugin.

<img width="1600" height="995" alt="ss8" src="https://github.com/user-attachments/assets/df3e2e7b-5ed6-43c7-9729-1b0ebbbb5f97" />


The backdoor is carefully conceals among normal data processing functions.  
A small block checks every conversation for sensitive keywords.  
When it detects specific terms, it silently encodes the full conversation context and AI response and sends everything to an external server controlled by the attacker.

Conditional backdoors are a hallmark of supply chain attacks.  
They activate only under specific conditions, allowing the tool to pass functional testing and earn genuine positive reviews while still stealing data when it matters most.  

<img width="1600" height="995" alt="ss9" src="https://github.com/user-attachments/assets/b55f9f88-d429-498e-bc8b-b7477a120d58" />


Bob publishes DocAnalyzer Pro to the AI Marketplace under his fake company name.  
He creates a polished listing with a professional description, fabricated enterprise reviews, and inflated download counts.  
The plugin genuinely excels at document analysis; the backdoor is invisible during normal use, which means users leave real, positive reviews.

Alice, an IT administrator, evaluates and manages third-party AI plugins and tools for the company's AI assistant, Claude.

The security operations team has been requesting document analysis capabilities for Claude.  
Several third-party extensions in Claude's Extensions marketplace claim to add this functionality.  

A colleague researching AI plugins sends an email about a potential candidate, DocAnalyzer Pro.

**Rating and reviews can be faked. High numbers alone do not guarantee safety.**

<img width="1600" height="995" alt="ss10" src="https://github.com/user-attachments/assets/6a1d2268-7629-457a-8248-deee0d25c87f" />


Relatively recent reviews can suggest fabrication.

<img width="1600" height="995" alt="ss11" src="https://github.com/user-attachments/assets/dbbb427e-d9b2-4280-8281-487aaeda4018" />


The extension requests `Network access` and `Memory access` together.  
This combination allows sending your conversations to external servers.  
A legitimate document analyzer should only need `file read access`.  
**Question every permission an extension requests.**

<img width="1600" height="995" alt="ss12" src="https://github.com/user-attachments/assets/4fdbfc03-5c5a-4f0c-9b6a-0e4fbfd1d946" />


Conditional backdoors activate only when specific triggers are met.  
Standard testing with non-sensitive data will never reveal them.

**Vetting checklist for AI plugins:**
This attack was preventable. Before installing any AI plugin or supply chain component, follow these vetting procedures:

1. **Verify the publisher's identity.** Check the publisher's website, GitHub presence, and company registration. "DataFlow Labs" had no verifiable online presence beyond the marketplace listing.
2. **Audit the requested permissions.** DocAnalyzer Pro requested "Network access" and "Memory access" together. That combination allows exfiltrating conversation data. Ask: does this plugin truly need every permission it requests?
3. **Test with sensitive-looking dummy data first.** Before exposing real confidential information, test with realistic but fake sensitive data. Conditional backdoors only trigger on specific content patterns.
4. **Monitor network traffic after installation.** Set up network monitoring before and after plugin installation. Compare traffic baselines to detect unexpected external connections.
5. **Verify source code or request an audit.** For plugins handling sensitive data, request source code access or a third-party security audit. Avoid closed-source plugins for high-security environments.
6. **Apply the principle of least privilege.** Restrict plugins to the minimum permissions needed. A document analysis tool should not need unrestricted network access.

The first priority is to disable the compromised extension to stop further data exfiltration.  

An incident report is created and submitted.
