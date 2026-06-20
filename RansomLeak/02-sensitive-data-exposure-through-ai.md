# Sensitive Data Exposure Through AI

We begin with receiving an email from our manager. A board meeting is in a few hours, and they need a polished summary of the Q3 client performance report immediately.

"..do whatever you need to get it done quickly."

Time constraints are real, and the pressure often leads employees to bypass security protocols.

<img width="1600" height="995" alt="ss4" src="https://github.com/user-attachments/assets/962ed89f-b2b9-4745-a94a-8499a49b2039" />


The data contains multiple PII metrics.

Consumer AI tools are not covered by the company's data processing agreements.  
At the top of the session, the tool discloses its use of information.

<img width="1600" height="995" alt="ss6" src="https://github.com/user-attachments/assets/a0e8b1ec-4312-435d-8562-fc3a861acef9" />


Once data is sent to a consumer AI service, deleting the chat doesn't remove it from the provider's servers, logs, or training data.

<img width="1600" height="995" alt="ss7" src="https://github.com/user-attachments/assets/5902043e-24df-4ded-be34-6ea914f12f62" />


**The core lesson**:
- Enterprise AI tools are covered by your company's data processing agreements. Data is not used for model training, access is controlled with audit logs, and the service complies with regulatory requirements like GDPR and SOC 2.
- Consumer AI tools have no data processing agreement with your employer. Input data may be used to train future models, stored in logs accessible to the provider's staff, and there is no guaranteed data deletion or retention control.

The tool itself is not the problem.  
The problem is using an *unapproved tool* with *sensitive data.*

- **Before using any AI tool with work data:** Check your company's AI Acceptable Use Policy. Classify the data first. Never paste API keys, credentials, or authentication tokens into any AI tool. Remove PII before using AI for data analysis, even with approved tools.
- **If you accidentally share sensitive data with a consumer AI:** Report to IT Security immediately. Do not delete the conversation (it is needed for investigation and does not remove data from provider systems). Request immediate rotation of any exposed credentials.
- **Remember:** Deadlines and pressure are real, but a few hours saved by using a consumer AI tool can lead to weeks of incident response, regulatory reporting, and damaged client relationships.
