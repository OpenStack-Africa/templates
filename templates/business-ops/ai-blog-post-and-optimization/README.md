# AI Blog Post Automation

An n8n workflow that automates the entire process of generating, saving, and publishing blog posts for startup founders.

## Overview

This workflow takes a list of blog topics from Google Sheets, generates a professional outline and full blog post using AI, saves the content to Notion and Google Sheets, and automatically publishes it to LinkedIn.

## How It Works

### Workflow Steps

1. **Trigger**  
   Manual trigger (`When clicking ‘Test workflow’`)

2. **Get Topics**  
   Pulls pending topics from the **"blog topics"** sheet in Google Sheets.

3. **Generate Outline**  
   Uses **GPT-4o-mini** to create a concise, compelling outline (under 150 words).

4. **Generate Blog Post**  
   Uses the outline to write a short, high-impact blog post (~400 characters) optimized for startup founders.  
   Includes storytelling, statistics, insightful tone, and a clear CTA.

5. **Save Content**
   - Appends topic, outline, and generated post to the **"blog lifecycle"** sheet.
   - Creates a new entry in the **Notion** "Blog posts" database.

6. **Publish**  
   Automatically posts the blog content to **LinkedIn**.

7. **Update Records**  
   Updates Google Sheets with the final post content.

## Tools & Integrations

- **Google Sheets** – Topic source & lifecycle tracking
- **OpenAI (GPT-4o-mini)** – Outline and content generation
- **Notion** – Blog post database
- **LinkedIn** – Auto publishing

## Benefits

- Saves hours of writing time
- Consistent content output
- Centralized content management (Sheets + Notion)
- Automated distribution to LinkedIn

## How to Use

1. Add new topics to the **"blog topics"** sheet in Google Sheets.
2. Run the workflow manually in n8n.
3. Review the generated post in Notion and LinkedIn.

---

**Automated Content Engine for Startup Founders**