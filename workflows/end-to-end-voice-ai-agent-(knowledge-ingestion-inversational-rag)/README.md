# 🎙️ VoxMind AI

### Intelligent Voice Agent with Long-Term Memory (RAG-Based)

VoxMind AI is an end-to-end **Voice AI Agent** that combines document ingestion, semantic search, and conversational intelligence.  
It enables natural voice or text-based interactions grounded in a custom knowledge base using Retrieval-Augmented Generation (RAG).

---

## 🚀 Features

- 🎧 Voice & Text Query Support
- 🧠 Long-Term Memory using Pinecone
- 📄 Automatic Knowledge Ingestion from Google Drive
- 🔍 Semantic Search with Vector Embeddings
- 🤖 Context-Aware Responses via Google Gemini
- 🔗 API-Based Integration using Webhooks
- ⚡ Scalable & Modular n8n Architecture

---

## 🏗️ Architecture Overview

```

User Voice/Text
↓
Webhook
↓
AI Agent
↓
Vector Retrieval (Pinecone)
↓
Google Gemini (LLM)
↓
Final Response

```

---

## 📂 Knowledge Ingestion Pipeline

1. Documents are fetched from Google Drive
2. Files are downloaded and chunked
3. Text is converted into embeddings using Google Gemini
4. Embeddings are stored in Pinecone
5. Data becomes searchable for conversational queries

---

## 🧠 Retrieval-Augmented Generation (RAG)

- User queries are embedded
- Relevant document vectors are retrieved from Pinecone
- Retrieved context is injected into the LLM prompt
- Responses are factual, grounded, and context-aware

---

## 🔌 Technologies Used

- **n8n** – Workflow orchestration
- **Google Drive API** – Knowledge source
- **Google Gemini (PaLM)** – Embeddings & LLM
- **Pinecone** – Vector database
- **LangChain (n8n nodes)** – RAG orchestration
- **Webhook API** – Voice/Text input integration

---

## 📡 API Usage

### Endpoint

```

POST /webhook/{id}

```

### Request Body

```json
{
  "question": "What projects does this assistant know about?"
}
```

### Response

```json
{
  "answer": "Here is the information I found based on my knowledge base..."
}
```

---

## 🎯 Use Cases

- Voice Assistants
- AI Chatbots with Memory
- Knowledge Base Q&A Systems
- Customer Support Automation
- Educational & Research Assistants

---

## 🛡️ Security & Scalability

- Namespaced vector storage
- Modular workflow design
- Easily extendable to multi-agent or multi-tenant setups

---

## 📌 Future Enhancements

- Real-time speech-to-text integration
- User authentication & personalization
- Multi-language voice support
- Streaming responses

---

## 📜 License

This project is intended for educational, research, and production-ready experimentation.
