# 🧠 Fintech Leads Middle East — Automated Newsletter Workflow

## 📋 Overview
This project automates the creation of **FinTech newsletters and account engagement recommendations** for Backbase Sales Executives.  
It ensures sales teams stay up to date with Middle East FinTech, banking, and digital banking news — and provides **AI-generated recommendations** on how to engage with key accounts based on relevant articles.

The system is built entirely in **n8n**, using **agentic AI nodes** and **integrations** with external APIs (SerpAPI, Tavily, Gmail).

---

## 🚩 Problem Statement
Backbase Sales Executives often:
- Struggle to keep up with fast-moving FinTech and digital banking trends.
- Spend hours curating and summarizing articles.
- Lack structured guidance on how to engage prospects based on news context.

---

## 💡 Solution
An **automated editorial pipeline** that:
- Fetches the latest FinTech and banking articles from the Middle East.
- Summarizes each article and adds Backbase-specific engagement advice.
- Generates a production-ready HTML newsletter.
- Publishes a **draft email in Gmail** for human review before sending.

---

## ⚙️ Workflow Overview

### 🔄 Workflow Steps
1. **Manual Trigger**  
   Workflow manually started — ensures a *human-in-the-loop* process.
2. **Initial Research (SerpAPI)**  
   Searches Google News for `"middle east fintech, banking and digital banking news"`.
3. **Planning Agent (GPT-5)**  
   Filters, ranks, and curates the most relevant articles. Generates the newsletter title.
4. **Structured Output Parser**  
   Defines and validates expected output schema.
5. **Split Out**  
   Splits articles into separate items for parallel enrichment.
6. **Research Topics (Tavily)**  
   Performs related searches per article to provide extra context.
7. **Section Writer Agent (GPT-5)**  
   - Creates condensed summaries of each article.  
   - Adds **recommendations** on how Backbase Sales can engage based on the content.
8. **Aggregate**  
   Combines all sections into one newsletter object.
9. **Editor Agent (GPT-5.1)**  
   - Generates a **dark-blue, white-card HTML email** with inline CSS.  
   - Uses a clean, table-based layout for email compatibility.
10. **E-mail Parser**  
    Validates that subject and HTML body are present.
11. **Create Draft (Gmail)**  
    Publishes the newsletter as a **Gmail draft** for manual approval and sending.

---

## 🧰 Tech Stack

| Component | Description |
|------------|-------------|
| **n8n** | Orchestration platform for workflow logic, integrations, and observability. |
| **SerpAPI** | Fetches news articles from Google News. |
| **Tavily** | Performs related content search and topic enrichment. |
| **OpenRouter (GPT-5 / GPT-5.1)** | Hosts LLMs used for planning, summarization, and content creation. |
| **Gmail API** | Creates email drafts directly in Gmail (human-in-the-loop). |

---

## 🧑‍💼 Agent Roles

### 🧭 **Planning Agent**
- Filters articles to include only relevant FinTech & banking topics.
- Creates a concise newsletter title.
- Removes generic or unrelated items (e.g., crypto-only articles).

### ✍️ **Section Writer Agent**
- Merges article research results into a single structured summary.  
- Adds recommendations aligned with **Backbase’s digital engagement proposition**.  
- Outputs `{ title, description, recommendation }`.

### 📰 **Editor Agent**
- Compiles all sections into a formatted HTML newsletter.  
- Uses table-based email markup and inline CSS (email-safe).  
- Enforces consistent styling and accessibility.

---

## 🧩 Design Principles

- **Separation of Concerns**  
  Each agent performs a single, well-defined role (plan → write → edit → publish).
- **Human-in-the-Loop**  
  Manual trigger and Gmail draft ensure quality control before publication.
- **Modularity**  
  Each node can be swapped or re-used (e.g., alternate LLM models via OpenRouter).
- **Observability & Control**  
  n8n offers full logging, error handling, and execution visibility.
- **Low-Code / No-Code Design**  
  Entire solution built inside n8n without custom backend code.

---

## 📈 Results & Evaluation

| Metric | Outcome |
|---------|----------|
| **Execution Time** | ~3–5 minutes per run |
| **Manual Effort Reduction** | From hours to minutes |
| **Output Quality** | Consistent, structured, relevant newsletters |
| **Human Oversight** | Built-in review step via Gmail draft |

**Impact:**  
Demonstrates how **AI agents + n8n** can automate contextual sales enablement content creation — transforming a time-consuming manual process into a repeatable, scalable, and high-quality workflow.

---

## 🚀 Future Improvements
- Reduce number of LLM calls (optimize Section Writer logic).
- Improve HTML design with pre-built template system.
- Add analytics (e.g., open-rate tracking or sales-engagement metrics).
- Integrate Backbase CRM or Salesforce to personalize recommendations per account.

---

**Author:** Jesse Piscaer  
**Course:** AI/ML Solutions Architecture — Capstone Project  
**Organization:** Backbase  
**Date:** October 2025
