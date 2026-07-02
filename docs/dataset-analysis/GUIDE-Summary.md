# Microsoft GUIDE Dataset – Quick Summary

## Source

Microsoft Security Incident Prediction (GUIDE)

https://www.kaggle.com/datasets/Microsoft/microsoft-security-incident-prediction

---

## Why did I choose this dataset?

- Real-world SOC incidents.
- Largest public security incident dataset.
- Analyst-labelled incidents.
- Covers MITRE ATT&CK techniques.
- Suitable for AI-assisted SOC research.

---

## Dataset Size

- 13M+ evidence records
- 1.6M alerts
- 1M incidents
- 6,100+ organizations
- 33 entity types
- 9,100 detector IDs
- 441 MITRE ATT&CK techniques

---

## Strengths

- Real production telemetry.
- Real analyst decisions.
- Large-scale dataset.
- Suitable for investigation workflows.

---

## Limitations

- No raw Windows/Linux logs.
- Cannot replace SIEM.
- Better suited for evaluation than log collection.

---

## How it fits my research

GUIDE will be used as the evaluation dataset for my proposed RAG-enhanced LLM framework. Security alerts from the dataset will be enriched with contextual information using Retrieval-Augmented Generation before being analysed by the language model. The generated explanations and detection recommendations can then be compared with analyst-labelled incident information to evaluate the effectiveness of the proposed approach.

---

## Key Takeaways

- Excellent dataset for SOC research.
- Complements Wazuh instead of replacing it.
- Supports investigation-focused AI research.
- Fits well with Detection Engineering.
