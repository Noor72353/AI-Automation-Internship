# Task 9 — Customer Support RAG Chatbot with Gmail Integration

## Overview

An AI-powered customer support automation system built using **n8n, Google Gemini, Gmail, Google Drive, and Retrieval-Augmented Generation (RAG)**.

The system automatically reads incoming customer emails, searches a company knowledge base, generates context-aware responses, and escalates unsupported or complicated queries to a human support representative.

## Features

- **Automated Email Monitoring:** Detects incoming customer emails through Gmail Trigger.
- **RAG-Based Knowledge Retrieval:** Searches company documentation using a vector store.
- **AI-Powered Responses:** Uses Google Gemini to generate relevant and professional customer replies.
- **Structured AI Classification:** Categorizes incoming emails as:
  - Supported
  - Unsupported
  - Unrelated
- **Human Escalation:** Sends internal notifications when a question requires human assistance.
- **Automatic Email Replies:** Responds to customers with AI-generated answers.
- **Email Organization:** Marks processed emails as read and applies Gmail labels.
- **Duplicate Handling:** Uses Gmail labels to exclude previously processed and escalated emails from subsequent trigger searches.

## Technologies Used

- n8n Cloud
- Google Gemini API
- Gmail API
- Google Drive
- Retrieval-Augmented Generation (RAG)
- Simple Vector Store
- Google Gemini Embeddings

## Workflow Architecture

### Workflow 1: Customer Support RAG — Knowledge Base

This workflow prepares the company knowledge base for AI retrieval.

**Workflow steps:**

1. Manual Trigger starts the workflow.
2. Google Drive downloads the company knowledge-base text file.
3. Extract From File extracts the text content.
4. Default Data Loader prepares the text documents.
5. Simple text splitting divides the content into smaller chunks.
6. Google Gemini Embeddings generates vector representations.
7. Simple Vector Store stores the document embeddings.

### Workflow 2: Customer Support RAG — Gmail Automation

This workflow handles incoming customer support emails.

**Workflow steps:**

1. Gmail Trigger detects new unread customer emails.
2. Gmail Get Message retrieves the complete email content.
3. AI Agent receives the customer email.
4. Simple Vector Store retrieves relevant company information.
5. Google Gemini generates a structured response containing:
   - Category
   - Customer reply
   - Human review requirement
   - Escalation reason
6. IF node checks whether human review is required.

**Supported or unrelated questions:**
- Gmail sends an automatic reply to the customer.
- The original email is marked as read.
- The `n8n-processed` label is applied.

**Unsupported or complicated questions:**
- An internal escalation notification is sent to the support inbox.
- The original email is marked as read.
- The `n8n-escalated` label is applied.

## Testing Results

| Test Scenario | Expected Result | Status |
|---|---|---|
| Express delivery inquiry | Correct RAG-based reply | Passed |
| Unknown laptop price | Human escalation | Passed |
| Unrelated weather inquiry | Polite redirection | Passed |
| Customer email reply | Automatic Gmail response | Passed |
| Processed email | Read status and processed label | Passed |
| Escalated email | Read status and escalation label | Passed |

## Setup Instructions

1. Create an n8n Cloud account.
2. Import both workflow JSON files.
3. Connect Google Drive and Gmail credentials.
4. Configure Google Gemini API credentials.
5. Upload your company knowledge-base text file to Google Drive.
6. Configure the Google Drive download node to select the knowledge-base file.
7. Ensure both workflows use the same Simple Vector Store memory key.
8. Execute the Knowledge Base workflow to populate the vector store.
9. Execute and test the Gmail Automation workflow.
10. Activate the Gmail workflow after completing the required checks.

## Important Notes

- This project uses a sample TechStore knowledge base for demonstration purposes.
- The Simple Vector Store stores data in temporary memory. Its contents may be lost when the n8n instance restarts, so the Knowledge Base workflow may need to be executed again.
- The Gmail and Google Gemini credentials must be configured separately in the user's n8n account.
- API keys, passwords, access tokens, and private credentials must never be committed to GitHub.
- The project is designed as an educational automation demonstration, not a production-ready customer support platform.

## Project Files

- `Customer Support RAG - Knowledge Base.json` — Knowledge-base ingestion workflow.
- `Customer Support RAG - Gmail Automation.json` — Gmail customer support automation workflow.

## Author

**Noorwali Khan**
BS Computer Science
FUUAST Islamabad, Pakistan

GitHub: [Noor72353](https://github.com/Noor72353)
