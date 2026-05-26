# Brand Mention Monitor & Auto-Responder

An automated social media monitoring system built with n8n that tracks brand mentions on X (Twitter), analyzes sentiment, sends alerts for negative mentions, and automatically generates & posts professional replies.

---

## Overview

This workflow searches for mentions of "n8n" on X every scheduled interval, performs sentiment analysis using AI, and takes appropriate action:
- Negative mentions → Email alert is sent
- Positive / Neutral mentions → AI generates a reply and posts it automatically
- All interactions are logged into Airtable

---

## Features

- Real-time brand mention tracking on X
- AI-powered sentiment analysis (Positive / Neutral / Negative)
- Automatic reply generation using GPT-4o-mini
- Instant email notification for negative mentions
- Automatic posting of replies on X
- Full logging to Airtable database
- Loop handling for batch processing

---

## Workflow Flow

1. **Schedule Trigger** → Runs at set intervals
2. **X Search** → Searches for "n8n" mentions
3. **Sentiment Analysis** → GPT-4o-mini analyzes each post
4. **Decision Logic**:
   - If Negative → Send Gmail Alert
   - If Positive/Neutral → Generate Reply → Post on X
5. **Logging** → Save all data to Airtable

---

## Technologies Used

- **n8n** - Workflow automation
- **X (Twitter)** - Search and posting
- **OpenAI (GPT-4o-mini)** - Sentiment analysis & reply generation
- **Airtable** - Data logging
- **Gmail** - Negative mention alerts

---

## Setup Requirements

- X (Twitter) OAuth2 credentials
- OpenAI API key
- Airtable Personal Access Token
- Gmail OAuth2 credentials
- Airtable Base and Table configured

---

## How to Use

1. Import the workflow JSON into n8n
2. Configure all credentials
3. Update the search keyword in the X node if needed (currently searching "n8n")
4. Set your desired schedule in the Schedule Trigger node
5. Activate the workflow

---

## Author

Chukwuka Victory  
Automated Brand Protection & Engagement System