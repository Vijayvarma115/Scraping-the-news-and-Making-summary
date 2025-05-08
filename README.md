# 📰 Google News RSS Scraper & Summarizer – n8n Workflow

This project is an **automated n8n workflow** that scrapes Google News RSS feeds, decodes the actual article URLs, uses a Large Language Model (LLM) to generate summaries, and stores the results in a **Google Sheet**.

---

## 📌 Features

- ⏰ Scheduled to run every day at 8 AM
- 🌐 Scrapes latest articles from [Google News RSS](https://news.google.com/rss)
- 🔍 Extracts and decodes original article URLs
- 🧠 Uses a Google Gemini LLM to generate 7–10 line article summaries
- 📄 Stores article title and summary in Google Sheets
- 🟰 Avoids duplication by matching article titles

---

## 🧩 Workflow Overview

The n8n workflow contains the following steps:

1. **Schedule Trigger** – Runs daily at 8 AM
2. **RSS Read** – Fetches articles from Google News RSS
3. **Code Node** – Decodes shortened Google article URLs to actual links
4. **Basic LLM Chain** – Summarizes each article using a custom prompt
5. **Google Gemini Chat Model** – Provides AI-generated summary
6. **Code Node** – Extracts `Title` and `Summary` from LLM response
7. **Google Sheets Node** – Appends or updates rows in a connected Google Sheet

---

## 🔧 Setup Instructions

### 1. Prerequisites

- An [n8n](https://n8n.io) instance (cloud or self-hosted)
- [Google Gemini API](https://ai.google.dev/)
- A connected [Google Sheets account](https://www.npmjs.com/package/n8n-nodes-base.googleSheets)
- An existing Google Sheet with headers:
  - `Title of the Article`
  - `Summary`

### 2. Import the Workflow

1. Download `Scraping.json` from this repository
2. Open your n8n editor
3. Click on `Import` → upload `Scraping.json`
4. Set credentials for:
   - Google Sheets
   - Google Gemini (via PaLM API key)
5. Optionally, update:
   - RSS URL
   - Sheet ID and name
   - Gemini model (e.g., `models/learnlm-1.5-pro-experimental`)

---

## 📂 Output Sample

Each row in your Google Sheet will look like this:

| Title of the Article | Summary |
|----------------------|---------|
| Trump announces trade deal... | President Trump has announced a trade deal with the United Kingdom... |

---
