# Threat Intelligence Pipeline

## Overview
This repository contains a secure, end-to-end, 5-step automated Threat Intelligence Pipeline designed to collect, classify, filter, and store threat information from open-source feeds (OSINT). The pipeline integrates large language models (LLM) and automated categorization to transform raw security data into actionable threat intelligence.

---

## Data Flow (5-Step Pipeline)

### 1. RSS Crawler (Google Colab) -> Ingest into Raw Google Sheets
* **Script:** `crawler/rss_crawler.py`
* **Function:** Automatically fetches security advisory feeds from reliable global OSINT sources (e.g., CISA, BleepingComputer, KrebsOnSecurity, etc.).
* **Deduplication:** Filters out duplicate articles before saving the clean, raw feed data into a central Google Sheets database.

### 2. Semi-Automated Annotation (via NotebookLM)
* **Function:** Analyzes the raw threat data using NotebookLM to generate preliminary category recommendations, severity ratings, and threat descriptions based on the raw content.

### 3. Review and Verification
* **Function:** Human-in-the-loop validation to review and refine the AI-generated labels directly inside Google Sheets, ensuring strict consistency, accuracy, and data integrity.

### 4. Threat Catalog Automation (Google Colab) -> Segment to Google Drive
* **Script:** `catalog/threat_classifier.py`
* **Function:** Fetches the verified labeled data from Google Sheets, segments the database, and appends the records into 27 thematic CSV files stored securely on Google Drive (each dedicated to specific malware types, attack vectors, or infrastructure targets).

### 5. Advanced Analysis & Knowledge Integration (Notion)
* **Function:** Ingests the organized CSVs into NotebookLM for deep-dive contextual correlation, generating intelligence reports, and synchronizing knowledge assets to Notion for long-term secure knowledge management.

---

## Configuration
All sensitive parameters and environment-specific variables are decoupled from the code and managed via a local `config.json` file. 

Refer to `config.example.json` for structure:
* `GEMINI_API_KEY`: Secure API key for LLM operations.
* `GOOGLE_SHEETS_ID`: The unique identifier of your primary Google Sheets.
* `RSS_FEED_URLs`: Customizable array of target RSS feed links.

---

## Security Considerations

* **Mitigating Data Poisoning:** The pipeline sanitizes raw feed content and isolates untrusted inputs before transferring data to subsequent processing steps.
* **Credential Isolation:** The `config.json` containing real API keys and Sheet IDs is completely excluded from Git via `.gitignore` to prevent accidental public exposure of secrets.

---

## Quick Start

1. **Clone the Repository:**
   ```bash
   git clone https://github.com/kimtruongle6-prog/threat-intelligence-pipeline.git
   cd threat-intelligence-pipeline
