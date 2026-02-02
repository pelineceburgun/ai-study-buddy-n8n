# AI-Powered Weekly Report Automation (n8n + LLM)

This project is an end-to-end **AI-powered automation workflow** built with **n8n (self-hosted)**.  
It analyzes weekly study/work data using a **Large Language Model (LLM)**, automatically generates an insightful summary, sends the result via **email on a weekly schedule**, and logs all outputs to **Google Sheets** for tracking and review.

The project demonstrates:
- Real-world LLM integration
- Scheduled automation with Cron
- Workflow orchestration using n8n
- API-based system design
- Security-aware implementation choices

---

## 🧠 Project Motivation

Weekly progress reviews are often done manually and inconsistently.  
This project automates the entire process by:

- Collecting weekly input data
- Letting an LLM analyze patterns and performance
- Generating a structured, human-readable report
- Automatically sending the report via email
- Persisting results for long-term tracking

The result is a **fully automated weekly reporting system** with zero manual intervention.

---

## 🏗️ System Architecture

**Core Components:**

- **n8n (Self-hosted via Docker)**  
  Acts as the workflow orchestration engine.

- **Cron Trigger (n8n)**  
  Executes the workflow automatically on a weekly basis.

- **OpenRouter (LLM API – DeepSeek model)**  
  Performs natural language analysis and summarization.

- **Email (SMTP)**  
  Sends the AI-generated weekly report.

- **Google Sheets API**  
  Stores all reports and metadata for historical analysis.

---

## 🔁 Workflow Overview

The workflow consists of the following steps:

1. **Cron Trigger**
   - The workflow is triggered automatically once per week.
   - No manual execution is required.

2. **Data Preparation**
   - Weekly study/work data is prepared and passed to the workflow.
   - This data serves as contextual input for the LLM.

3. **LLM Request (HTTP Request Node)**
   - A POST request is sent to the OpenRouter API.
   - The request includes:
     - Selected LLM model
     - Prompt instructions
     - Weekly data payload
   - The LLM generates:
     - A concise weekly summary
     - Strengths and weaknesses
     - Improvement suggestions

4. **Email Delivery**
   - The AI-generated report is sent automatically via email.
   - This enables consistent weekly feedback without manual effort.

5. **Google Sheets Logging**
   - Each execution is logged to Google Sheets.
   - Logged fields may include:
     - Execution timestamp
     - Weekly input data
     - AI-generated summary
     - Model name
     - Execution status

---

## ⏱️ Scheduling (Cron)

- The workflow uses **n8n’s Cron node**.
- It is configured to run **weekly**.
- This ensures:
  - Regular reporting
  - Consistent delivery cadence
  - Fully autonomous operation

The system continues running without user interaction once deployed.

---

## 📊 Outputs

- **Email Output**
  - Clean, readable weekly AI report
  - Suitable for personal review or sharing

- **Google Sheets**
  - Centralized log of all weekly reports
  - Enables trend analysis over time

Screenshots of the workflow, email output, and Google Sheets logs are available in the `screenshots/` directory.

---

## 🔐 Security Considerations

Security was treated as a first-class concern.

- ❌ Workflow JSON is intentionally NOT included
- ❌ No API keys or secrets are committed
- ✅ All sensitive values are managed via:
  - n8n Credentials
  - Environment variables (where applicable)

This repository focuses on **architecture, behavior, and results** rather than exposing internal secrets.

---

## 🛠️ Technologies Used

- **n8n** (Self-hosted, Docker)
- **Cron Scheduling**
- **OpenRouter API**
- **Large Language Models (LLMs)**
- **SMTP Email Automation**
- **Google Sheets API**
- **REST APIs**
- **JSON-based workflows**

---

## 🚀 Possible Extensions

- Error-handling branches for API or model failures
- Multi-model comparison (A/B testing LLM outputs)
- User input via Webhook (API-style interface)
- Dashboard visualization on top of Google Sheets
- Dynamic prompt tuning based on historical data

---

## 🧩 Key Takeaways

- Demonstrates production-style AI automation
- Combines scheduling, AI, email, and persistence
- Shows awareness of security and credential management
- Designed for extensibility and real-world use

---

## 📌 Note

This repository intentionally does not include raw workflow files or credentials.  
The focus is on **design decisions, automation logic, and outputs**, following best practices for security-conscious projects.

