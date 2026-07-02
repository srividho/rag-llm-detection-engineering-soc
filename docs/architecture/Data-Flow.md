# Data Flow

---

# Overview

Understanding how information moves throughout the proposed framework is essential before beginning the implementation. The purpose of this data flow is to illustrate how security events are generated, processed, enriched with contextual cybersecurity knowledge, analysed using Artificial Intelligence, and finally transformed into actionable detection engineering recommendations.

Unlike traditional Security Operations Center (SOC) workflows, where analysts manually correlate information from multiple sources, the proposed framework integrates security monitoring, contextual knowledge retrieval, AI-assisted reasoning, and detection engineering into a single continuous process. This allows security alerts to be analysed with additional context while maintaining human validation before operational decisions are made.

---

# Data Sources

The proposed framework utilizes two complementary sources of security data.

The first source is a locally deployed Security Operations Center (SOC) environment consisting of Windows and Linux virtual machines. Security events are generated through controlled attack simulations using Atomic Red Team and manually executed attack scenarios. These events provide realistic telemetry that can be monitored by the SIEM platform throughout the implementation phase.

The second source is the Microsoft GUIDE dataset, which contains analyst-labelled security incidents collected from real-world production environments. Unlike the local SOC environment, this dataset is not used to generate security logs but rather to evaluate the proposed framework against realistic security investigations.

Together, these two data sources provide both experimental flexibility and practical evaluation capability.

---

# Data Flow Process

The workflow begins inside the local SOC environment where attack simulations generate security events on Windows and Linux systems. These activities produce operating system logs and endpoint telemetry that are continuously collected by Wazuh SIEM.

Once collected, Wazuh analyses the incoming logs and generates structured security alerts whenever suspicious behaviour is detected. These alerts represent the starting point of the AI-assisted investigation workflow.

Before an alert is analysed by the language model, it passes through an alert processing stage where relevant information such as timestamps, hostnames, process names, usernames, event identifiers, and severity levels are extracted and normalized. This preprocessing step prepares the alert for contextual analysis.

The processed alert is then forwarded to the Retrieval-Augmented Generation (RAG) layer. Rather than relying solely on the internal knowledge of the language model, the RAG framework retrieves relevant cybersecurity knowledge from trusted sources including the MITRE ATT&CK Framework, threat intelligence reports, Sigma detection rules, and detection engineering documentation.

The retrieved knowledge, together with the processed security alert, is provided to the Large Language Model for contextual reasoning. Based on this combined information, the model generates a structured analysis that includes an explanation of the alert, ATT&CK technique mapping, investigation guidance, threat context, identification of potential detection gaps, and recommendations for improving existing detection logic.

The generated recommendations are then presented to the SOC analyst, who reviews and validates the AI-assisted outputs before any operational decision is made. Maintaining human oversight ensures that the framework functions as a decision-support system rather than an autonomous security platform.

Finally, the effectiveness of the proposed framework is evaluated using both locally generated attack scenarios and the Microsoft GUIDE dataset. This dual evaluation strategy enables the framework to be validated in controlled laboratory conditions while also assessing its applicability to real-world security incidents.

---

# Data Flow Mapping

| Stage | Input | Output |
|--------|-------|--------|
| Attack Simulation | Atomic Red Team, Manual Attack Scenarios | Security Logs |
| Local Systems | Windows, Linux, Sysmon | Operating System Logs |
| Wazuh SIEM | Security Logs | Security Alerts |
| Alert Processing | Raw Security Alerts | Structured Security Alerts |
| RAG Framework | Structured Alert | Contextual Cybersecurity Knowledge |
| Knowledge Sources | MITRE ATT&CK, Threat Intelligence, Sigma Rules, Detection Documentation | Retrieved Context |
| Large Language Model | Alert + Retrieved Context | AI-Assisted Security Analysis |
| Detection Engineering Module | AI Analysis | Detection Recommendations |
| SOC Analyst | AI Recommendations | Validated Decision |
| Evaluation | Local Alerts + GUIDE Dataset | Performance Assessment |

---

# Component Relationship

The relationship between the major components of the proposed framework can be summarized as follows.

```

Attack Simulation
↓
Windows / Linux Systems
↓
Security Logs
↓
Wazuh SIEM
↓
Security Alerts
↓
Alert Processing
↓
Retrieval-Augmented Generation (RAG)
↓
MITRE ATT&CK + Threat Intelligence + Sigma Rules
↓
Large Language Model
↓
AI-Assisted Detection Engineering
↓
SOC Analyst
↓
Framework Evaluation

```

---

# Why This Data Flow?

The proposed data flow was designed after analysing the limitations of existing AI-assisted SOC solutions identified during the literature review. Current approaches generally focus on individual activities such as alert explanation, threat intelligence retrieval, or detection rule generation. As a result, analysts are still required to manually combine information from multiple systems before reaching a decision.

The proposed framework addresses this limitation by integrating every stage of the investigation into a unified workflow. Security alerts generated within the local SOC environment are enriched with contextual cybersecurity knowledge before being analysed by the language model. Rather than stopping at alert interpretation, the framework continues by identifying possible detection gaps and recommending improvements to existing detection logic.

The inclusion of the Microsoft GUIDE dataset further strengthens the evaluation by enabling the proposed approach to be assessed using real-world analyst-labelled security incidents in addition to locally generated attack scenarios.

---

# Key Observations

Several important observations emerged while designing the data flow.

First, the Microsoft GUIDE dataset should be viewed as an evaluation dataset rather than a replacement for the SIEM environment. Security events must still be generated within a controlled SOC laboratory to evaluate the framework under realistic attack scenarios.

Second, Retrieval-Augmented Generation plays a central role in improving the reliability of AI-generated responses by supplying the language model with trusted cybersecurity knowledge during the reasoning process.

Finally, the framework intentionally preserves human validation as the final stage of the workflow. The objective of the proposed system is not to replace SOC analysts but to reduce repetitive investigation tasks while supporting more efficient and informed detection engineering activities.

---

# Conclusion

The proposed data flow establishes a complete end-to-end workflow for AI-assisted Detection Engineering within a Security Operations Center. By combining locally generated security events, contextual knowledge retrieval, Large Language Models, and real-world evaluation using the Microsoft GUIDE dataset, the framework provides a practical foundation for implementing and validating the proposed research. This design also ensures that each stage of the workflow can be independently evaluated and improved throughout the implementation phase of the project.
