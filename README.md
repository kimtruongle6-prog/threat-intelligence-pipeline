# Threat Intelligence Pipeline

**Project Status:** Exploratory Research Prototype — Under Development

**Author:** K.Le  
**Affiliation:** Independent Research  
**Research Focus:** Threat Intelligence Engineering, OSINT Data Processing, and Pipeline Architecture

**Copyright:** © 2026 K.Le. Applies only to original materials authored for this project. Third-party materials remain subject to their respective licenses.

---

## Overview

This project explores a semi-automated workflow for preparing open-source threat intelligence (OSINT), using LLM-assisted analysis, human review, and thematic data organization.

A separate experimental workflow demonstrated the preparation of a dataset containing **185 records** and the organization of reviewed threat information into **27 thematic CSV files**. These outputs were produced through a Google Colab and NotebookLM-assisted workflow; they are not generated automatically by the current Python scripts in this repository.

The GitHub repository contains early-stage Python prototypes for selected pipeline components. Actual RSS ingestion, live Google Sheets integration, automated classification, and end-to-end execution remain under development.

For the research workflow and supporting documentation, see the [K.Le Research Portfolio — Threat Intelligence Pipeline](https://sentinel-x-report.notion.site/Threat-Intelligence-Pipeline-Automated-OSINT-Processing-LLM-Assisted-Analysis-3ac39bb2f45d80c7b44fd907cfab3429).

---

## Experimental Workflow

The research workflow explored the following stages:

1. **OSINT Feed Preparation** — Collecting and preparing publicly available cybersecurity feed data.
2. **Data Preparation & Metadata Annotation** — Cleaning and organizing records, with preliminary AI-assisted and rule-based metadata preparation.
3. **Contextual Analysis & Human Review** — Using NotebookLM as an interactive analysis assistant and reviewing suggested themes and annotations.
4. **Thematic Cataloging** — Organizing reviewed records into 27 thematic CSV files.
5. **Knowledge Management Direction** — Exploring future organization and integration of the thematic datasets into a centralized knowledge base.

The experimental workflow involved separate Colab and NotebookLM activities. It should not be interpreted as a fully automated pipeline implemented by the repository scripts.

---

## Repository Structure

```text
threat-intelligence-pipeline/
├── crawler/
│   └── rss_crawler.py
├── catalog/
│   └── threat_classifier.py
├── config.example.json
├── .gitignore
└── README.md
```

### Current Source Code

- **`crawler/rss_crawler.py`** — Initial RSS crawler prototype. The current version uses simulated article records; actual RSS parsing, deduplication, and Google Sheets ingestion are not implemented.
- **`catalog/threat_classifier.py`** — Initial cataloging prototype. The current version uses a mock Google Sheets client and writes 27 CSV files containing simulated content. It does not retrieve or classify real threat records.

---

## Current Implementation Status

| Component | Current Status |
|---|---|
| OSINT dataset preparation | Demonstrated in a separate Colab workflow |
| Experimental dataset | 185 records reported in the experimental workflow |
| AI-assisted metadata preparation | Demonstrated as preliminary output |
| NotebookLM contextual analysis | Conducted as an interactive workflow |
| Human review of annotations | Included in the experimental workflow |
| Thematic CSV catalog | 27 files produced in the experimental workflow |
| GitHub RSS crawler | Initial prototype; currently uses simulated article data |
| GitHub threat classifier | Initial prototype; currently generates CSV files with simulated content |
| Google Sheets API integration in repository | Not implemented |
| Automated NotebookLM integration | Not implemented |
| Automated Notion synchronization | Not implemented |
| End-to-end automated execution | Not yet implemented or validated |

The experimental workflow outputs and the current repository implementation are separate. The Python scripts are an initial attempt to structure and reproduce selected processing stages.

---

## Configuration

The repository includes `config.example.json` as a reference for local configuration. It contains placeholder values only.

Before running either script, create a local `config.json` from `config.example.json`. The example now lists the configuration keys expected by the current prototypes. These values are placeholders: the scripts still use simulated data and do not perform live external-service integration.

- Keep API keys, credentials, and private identifiers out of source control.
- The `.gitignore` file excludes `config.json`.
- Do not commit real credentials or private datasets.

---

## Security Considerations & Limitations

- **Untrusted OSINT content:** External feeds may contain inaccurate, misleading, or intentionally manipulated information. Formal source validation, content sanitization, and prompt-injection controls remain areas for further implementation.
- **Human review:** AI-generated summaries, labels, and severity suggestions are preliminary and require review. The consistency and effectiveness of the review process have not yet been evaluated through a formal validation study.
- **Credential management:** Sensitive configuration values should be stored locally and excluded from version control. The current scripts do not yet implement complete authentication or live service integrations.
- **Data integrity:** Taxonomy alignment and structured CSV preparation were explored in the experimental workflow. Automated schema enforcement and comprehensive data-integrity validation have not yet been demonstrated by the current GitHub scripts.
- **Performance and scalability:** Operating costs, usage limits, scalability, and long-term reliability have not yet been formally benchmarked.

---

## Development Roadmap

1. **Reliable OSINT ingestion**
   - Implement actual RSS parsing.
   - Define a consistent article data structure.
   - Add URL-based or content-based duplicate detection.
   - Handle unavailable feeds and malformed entries.

2. **Data preparation and validation**
   - Implement HTML cleanup and date normalization.
   - Define required metadata fields.
   - Validate missing or malformed records.
   - Establish consistent record identifiers.

3. **AI-assisted annotation and human review**
   - Define a repeatable annotation format.
   - Explore LLM-assisted entity extraction, categorization, and summarization.
   - Preserve human review before accepting important classifications.

4. **Thematic catalog generation**
   - Replace simulated data with actual input records.
   - Implement real record segmentation and CSV generation.
   - Validate category assignments and output schemas.

5. **Integration and evaluation**
   - Explore Google Sheets and Google Drive integration.
   - Investigate structured knowledge-base synchronization.
   - Evaluate classification consistency and data quality.
   - Document reproducible execution and limitations.

These are planned development activities, not completed milestones.

---

## Research Direction

The project investigates how OSINT data preparation, AI-assisted analysis, and human review can support the organization of open-source cybersecurity information.

The experimental workflow demonstrated a 185-record dataset and 27 thematic CSV outputs. The current repository does not yet reproduce that workflow automatically. The immediate development priority is to implement reliable RSS ingestion and real data processing before expanding to external integrations and automated threat catalog generation.
