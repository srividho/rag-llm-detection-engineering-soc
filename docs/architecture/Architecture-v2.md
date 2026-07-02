# Architecture V2 – Integrated AI-Assisted Detection Engineering Framework

---

# Objective

The objective of Architecture V2 is to define the implementation framework for the proposed AI-assisted Detection Engineering system. Unlike the initial conceptual architecture, this version describes how security events will be generated, collected, analysed, and evaluated throughout the research. The framework combines a locally deployed Security Operations Center (SOC), Wazuh SIEM, Retrieval-Augmented Generation (RAG), Large Language Models (LLMs), and trusted cybersecurity knowledge sources to support security investigations and detection engineering activities. In addition to the experimental SOC environment, the Microsoft GUIDE dataset is incorporated as an evaluation dataset, allowing the proposed framework to be assessed using both locally generated security events and real-world analyst-labelled incidents. This architecture establishes the foundation for implementing and evaluating the proposed research framework.

---

# Architecture Diagram

> *(Insert Architecture-v2.png here once the professional diagram has been created.)*

```
                                 Proposed AI-Assisted Detection Engineering Framework (Version 2)

                                        ┌────────────────────────────┐
                                        │     Experimental Data      │
                                        └────────────────────────────┘
                                                     │
                   ┌─────────────────────────────────┴─────────────────────────────────┐
                   │                                                                   │
                   ▼                                                                   ▼
      ┌──────────────────────────┐                                   ┌──────────────────────────┐
      │   Local SOC Environment  │                                   │ Microsoft GUIDE Dataset  │
      └──────────────────────────┘                                   └──────────────────────────┘
                   │                                                                   │
         ┌─────────┼──────────┐                                                        │
         │         │          │                                                        │
         ▼         ▼          ▼                                                        │
   Windows VM   Linux VM   Sysmon Events                                               │
         │         │          │                                                        │
         └─────────┴──────────┘                                                        │
                   │                                                                   │
                   ▼                                                                   │
        ┌──────────────────────────┐                                                   │
        │     Attack Simulation    │                                                   │
        │ Atomic Red Team / Manual │                                                   │
        └──────────────────────────┘                                                   │
                   │                                                                   │
                   ▼                                                                   │
        ┌──────────────────────────┐                                                   │
        │     Security Logs        │                                                   │
        └──────────────────────────┘                                                   │
                   │                                                                   │
                   └──────────────────────┬────────────────────────────────────────────┘
                                          ▼
                             ┌─────────────────────────┐
                             │      Wazuh SIEM         │
                             │ Alert Collection & SIEM │
                             └─────────────────────────┘
                                          │
                                          ▼
                             ┌─────────────────────────┐
                             │    Alert Processing     │
                             │ Parsing & Normalization │
                             └─────────────────────────┘
                                          │
                                          ▼
                    ┌────────────────────────────────────────────────┐
                    │ Retrieval-Augmented Generation (RAG) Framework │
                    └────────────────────────────────────────────────┘
                                          │
         ┌─────────────────┬────────────────────┬───────────────────┬────────────────────┐
         ▼                 ▼                    ▼                   ▼
 MITRE ATT&CK       Threat Intelligence     Sigma Rules      Detection Knowledge
   Framework             Reports             Repository          Documentation
         │                 │                    │                   │
         └─────────────────┴────────────────────┴───────────────────┘
                                          │
                                          ▼
                            ┌──────────────────────────┐
                            │  Large Language Model    │
                            │     (LLM Reasoning)      │
                            └──────────────────────────┘
                                          │
                                          ▼
        ┌─────────────────────────────────────────────────────────────────────────────┐
        │                 AI-Assisted Detection Engineering Module                    │
        ├─────────────────────────────────────────────────────────────────────────────┤
        │ • Alert Explanation                                                        │
        │ • MITRE ATT&CK Mapping                                                     │
        │ • Threat Context                                                           │
        │ • Investigation Guidance                                                   │
        │ • Detection Gap Identification                                             │
        │ • Detection Engineering Recommendation                                     │
        │ • Suggested Detection Rule Improvement                                     │
        └─────────────────────────────────────────────────────────────────────────────┘
                                          │
                                          ▼
                              ┌────────────────────────┐
                              │      SOC Analyst       │
                              │ Human Validation       │
                              └────────────────────────┘
                                          │
                                          ▼
                           Improved Detection Strategy & Evaluation
```

