# Autonomous Multi-Agent Workspace (n8n, Multi-Modal Ingestion & Advanced RAG)

An enterprise-grade, autonomous multi-agent ecosystem engineered using n8n orchestration. The system utilizes a centralized Orchestrator Agent powered by GPT-4o-mini to dynamically parse multi-modal inputs (Text, Voice, Images) from WhatsApp and intelligently delegate tasks to a network of specialized sub-agents. It features an automated end-to-end document ingestion pipeline (RAG) and cross-platform marketing automation.

---

## 🚀 Key Features

- **Centralized Orchestration:** A master Orchestrator Agent that dynamically evaluates user intent, manages session memory, and routes execution to dedicated sub-agents.
- **Multi-Modal Ingestion:** Real-time stream processing of WhatsApp inputs, including text routing, automated voice transcription, and computer vision-driven image analysis.
- **Automated RAG & Document Processing:** A complete ingestion pipeline that downloads incoming files, extracts data from PDFs, applies a `Recursive Character Text Splitter`, and stores embeddings into **Pinecone Vector DB**.
- **Specialized RAG Agent:** A dedicated sub-agent hooked directly to the Pinecone Vector Store for highly accurate, context-aware semantic query retrieval.
- **Instagram Marketing Automation:** Autonomous workflows leveraging the Instagram Graph API to create media containers and publish posts with zero human intervention.
- **Omnichannel Toolsets:** Out-of-the-box automation blocks for Gmail (CRUD operations), Google Calendar scheduling, and live multi-source web searches (Google, Wikipedia, Hacker News).

---

## 🏗️ Architecture Flow

```text
       ┌──────────────────┐
       │  WhatsApp Input  │ (Text, Voice, Image, PDF/Files)
       └─────────┬────────┘
                 │
                 ▼
       ┌──────────────────┐
       │   n8n Gateway    │ (Conditional Routing / Switch Nodes)
       └────┬─────────┬───┘
            │         │
            │         ▼ [Document Upload Path]
            │    ┌────────────────────────────────────────────────────────┐
            │    │ Download File ──► Extract PDF ──► Recursive Text Split │
            │    └───────────────────────────┬────────────────────────────┘
            │                                │
            │                                ▼
            │                    ┌───────────────────────┐
            │                    │  Pinecone Vector DB   │
            │                    └───────────▲───────────┘
            ▼                                │
   ┌──────────────────┐                      │
   │   Orchestrator   │                      │
   │   (GPT-4o-mini)  ├──────────────────────┤
   └─┬───┬───┬───┬────┘                      │
     │   │   │   │                           │
     │   │   │   └─► 🧠 RAG Agent ───────────┘ (Semantic Context Q&A)
     │   │   └─────► 📸 Instagram Agent (Container Creation & Auto-Publish)
     │   └─────────► 📧 E-Mail Agent (Gmail CRUD Operations)
     └─────────────► 📅 Calendar & Web Search Agents (Google, Wikipedia)


🛠️ Tech Stack
Orchestration & Workflow Engine: n8n

LLM Backbone & Embeddings: OpenAI (GPT-4o-mini, Text-Embeddings-3)

Vector Database: Pinecone Vector DB

Text Chunking: Recursive Character Text Splitter

APIs & Integrations: WhatsApp Business API, Instagram Graph API, Google Workspace APIs (Gmail, Calendar)

Scripting & Data Manipulation: JavaScript / Node.js
