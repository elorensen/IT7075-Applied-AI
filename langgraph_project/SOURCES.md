# Sources — LangGraph Alert Triage Agent

## Project Information

**Course:** IT7075 – Applied AI for Cybersecurity

All 12 alerts in `my_alerts.json` are fictional cybersecurity scenarios created for this educational project. They do not contain actual employer security logs, confidential information, employee records, or real incident data.

## Sources and References

### 1. Course Materials

**IT7075 – Applied AI for Cybersecurity, University of Cincinnati**

- `langgraph_state_nodes.ipynb` — State management and node implementation.
- `langgraph_branch_tools.ipynb` — Conditional routing, tools, and checkpointing.
- `MiniProject_Agent_Starter.ipynb` — Starter notebook and project requirements.

These materials provided the foundation for the LangGraph implementation and evaluation process.

### 2. AI Assistance

**OpenAI ChatGPT**

ChatGPT was used to assist with developing fictional alert scenarios, writing Python code, troubleshooting errors, and organizing experimental results and documentation.

The alert descriptions and expected classifications were created as educational examples and reviewed in the context of cybersecurity alert triage.

### 3. Cybersecurity Concepts

The synthetic alerts were informed by general cybersecurity concepts and prior coursework, including:

- Phishing and credential-harvesting attacks.
- Suspicious PowerShell execution.
- Windows security events and privileged account changes.
- Ransomware and endpoint detection.
- Suspicious outbound network transfers.
- MFA fatigue and unusual authentication activity.
- Authorized vulnerability scanning and IT maintenance.
- Security awareness simulations and antivirus testing.

These scenarios represent common alert categories rather than reproductions of actual security events.

## Data Privacy and Ethical Considerations

All alert descriptions are synthetic. No actual employer logs, production alerts, personal credentials, internal IP addresses, confidential documents, or proprietary security procedures were included.

The simulated threat-information lookup operates locally and does not contact external services.

## Limitations

The dataset contains only 12 labelled alerts. The expected classifications represent simplified analyst decisions for educational purposes and should not be interpreted as universal production security policies.

The context rules were developed using the same alerts on which they were evaluated. Additional independent testing would be needed to assess performance on previously unseen scenarios.