---

# Component Description

The framework consists of several interconnected components that collectively support AI-assisted detection engineering within a Security Operations Center.

| Component | Description |
|-----------|-------------|
| **Local SOC Environment** | A controlled laboratory environment consisting of Windows and Linux virtual machines used to generate realistic security events for experimentation. |
| **Attack Simulation** | Simulated attack scenarios executed using Atomic Red Team and manually performed techniques to generate security telemetry representative of real-world attacks. |
| **Microsoft GUIDE Dataset** | A publicly available dataset containing analyst-labelled security incidents used to evaluate the proposed framework against real operational scenarios. |
| **Wazuh SIEM** | Collects, correlates, and monitors security events from the local environment, transforming raw logs into structured security alerts. |
| **Alert Processing** | Parses and normalizes generated alerts by extracting relevant information such as timestamps, users, hosts, event identifiers, and process details. |
| **RAG Framework** | Retrieves contextual cybersecurity knowledge from trusted external sources before LLM reasoning, reducing hallucinations and improving response quality. |
| **Knowledge Sources** | Includes MITRE ATT&CK, threat intelligence reports, Sigma rules, and detection engineering documentation that enrich alert analysis. |
| **Large Language Model** | Performs contextual reasoning by analysing alerts together with retrieved knowledge and generates structured investigation outputs. |
| **AI-Assisted Detection Engineering Module** | Produces alert explanations, ATT&CK mappings, investigation guidance, detection gap identification, and recommendations for improving existing detections. |
| **SOC Analyst** | Reviews and validates AI-generated recommendations before operational decisions are made, ensuring human oversight throughout the investigation process. |

---

# Data Flow

The proposed workflow begins by generating security events within a controlled SOC laboratory environment through simulated attack scenarios. Security logs produced by Windows and Linux systems are collected by Wazuh SIEM, which correlates events and generates structured security alerts. At the same time, the Microsoft GUIDE dataset is incorporated as an external evaluation dataset, allowing the framework to be tested using real-world analyst-labelled incidents.

Each security alert is processed and normalized before entering the Retrieval-Augmented Generation (RAG) layer. During this stage, relevant contextual information is retrieved from trusted cybersecurity knowledge sources, including MITRE ATT&CK, threat intelligence reports, Sigma rule repositories, and detection engineering documentation. The retrieved context, together with the processed alert, is then supplied to the Large Language Model.

Using both the alert and the retrieved cybersecurity knowledge, the language model performs contextual reasoning and generates structured outputs including alert explanations, ATT&CK technique mappings, investigation guidance, identification of potential detection gaps, and recommendations for improving existing detection rules. These recommendations are finally presented to the SOC analyst for validation before being incorporated into future detection strategies.

---

# Why This Architecture?

The proposed architecture was developed after reviewing the current state of research in AI-assisted Security Operations Centers and identifying several limitations in existing approaches. Most existing solutions focus on a single activity, such as alert triage, log analysis, threat intelligence retrieval, or automated detection rule generation. Although these approaches provide valuable support, they remain fragmented and require analysts to manually combine information from multiple tools throughout the investigation process.

Architecture V2 addresses this limitation by integrating the complete workflow into a single framework. Rather than treating alert analysis and detection engineering as independent activities, the proposed design connects security monitoring, contextual knowledge retrieval, AI-assisted reasoning, and detection improvement within one continuous process. The inclusion of both a locally generated SOC environment and the Microsoft GUIDE dataset also strengthens the research by combining practical implementation with evaluation using real-world security incidents.

Instead of replacing human analysts, the framework is designed to reduce repetitive investigation tasks while providing explainable recommendations that support decision-making. This approach aligns with current research trends in AI-augmented Security Operations Centers while introducing a stronger focus on Detection Engineering as the primary research contribution.
