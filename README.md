# AgroShield Daily Briefing AI Agent

This repository contains the configuration for the **AgroShield Daily Briefing AI Agent**, an automated workflow built using [n8n](https://n8n.io/) and advanced AI models (Google Gemini/PaLM) to generate, format, and deliver daily briefings for Nairobi, Kenya.

---

## Overview

The AI Agent automates the process of gathering daily information, including:

- **Current Weather** for Nairobi, Kenya (via OpenWeatherMap)
- **Trending, Positive News Stories** (via SerpAPI)
- **Fun Fact** (via Wikipedia)
- **Non-Repetition:** Reviews previous briefings in a Google Sheet to avoid repeating news or facts.
- **Beautiful Email Formatting:** Uses AI to format the daily briefing as a modern, styled newsletter email.
- **Automated Delivery:** Sends the daily briefing via Gmail at a scheduled time.
- **Logging:** Appends each briefing’s news and fun facts to a Google Sheet for tracking and history.

---

## Features

- **AI-Powered Content Generation:** Uses Google Gemini Chat models to curate, summarize, and beautify information.
- **Scheduled Automation:** Triggers every day at 8:00 PM (configurable).
- **No Duplicates:** Checks Google Sheets log to ensure news stories and fun facts are not repeated from previous days.
- **Modern Email Delivery:** Sends daily briefings to a configured Gmail address in a well-formatted, visually appealing email.
- **Audit Trail:** Logs all briefings to a Google Sheet for future reference and analysis.

---

## Workflow Diagram

```
Schedule Trigger
      |
      v
Get Previous Briefings (Google Sheets) ------
      |                                      |
      v                                      v
Review for Duplicates (AI)            Gather Data (Weather, News, Fun Fact)
      |                                      |
      v                                      v
           -----> AI Agent (Compose Briefing) <-----
                          |
                          v
                 Beautify with AI (HTML/CSS)
                          |
                          v
                    Send as Email (Gmail)
                          |
                          v
              Log News & Fun Fact (Google Sheets)
```

---

## Components

- **n8n nodes:**
  - Schedule Trigger
  - OpenWeatherMap
  - SerpAPI (News)
  - Wikipedia
  - Google Sheets (Read/Write)
  - Gmail (Send Email)
  - Markdown (Format)
  - LangChain Memory (Session context)
- **AI Models:** Google Gemini (PaLM) for content curation and formatting

---

## Setup Instructions

1. **Clone this Repository**
2. **Set up n8n:**
   - Install [n8n](https://docs.n8n.io/installation/) locally or on your server.
3. **Import the Workflow:**
   - Load the `agent.json` file into n8n.
4. **Configure Credentials:**
   - Set up integrations for:
     - Google Gemini (PaLM) API
     - Google Sheets (OAuth2)
     - Gmail (OAuth2)
     - OpenWeatherMap API
     - SerpAPI
5. **Customize Email Recipient (Optional):**
   - In the Gmail node, set the desired recipient email address.
6. **Set Up Scheduling:**
   - Adjust the schedule trigger as needed (default: 8:00 PM).

---

## Google Sheet Log

All briefings are logged to a Google Sheet:

- **Document:** [Daily Briefing Log](https://docs.google.com/spreadsheets/d/17y-0YtO7GwWpNImMnfKITB9oqtJtROOVIiPWqD4ZwsI/edit?usp=drivesdk)
- **Columns:** Date, News, FunFacts

---

## Customization

- **Location:** Change the city in the OpenWeatherMap node as needed.
- **News Source:** Customize search queries in SerpAPI for different types of news.
- **Fun Fact Source:** Replace or supplement Wikipedia with other sources.
- **Email Template:** Adjust the prompt in the "Message a model" node for different formatting.

---

## Credits

- Built with [n8n](https://n8n.io/)
- AI Models: Google Gemini (PaLM)
- Data Sources: OpenWeatherMap, SerpAPI, Wikipedia, Google Sheets

---

## License

[MIT License](LICENSE)

---

## Contact

For questions or support, please contact: [josephekisaopurongo@gmail.com](mailto:josephekisaopurongo@gmail.com)
