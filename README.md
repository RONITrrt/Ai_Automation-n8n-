# 🤖 AI Content Automation Workflow

This is an automated content creation system built using [n8n](https://n8n.io/). It streamlines the content pipeline by researching trending topics, generating high-quality blog posts and video scripts using LLaMA-3 via Groq API, and submitting everything to Google Sheets for human review.

---

## ✨ Features

- **Automated Research**  
  Discovers trending topics in the AI automation niche daily using Google Trends and YouTube.

- **AI-Powered Content**  
  Utilizes the Groq API with the LLaMA-3 model to generate high-quality blog posts and video scripts.

- **Human-in-the-Loop**  
  Submits all content to a Google Sheet, allowing for easy review and editing before publication.

- **Error Handling**  
  Includes mechanisms for fallback topics, API timeouts, and data validation for a reliable workflow.

---

## 🏗️ Architecture

This is a 4-Agent system built in **n8n** using visual workflow nodes.

### 1. 🕵️‍♂️ Content Research Agent
**Purpose:** Discover trending topics in the AI Automation niche.

**Nodes Used:**
- `Schedule Trigger`: Executes daily at 9:00 AM.
- `HTTP Request (Google Trends)`: Fetches via SerpAPI.
- `HTTP Request (YouTube Trends)`: Uses YouTube Data API v3.
- `Code Node (Process Topics)`: Cleans, deduplicates, and outputs 5 unique topics.

---

### 2. 💡 Prompt Agent
**Purpose:** Generate content creation prompts based on trending topics.

**Nodes Used:**
- `HTTP Request (Groq API)`: Uses LLaMA-3 to generate prompts.
- `Code Node (Parse Prompts)`: Formats the data for content generation.

---

### 3. ✍️ Content Creator Agent
**Purpose:** Generate long-form content and scripts.

**Nodes Used:**
- `HTTP Request (Blog Content)`: Blog post generation via Groq API (LLaMA-3, 2000 tokens).
- `HTTP Request (Video Script)`: Video script generation via Groq API (1500 tokens).
- `Code Node (Compile Content)`: Merges blog and video content into a structured object.

---

### 4. 📤 Content Submission & Review Agent
**Purpose:** Submits content to a Google Sheet for human QA.

**Nodes Used:**
- `HTTP Request (Google Sheets)`: Sends data to a Google Apps Script web endpoint.
- `Google Apps Script`: Handles backend write to Google Sheet.

---

## 🛠️ Technical Implementation

### API Integrations
- **SerpAPI**: Fetches Google Trends data.
- **YouTube Data API v3**: Gathers trending video topics.
- **Groq API**: Content generation via LLaMA-3.
- **Google Apps Script**: Submits data to a spreadsheet.

### Configuration Requirements

You will need the following:
- ✅ SerpAPI key  
- ✅ YouTube Data API v3 key  
- ✅ Groq API key  
- ✅ Google Apps Script Web App URL  

---
[Schedule Trigger]
↓
[Google Trends + YouTube Trends APIs]
↓
[Process Topics]
↓
[Groq LLaMA-3: Prompt Generation]
↓
[Groq LLaMA-3: Blog + Video Generation]
↓
[Compile Content]
↓
[Submit to Google Sheets]

yaml
Copy
Edit

---

## 📊 Performance & Metrics

| Metric              | Value               |
|---------------------|---------------------|
| ⏱️ Execution Time   | ~45 seconds         |
| ✅ Success Rate      | ~98% (with retries) |
| 🧠 Content Quality   | SEO-optimized, high-quality |
| 💵 Estimated Cost    | ~$0.05 per full run |

---

## 📂 Folder Structure (Optional)
/n8n-workflows/

content_research.json

prompt_agent.json

content_creator.json

submission_agent.json

/scripts/

google_apps_script.gs

/docs/

sample_output.md

api_config_guide.md

yaml
Copy
Edit

---

## 📜 License

This project is open-sourced under the [MIT License](LICENSE).

---
## 🔄 Data Flow

