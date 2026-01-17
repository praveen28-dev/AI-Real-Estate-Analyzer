# 🏠 AI-Powered Real Estate Deal Analyzer

**An automated ETL pipeline that ingests property data, analyzes investment viability using Generative AI (Google Gemini), and visualizes results on a user dashboard.**

![Project Status](https://img.shields.io/badge/Status-Completed-success)
![Tools](https://img.shields.io/badge/Tools-n8n%20|%20Airtable%20|%20Softr%20|%20Gemini-blue)

## 📖 Project Overview
This project solves the problem of manually analyzing real estate listings. It automatically parses unstructured property descriptions, calculates financial viability, and flags deals for human review if data is missing.

**Key Features:**
* **Cost-Effective AI:** Re-engineered to use **Google Gemini Flash** for analysis (replacing OpenAI).
* **Robust Error Handling:** Automatically flags deals as `🟡 HUMAN REVIEW` if critical financial data (price/renovation cost) is missing.
* **Strict JSON Parsing:** Custom logic to extract structured data (`asking_price`, `renovation_cost`, `airbnb_legal`) from natural language.
* **Frontend Dashboard:** Integrated with **Softr** for real-time visualization.

## ⚙️ Architecture

The system follows a 3-step pipeline orchestrated in **n8n**:

1.  **Ingestion:** Receives property text via Webhook.
2.  **Analysis (AI Agent):**
    * **Input:** Unstructured text.
    * **Model:** Google Gemini (PaLM).
    * **Logic:**
        * Extracts Price & Reno Cost.
        * Checks Airbnb legality.
        * Verdict: `🟢 BUY` if (Price + Reno < $400k) AND (Airbnb Allowed). Else `🔴 PASS`.
3.  **Storage & Display:** Saves structured data to **Airtable**, which syncs to the **Softr** dashboard.

## 📂 Files in this Repo
* `workflow.json`: The complete n8n workflow file. You can import this directly into your n8n instance.
* `Internship Assesment.pdf`: Detailed technical report and screenshot evidence of the working pipeline.

## 🚀 How to Use (Importing the Workflow)
1.  Download `workflow.json` from this repository.
2.  Open your [n8n](https://n8n.io) instance.
3.  Go to **Workflows** -> **Import from File**.
4.  Select `workflow.json`.
5.  Update the credentials for **Google Gemini** and **Airtable**.

## 📊 Dashboard Preview
*(The dashboard allows investors to filter deals by "BUY" or "PASS" status instantly).*

---
**Created by:** Praveen A
