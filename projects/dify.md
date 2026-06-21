# Dify — Production AI App Builder

![Stars](https://img.shields.io/github/stars/langgenius/dify?style=social)
![Language](https://img.shields.io/github/languages/top/langgenius/dify)

> **Open-source platform for building, deploying, and managing AI applications at production scale.** Think of it as "Vercel for AI apps" — visual workflow builder meets enterprise-grade infrastructure.

---

## What Makes Dify Different

While LangChain gives you the LEGO bricks, Dify gives you the **factory**. It handles:

- 🏗️ **Visual workflow design** — drag-and-drop RAG pipelines, agent chains
- 📊 **Observability** — monitor cost, latency, quality in real-time
- 🔄 **Model orchestration** — route between GPT-4, Claude, Llama based on task
- 🗄️ **Knowledge base** — upload docs, auto-chunk, embed, manage vector stores
- 🚀 **One-click deploy** — publish as API, web app, chatbot widget

## Architecture

```
┌──────────────┐  ┌──────────────┐  ┌──────────────┐
│  Web Console │  │   API Layer  │  │  Chat Widget  │
└──────┬───────┘  └──────┬───────┘  └──────┬───────┘
       │                 │                 │
       └────────┬────────┴────────┬────────┘
                │                 │
         ┌──────▼─────────────────▼──────┐
         │         Workflow Engine       │
         │  ┌────────┐ ┌─────┐ ┌─────┐  │
         │  │ RAG    │ │Agent│ │Tool │  │
         │  │ Pipeline│ │Loop │ │Use  │  │
         │  └────────┘ └─────┘ └─────┘  │
         └──────────────┬────────────────┘
                        │
         ┌──────────────▼────────────────┐
         │      Model Orchestration      │
         │  GPT-4 │ Claude │ Llama │ ... │
         └───────────────────────────────┘
```

## Key Features

### 1. Visual Workflow Builder
```
[User Input] → [Knowledge Retrieval] → [LLM Generation] → [Response]
                     ↑
              [Vector Store]
```

### 2. RAG Pipeline
- Upload PDFs, DOCX, web pages, Notion, etc.
- Auto-chunking with multiple strategies
- Embedding model selection
- Hybrid search (vector + keyword)

### 3. Agent Mode
- Tool calling with 50+ built-in tools
- Multi-step reasoning
- Code interpreter for data analysis

### 4. Production Features
- Rate limiting & quota management
- A/B testing between models
- Annotation & human feedback loops
- SSO, RBAC, audit logs (enterprise)

## Use Cases

| Use Case | Why Dify |
|----------|----------|
| **Customer support bot** | RAG on your docs + agentic problem-solving |
| **Internal knowledge base** | Company wiki turned into conversational AI |
| **Content generation pipeline** | Multi-step: research → draft → review → publish |
| **Data analysis assistant** | Code interpreter + natural language querying |
| **API service** | Deploy AI endpoints for your app (REST + streaming) |

## Self-Host or Cloud

```bash
# Self-host with Docker
git clone https://github.com/langgenius/dify.git
cd dify/docker
docker compose up -d

# Or use Dify Cloud for zero-ops
```

## Stack

- **Backend:** Python (Flask) + Celery + PostgreSQL + Redis
- **Frontend:** Next.js + TypeScript
- **Vector DB:** Weaviate / Qdrant / Milvus / pgvector
- **LLMs:** OpenAI, Anthropic, Azure, Ollama, and 100+ more

---

**Repo:** [github.com/langgenius/dify](https://github.com/langgenius/dify)

**Category:** [Agent Frameworks](../README.md#agent-frameworks)
