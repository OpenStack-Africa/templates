# RAG Automation - n8n Workflow

A **Retrieval-Augmented Generation (RAG)** system built with **n8n** that automatically ingests a document (CV) from Google Drive and allows intelligent chat interactions with it using vector search.

---

## Overview

This workflow implements a complete **RAG pipeline** with two main phases:

- **Ingestion Pipeline**: Automatically downloads a document, chunks it, embeds it, and stores it in Pinecone.
- **Query Pipeline**: Exposes a chat interface where users can ask questions about the ingested document. The AI Agent retrieves relevant context using vector similarity search before answering.

---

## Features

- **Automated Ingestion** – Runs every 2 hours
- **Google Drive Integration** – Pulls latest version of the document
- **Vector Database** – Pinecone for scalable semantic search
- **Multi-LLM Support** – Uses both OpenAI (`gpt-4o-mini`) and Google Gemini
- **Memory** – Conversation buffer window (last 20 messages)
- **Public Chat Trigger** – Can be used as a webhook/chatbot endpoint
- **Proper Text Splitting** – Recursive Character Text Splitter with overlap

---

## Workflow Architecture

### 1. Ingestion Phase (Scheduled)

---

## Technologies Used

| Component              | Technology                          |
|------------------------|-------------------------------------|
| Workflow Orchestration | n8n                                 |
| Vector Database        | Pinecone                            |
| Embeddings             | OpenAI (`text-embedding-3-small` / 512 dim) |
| LLMs                   | OpenAI `gpt-4o-mini` + Google Gemini |
| Document Loader        | n8n Default Data Loader             |
| Text Splitter          | Recursive Character Text Splitter   |
| Memory                 | Buffer Window Memory                |

---

## Prerequisites

- n8n instance (self-hosted or cloud)
- Google Drive OAuth2 credentials
- OpenAI API key
- Google Gemini (PaLM) API key
- Pinecone API key + Index (`rag`)

---

## Setup Instructions

1. Import the workflow JSON into n8n
2. Set up the following credentials:
   - `chuka's drive` → Google Drive OAuth2
   - `OpenAi account 3` → OpenAI API
   - `chuka's Google Gemini` → Google Gemini API
   - `n8n` → Pinecone API
3. Update the Google Drive File ID if needed
4. Activate the workflow

---

## Usage

### Ingestion
The workflow automatically ingests/updates the document from Google Drive every **2 hours**.

**Manual Trigger**: You can manually execute the "Schedule Trigger" node to force re-ingestion.

### Chat Interface
Once active, the **"When chat message received"** node provides a public webhook URL. You can:
- Use it directly in n8n Chat
- Integrate with frontend apps
- Connect to WhatsApp, Telegram, Slack, etc.

---
