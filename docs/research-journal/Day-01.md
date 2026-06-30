# Research Journal – Day 1

**Project:** RAG-Enhanced LLM-Driven Detection Engineering for SOC Operations
**Date:** 30 June 2026

Today was dedicated entirely to understanding the research landscape before starting any implementation. I wanted to avoid jumping directly into coding or building a SOC environment without first understanding the actual problems researchers and security teams are trying to solve.

During the past few days, I explored several possible research directions in defensive cybersecurity, including Cloud Security Monitoring, AI for Cyber Defense, Detection Engineering, and Security Operations Centers (SOCs). Although cloud security is an interesting field, I decided not to pursue it for this project because building and evaluating realistic cloud environments would require additional infrastructure and budget. Instead, I chose a topic that can be implemented locally using open-source tools while still addressing a practical problem faced by modern SOC teams.

The research topic selected for this project is:

> **RAG-Enhanced LLM-Driven Detection Engineering for SOC Operations**

My initial objective was to understand how AI, Large Language Models (LLMs), and Retrieval-Augmented Generation (RAG) are currently being used within SOC environments. Rather than reading papers randomly, I organized them into several themes: AI-assisted SOCs, security log analysis, RAG, detection engineering, alert triage, and autonomous SOC operations.

Today, I completed a detailed review of the following three papers:

### 1. AI-Augmented SOC: A Survey of LLMs and Agents for Cyber Defense

This paper provided an excellent overview of the current research landscape. One of the biggest observations was that AI is being applied to many different SOC activities, including alert triage, log analysis, incident investigation, threat intelligence, and report generation. However, most of these solutions solve only one specific problem rather than supporting the complete analyst workflow.

Paper:
https://www.mdpi.com/2624-800X/5/4/95

---

### 2. Toward Autonomous SOC Operations

This paper explored how AI can participate throughout the investigation process instead of simply explaining alerts. The proposed framework assists analysts by generating queries, collecting evidence, correlating events, and recommending response actions. While the idea of an autonomous SOC is promising, the paper also highlights that human analysts are still required to validate AI-generated decisions.

Paper:
https://arxiv.org/abs/2604.27321

---

### 3. OpenSOC-AI

This paper focuses on using lightweight open-source language models to analyze security logs and automatically map them to MITRE ATT&CK techniques. I found this paper particularly relevant because it demonstrates that useful AI-assisted SOC capabilities can be achieved without relying on expensive commercial models. At the same time, the paper mainly focuses on log interpretation and does not extend into detection engineering or contextual knowledge retrieval.

Paper:
https://arxiv.org/abs/2604.26217

---

After reading these papers, several common problems appeared repeatedly.

The first is **alert fatigue**. Modern SOC analysts receive an overwhelming number of alerts every day, many of which turn out to be false positives. Another recurring issue is the shortage of experienced analysts, making it difficult for organizations to investigate incidents efficiently. I also noticed that investigation itself remains highly manual, requiring analysts to switch between SIEM dashboards, MITRE ATT&CK documentation, threat intelligence reports, and previous incidents before making decisions.

One observation stood out more than anything else.

Most existing research focuses on a single stage of the SOC workflow. Some papers concentrate on log analysis, others on alert triage, while others investigate automated detection rule generation. Very few studies attempt to combine these capabilities into one integrated framework.

This became the main motivation behind my research topic. Instead of solving only one SOC problem, I want to explore whether RAG, LLMs, MITRE ATT&CK knowledge, and detection engineering can be combined into a single workflow that assists analysts during investigations and also helps improve future detections.

I also sketched an initial high-level architecture for the project. The idea is to collect alerts from a SIEM platform, retrieve relevant knowledge from MITRE ATT&CK and threat intelligence sources using RAG, provide that context to an LLM, and generate outputs such as alert explanations, ATT&CK mappings, investigation guidance, and detection engineering recommendations. This architecture will undoubtedly evolve as I continue reviewing the literature and begin implementation.

Overall, today was less about technology and more about understanding the research problem. By the end of the day, I had a much clearer picture of where current research stands, what limitations still exist, and where my work might contribute. Rather than thinking of this as an AI project, I now see it as a cybersecurity research project where AI is one of the technologies used to solve a real operational challenge.

## Plan for Tomorrow

* Read the next three papers (Wazuh RAG Copilot, SigmaGen, and Detection Logic Generation).
* Continue refining the State of the Art.
* Explore the Microsoft GUIDE dataset.
* Refine the system architecture based on the literature.
* Start identifying the components required for the proof-of-concept implementation.
