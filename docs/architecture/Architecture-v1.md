# Architecture v1

## Objective

The objective of this architecture is to design an AI-assisted framework that supports Security Operations Center (SOC) analysts during both security investigations and detection engineering activities. Current SOC solutions often focus on a single task, such as alert triage, log interpretation, or detection rule generation, requiring analysts to switch between multiple tools and knowledge sources throughout an investigation. The proposed architecture aims to bring these activities together by combining security telemetry, contextual knowledge retrieval, Large Language Model (LLM) reasoning, and detection engineering assistance within a unified workflow. Rather than replacing analysts, the framework is intended to provide relevant context and actionable recommendations that help improve investigation efficiency and continuously strengthen detection capabilities.

---

# Architecture Diagram

```text
                                             Proposed AI-Assisted Detection Engineering Framework
                  ─────────────────────────────────────────────────────────────────────────────

 ┌────────────────────┐
 │   Data Sources     │
 └────────────────────┘
          │
          │
          ├──────────── Windows Security Logs
          ├──────────── Linux Security Logs
          ├──────────── Sysmon Events
          └──────────── Microsoft GUIDE Dataset
                          │
                          ▼
              ┌─────────────────────────┐
              │   Security Monitoring   │
              │       Wazuh SIEM         │
              └─────────────────────────┘
                          │
                          ▼
              ┌─────────────────────────┐
              │   Alert Processing      │
              │ Event Parsing & Context │
              └─────────────────────────┘
                          │
                          ▼
        ┌──────────────────────────────────────────────┐
        │     Retrieval-Augmented Generation (RAG)     │
        └──────────────────────────────────────────────┘
                          │
          ┌───────────────┼──────────────────┬────────────────────┐
          │               │                  │                    │
          ▼               ▼                  ▼                    ▼
  MITRE ATT&CK      Threat Intelligence   Sigma Rules    Detection Knowledge
     Knowledge           Reports            Repository      Documentation
          │               │                  │                    │
          └───────────────┴──────────────────┴────────────────────┘
                          │
                          ▼
              ┌─────────────────────────┐
              │ Large Language Model    │
              │     (LLM Reasoning)      │
              └─────────────────────────┘
                          │
                          ▼
      ┌──────────────────────────────────────────────────────────────┐
      │                AI-Assisted SOC Analysis                      │
      ├──────────────────────────────────────────────────────────────┤
      │ • Alert Explanation                                          │
      │ • MITRE ATT&CK Mapping                                       │
      │ • Threat Context                                             │
      │ • Investigation Guidance                                     │
      │ • Detection Gap Identification                               │
      │ • Detection Engineering Recommendations                      │
      └──────────────────────────────────────────────────────────────┘
                          │
                          ▼
                ┌───────────────────────┐
                │     SOC Analyst       │
                │ Human Validation      │
                └───────────────────────┘
                          │
                          ▼
                Improved Detection Strategy
```

---

# Component Description

| Component                           | Description                                                                                                                                                                                                                                                 |
| ----------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Security Events**                 | Security events collected from Windows, Linux systems, and publicly available datasets such as the Microsoft GUIDE dataset. These events represent the input to the framework.                                                                              |
| **Wazuh SIEM**                      | Acts as the centralized monitoring platform responsible for collecting, correlating, and generating security alerts from incoming telemetry.                                                                                                                |
| **RAG Knowledge Layer**             | Retrieves relevant cybersecurity knowledge from external sources, including MITRE ATT&CK, threat intelligence reports, Sigma rules, and detection engineering references. This additional context helps the language model produce more reliable responses. |
| **Large Language Model**            | Interprets the alert together with the retrieved context, identifies potential attack techniques, summarizes the incident, and provides investigation guidance.                                                                                             |
| **Detection Engineering Assistant** | Uses the investigation results to suggest possible improvements to existing detections, helping analysts strengthen monitoring capabilities against similar attacks in the future.                                                                          |
| **SOC Analyst**                     | Reviews the generated recommendations and makes the final decision. The framework is designed to support human analysts rather than automate security decisions.                                                                                            |

---

# Data Flow

The workflow begins when security events are generated by monitored systems or loaded from the Microsoft GUIDE dataset. These events are collected and processed by Wazuh, which produces alerts whenever suspicious activity is detected. Instead of sending the alert directly to the language model, the framework first retrieves relevant contextual information from trusted cybersecurity knowledge sources using a Retrieval-Augmented Generation (RAG) pipeline. The retrieved context, together with the original alert, is then provided to the LLM for analysis. Based on this information, the model produces a structured response that includes an explanation of the alert, the associated MITRE ATT&CK techniques, recommended investigation steps, and suggestions for improving existing detections. The final recommendations are presented to the SOC analyst, who validates the results and decides on the appropriate actions.

---

# Why This Architecture?

The architecture was designed based on observations from the literature review. Existing research has shown promising results in areas such as alert triage, log analysis, threat intelligence retrieval, and automated detection rule generation. However, these capabilities are often implemented as separate solutions with limited interaction between them. As a result, analysts still spend considerable time gathering contextual information, correlating findings, and improving detection content manually.

The proposed architecture addresses this limitation by integrating contextual knowledge retrieval, AI-assisted reasoning, and detection engineering support into a single workflow. By enriching security alerts with external cybersecurity knowledge before LLM analysis, the framework aims to provide more accurate and explainable recommendations while reducing the need for analysts to consult multiple resources during an investigation. Extending the workflow beyond alert interpretation to include detection improvement also aligns the framework more closely with the operational responsibilities of modern SOC teams.

Although this architecture represents an initial design, it establishes a foundation for implementing and evaluating an integrated AI-assisted detection engineering framework. Future iterations may refine individual components based on implementation results, experimental evaluation, and insights gained from additional literature.
