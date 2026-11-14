# N8N Task 4: Pinecone RAG Chatbot

## Project Overview

This project demonstrates a Retrieval-Augmented Generation (RAG) chatbot built using n8n, Pinecone, and OpenAI.

It consists of two workflows: one for uploading and storing documents in Pinecone, and another for answering questions using the stored documents.

## Workflows

### 1. Inserting Document to Pinecone

This workflow allows users to upload PDF documents through an n8n form.

**Workflow process:**
- Receive PDF files through an n8n Form Trigger.
- Extract document content using Default Data Loader.
- Generate vector embeddings using OpenAI Embeddings.
- Store documents and embeddings in a Pinecone index.

### 2. RAG Chatbot

This workflow allows users to ask questions about the uploaded documents.

**Workflow process:**
- Receive questions through Chat Trigger.
- Process questions using an AI Agent.
- Retrieve relevant information from Pinecone Vector Store.
- Generate answers using the OpenAI Chat Model.

## Technologies Used

- n8n
- Pinecone Vector Database
- OpenAI
- AI Agent
- Retrieval-Augmented Generation (RAG)
- Vector Embeddings

## Files Included

| File | Description |
|---|---|
| `Inserting document to Pinecone.json` | Document ingestion workflow |
| `Rag Chatbot.json` | RAG chatbot workflow |

## Setup Instructions

1. Import both JSON workflow files into n8n.
2. Configure your own OpenAI credentials.
3. Configure your own Pinecone credentials.
4. Use the compatible Pinecone index named `n8n-documents`.
5. Activate or publish the workflows as required.

**Note:** You must configure your own credentials before running the workflows.
