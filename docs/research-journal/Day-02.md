# Research Journal – Day 2

**Project:** RAG-Enhanced LLM-Driven Detection Engineering for SOC Operations
**Date:** 1 July 2026

Today was focused on refining the research direction and understanding how my work can contribute beyond the existing literature. After reviewing the initial papers yesterday, I wanted to identify the limitations of current approaches and determine where my proposed framework could provide additional value.

I began by studying three research papers that are closely related to my topic:

### 1. Wazuh Security Event Response with RAG-Driven Copilot

This paper demonstrates how Retrieval-Augmented Generation (RAG) can assist SOC analysts by retrieving relevant cybersecurity knowledge before generating responses. Instead of relying solely on the knowledge stored within the language model, the framework retrieves contextual information from sources such as MITRE ATT&CK and threat intelligence documentation. This approach improves investigation quality and helps reduce hallucinations during alert analysis. However, the work mainly focuses on investigation support and does not address detection engineering or continuous improvement of detection capabilities.

**Paper:**
https://wazuh.com/blog/security-event-response-with-rag-driven-copilot/

---

### 2. SigmaGen

This paper explores the use of Large Language Models to automatically generate Sigma detection rules from attack descriptions. The proposed approach significantly reduces the effort required to create detection rules and demonstrates that AI can assist detection engineers during rule development. Nevertheless, the generated rules still require manual validation before they can be deployed in production environments.

**Reference:**
https://arxiv.org/search/?query=SigmaGen&searchtype=all

---

### 3. Evaluating LLMs for Automated Detection Logic Generation

This paper evaluates the capability of Large Language Models to generate detection logic from cybersecurity scenarios. The results indicate that LLMs can support detection engineers by producing detection logic more quickly than manual development. However, the generated outputs are not always reliable and still depend on human expertise for verification. In addition, the proposed approach does not incorporate contextual cybersecurity knowledge through Retrieval-Augmented Generation.

**Reference:**
https://arxiv.org/search/?query=Evaluating+LLMs+for+Automated+Detection+Logic+Generation&searchtype=all

---

After comparing these papers, I noticed that they all address different stages of the SOC workflow. The Wazuh RAG Copilot focuses on investigation, SigmaGen focuses on Sigma rule generation, and the Detection Logic Generation paper focuses on creating detection logic. Although each solution is valuable, they operate independently and do not provide a complete workflow for SOC analysts.

This comparison helped me better understand the current research gap. Existing solutions generally concentrate on solving one problem at a time rather than supporting analysts throughout the entire investigation and detection engineering process. As a result, analysts still need to switch between multiple tools and manually combine information from different sources before making decisions.

One of the most important realizations today was that the project should not be centred around AI itself. The actual research problem is **Detection Engineering for Security Operations Centers**. Technologies such as Retrieval-Augmented Generation (RAG) and Large Language Models (LLMs) are simply the methods used to address this problem. Thinking about the project from this perspective makes the research much more meaningful and industry-oriented.

Based on the literature review, I refined the expected contribution of the project. Rather than developing another AI assistant that only explains security alerts, I want to investigate whether contextual cybersecurity knowledge retrieved through RAG can assist analysts during investigations while also providing recommendations to improve future detections. This approach combines investigation support with detection engineering, which appears to be less explored in the existing literature.

I also designed the first version of the proposed system architecture. The framework begins with security events collected from Windows, Linux systems, and publicly available datasets. These events are monitored by Wazuh to generate security alerts. Before the alerts are analysed by the language model, the framework retrieves relevant contextual information from trusted cybersecurity knowledge sources, including MITRE ATT&CK, threat intelligence reports, Sigma rules, and detection engineering documentation. The retrieved information is then combined with the original alert and provided to the LLM for analysis. The final output consists of an alert explanation, ATT&CK mapping, investigation guidance, and recommendations for improving existing detections. Human analysts remain responsible for validating all AI-generated recommendations before operational decisions are made.

Today's work also helped me understand the importance of designing a research architecture rather than simply a software architecture. Every component included in the framework should exist to answer a research question or solve an operational problem identified during the literature review. As the project progresses, the architecture will continue to evolve based on implementation results and additional research findings.

Overall, today provided a much clearer understanding of how my research differs from the existing work. The novelty is not the use of RAG or LLMs individually, but the integration of contextual knowledge retrieval, AI-assisted reasoning, and detection engineering into a unified workflow that supports SOC analysts throughout the investigation process.

## Plan for Tomorrow

* Explore the Microsoft GUIDE dataset and understand its structure.
* Identify the data required for experimentation and evaluation.
* Refine the proposed architecture based on the dataset.
* Prepare the implementation roadmap for the proof-of-concept.
* Begin planning the Wazuh-based experimental environment.
