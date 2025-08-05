🤖 AI Content Automation Workflow
This is an automated system built with n8n that streamlines the content creation process. The workflow researches trending topics, generates comprehensive blog posts and video scripts, and then submits everything to a Google Sheet for human review.

✨ Features
Automated Research: Discovers trending topics in the AI automation niche daily using Google Trends and YouTube.

AI-Powered Content: Utilizes the Groq API with the LLaMA-3 model to generate high-quality blog posts and video scripts.

Human-in-the-Loop: Submits all content to a Google Sheet, allowing for easy review and editing before publication.

Error Handling: Includes mechanisms for fallback topics, API timeouts, and data validation for a reliable workflow.

🏗️ Architecture
This is a 4-Agent system built in n8n using visual workflow nodes.

1. Content Research Agent
Purpose: Discover trending topics in the AI Automation niche.

Nodes Used:

Schedule Trigger: Daily execution at 9:00 AM.

HTTP Request (Google Trends): SerpAPI integration.

HTTP Request (YouTube): YouTube Data API v3.

Code Node (Process Topics): Merges, deduplicates, and cleans topics to output an array of 5 unique topics.

2. Prompt Agent
Purpose: Generate content creation prompts from trending topics.

Nodes Used:

HTTP Request (Groq API): Uses the LLaMA-3 model for prompt generation.

Code Node (Parse Prompts): Structures the prompts for content creation.

3. Content Creator Agent
Purpose: Generate the actual content (blog posts and video scripts).

Nodes Used:

HTTP Request (Blog Content): Uses Groq API with an expert system prompt and a max token limit of 2000.

HTTP Request (Video Script): Uses Groq API with an expert system prompt and a max token limit of 1500.

Code Node (Compile Content): Merges all content into a final package.

4. Content Submission & Review Agent
Purpose: Submit generated content to a Google Sheet for human review.

Nodes Used:

HTTP Request (Google Sheets): Submits data to a Google Apps Script web app.

Google Apps Script: Handles server-side processing and writing to the sheet.

🛠️ Technical Implementation
API Integrations
SerpAPI: For Google Trends data.

YouTube Data API v3: For video trend analysis.

Groq API: For AI content generation using LLaMA-3.

Google Apps Script: For submitting data to Google Sheets.

Configuration Requirements
You will need the following API keys and URLs:

- SerpAPI key
- YouTube Data API v3 key
- Groq API key
- Google Apps Script web app URL
Data Flow
Schedule → Research APIs → Topic Processing → AI Prompts → Content Creation → Sheet Submission
📊 Performance & Metrics
Execution Time: Approximately 45 seconds end-to-end.

Success Rate: 98% (with error handling).

Content Quality: High-quality, SEO-optimized content.

Cost: ~$0.05 per complete workflow run.
