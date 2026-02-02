# AI-Powered Weekly Report Automation (n8n + LLM)

This project is an end-to-end **AI-powered automation workflow** built with **n8n (self-hosted)**.  
It analyzes weekly study/work data using a **Large Language Model (LLM)**, automatically generates an insightful summary, sends the result via **email**, and logs all outputs to **Google Sheets** for tracking and review.

The main goal of this project is to demonstrate:
- Practical LLM integration
- Workflow orchestration with n8n
- API-based automation
- Security-aware design decisions

---

## 🧠 Project Motivation

Manually reviewing weekly progress data and writing summaries is repetitive and time-consuming.  
This project automates that process by:

- Feeding raw weekly data into an LLM
- Letting the model analyze strengths, weaknesses, and trends
- Generating a human-readable report
- Automatically delivering and storing the results

This turns unstructured data into **actionable insights** with minimal manual effort.

---

## 🏗️ System Architecture

**Core Components:**

- **n8n (Self-hosted via Docker)**  
  Workflow orchestration and automation engine.

- **OpenRouter (LLM API – DeepSeek model)**  
  Used to analyze text-based weekly data and generate summaries.

- **Email (SMTP)**  
  Delivers the AI-generated report automatically.

- **Google Sheets API**  
  Stores historical results for tracking and comparison.

---

## 🔁 Workflow Overview

The workflow consists of the following steps:

1. **Trigger**
   - Manual trigger (can be extended to Cron for scheduled execution).

2. **Data Preparation**
   - Weekly study/work data is prepared and passed to the workflow.
   - This data acts as the input context for the LLM.

3. **LLM Request (HTTP Request Node)**
   - A POST request is sent to the OpenRouter API.
   - The request includes:
     - Selected LLM model
     - Prompt instructions
     - Weekly data payload
   - The LLM analyzes the data and generates:
     - A concise summary
     - Strengths and weak points
     - Improvement suggestions

4. **Email Delivery**
   - The generated AI report is sent via email.
   - This enables hands-free weekly reporting.

5. **Google Sheets Logging**
   - Each execution is logged to Google Sheets.
   - Stored information may include:
     - Timestamp
     - Raw input data
     - AI-generated summary
     - Model used

---

## 📊 Example Outputs

- **Email Output**
  - Human-readable weekly report
  - Ready to be shared or archived

- **Google Sheets**
  - Historical record of all AI-generated reports
  - Enables long-term tracking and analysis

(Screenshots are available in the `screenshots/` directory.)

---

## 🔐 Security Considerations

Security was treated as a first-class concern in this project.

- ❌ **Workflow JSON is NOT included**
- ❌ **No API keys or secrets are committed**
- ✅ All sensitive data is managed via:
  - n8n Credentials
  - Environment variables (where applicable)

This repository intentionally contains:
- Architecture explanation
- Visual documentation (screenshots)
- Conceptual workflow description

This approach prevents accidental exposure of sensitive credentials while still clearly demonstrating the system design.

---

## 🛠️ Technologies Used

- **n8n** (Self-hosted, Docker)
- **OpenRouter API**
- **Large Language Models (LLMs)**
- **SMTP / Email Automation**
- **Google Sheets API**
- **REST APIs**
- **JSON-based workflows**

---

## 🚀 Possible Extensions

This project can easily be extended with:

- Cron-based weekly scheduling
- Error-handling branches (LLM/API failure cases)
- Multiple LLM model comparison
- Dashboard visualization on top of Google Sheets
- User input via Webhooks (API-style usage)

---

## 🧩 Key Takeaways

- Demonstrates real-world LLM integration beyond simple demos
- Shows practical workflow automation skills
- Highlights awareness of API security best practices
- Designed with extensibility and maintainability in mind

---

## 📌 Note

This repository focuses on **concept, architecture, and results** rather than sharing raw workflow files, in order to follow best practices around security and credential management.
