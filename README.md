# 🤖 AI Job Scraper & Application Assistant (n8n Automation)

An **end-to-end automated job-hunting assistant** built with **n8n** and **AI agents**.

This workflow automatically:
- Scrapes fresh job listings from LinkedIn
- Evaluates them using **Google Gemini AI**
- Generates **personalized cover letters**
- Sends the best job matches directly to **Telegram**

All of this runs **fully automated — completely hands-free**.

---

## 🧠 Overview

Finding relevant jobs manually is time-consuming. This automation pipeline solves that by combining **web scraping, AI evaluation, and messaging** into one daily workflow — analyzing listings against your resume and notifying you only about the **best opportunities**.

---

## ⚙️ Workflow Architecture

### 1️⃣ Setup & Data Collection
- **Schedule Trigger** — runs daily (e.g., 5 PM)
- **Google Drive** — downloads your latest resume PDF
- **File Extractor** — converts resume to text for AI processing
- **Google Sheets** — loads search preferences (keywords, location, experience level)

### 2️⃣ LinkedIn Job Scraping
- **URL Builder** — dynamically constructs a LinkedIn search URL via JavaScript
- **HTTP Request** — downloads the job search results page
- **HTML Extractor** — pulls all job posting links
- **Item Splitter** — breaks links into individual items for processing

### 3️⃣ Job Processing Loop
- **Wait (2s)** — prevents scraping rate limits
- **HTTP Request** — fetches each job detail page
- **HTML Parser** — extracts title, company, location, and description
- **Field Editor** — cleans and formats the extracted data

### 4️⃣ AI Evaluation & Cover Letter Generation
The workflow uses **Google Gemini AI** to:
- Compare the job description with your resume
- Generate a **Match Score (1–100)**
- Write a **tailored cover letter**

Results are parsed from structured JSON and saved to **Google Sheets**.

### 5️⃣ Smart Notifications
```
If Match Score ≥ 50 → Send Telegram Notification
```
Each Telegram message includes: Job Title · Company · Location · Match Score · Cover Letter · Job Link

---

## 🧩 Tech Stack

| Tool | Purpose |
|------|---------|
| **n8n** | Workflow automation engine |
| **Google Drive** | Resume storage |
| **Google Sheets** | Job preferences input & results output |
| **LinkedIn** | Job listing source |
| **Google Gemini AI** | Job matching + cover letter generation |
| **Telegram Bot** | Real-time job notifications |

---

## 🔁 Automation Flow

```
Schedule Trigger
      ↓
Resume + Preferences Loaded
      ↓
LinkedIn Job Scraping
      ↓
Job Data Extraction
      ↓
AI Job Matching (Gemini)
      ↓
AI Cover Letter Generation
      ↓
Save Results to Google Sheets
      ↓
Send Best Jobs to Telegram
```

---

## 📊 Google Sheets Setup

Import the two provided Excel files into Google Sheets.

**Sheet 1 — `Job_Search_n8n_Sheet`** *(Search Preferences — Input)*

**Sheet 2 — `Job_Search_n8n_founded_job_score_50`** *(Shortlisted Jobs — Output)*

Auto-populated by the workflow with jobs scoring ≥ 50.

---

## 🚀 Getting Started

1. Install and open your **n8n** instance
2. **Import** the workflow JSON
3. **Connect credentials:**
   - Google Drive
   - Google Sheets
   - Telegram Bot token
   - Gemini API key
4. **Configure Google Sheets** using the two provided Excel files
5. **Activate** the workflow

---

## 🔒 Security Notice

All API keys and OAuth credentials have been removed from the exported workflow JSON. You must reconnect all credentials after importing into your n8n instance.

---

## 📦 Use Cases

- Automated job alerts
- Resume-based job matching
- AI cover letter generation
- LinkedIn job monitoring
- Personal career automation

---

## 👨‍💻 Author

**Muhammad Haroon** — iOS Developer · Automation Engineer · AI Workflow Builder

📧 mianmharoon72@gmail.com  
🔗 [LinkedIn](https://www.linkedin.com/in/mian-haroon/)
