# Ollama — Run AI Locally

![Stars](https://img.shields.io/github/stars/ollama/ollama?style=social)
![Language](https://img.shields.io/github/languages/top/ollama/ollama)

> **The Docker of Local AI.** Run Llama, Mistral, Gemma, and hundreds of other models on your own machine — no cloud, no API keys, no latency.

---

## Why Ollama?

Ollama made local LLMs mainstream. Before Ollama, running models locally meant wrestling with CUDA drivers, Python environments, and arcane CLI flags. Now it's:

```bash
ollama run llama3.2
```

That's it. One command.

## Key Features

| Feature | Why It Matters |
|---------|---------------|
| **One-command model serving** | Zero config — pulls and runs models automatically |
| **REST API** | Drop-in OpenAI-compatible `/v1/chat/completions` endpoint |
| **Model library** | 1000+ community models, any GGUF |
| **GPU acceleration** | Auto-detects NVIDIA, AMD, Apple Silicon |
| **Modelfiles** | "Dockerfiles for LLMs" — reproducible model configs |
| **Multimodal support** | Vision models (LLaVA, BakLLaVA) work out of the box |

## The Standard Stack

```
Ollama (engine) + Open WebUI (interface) = Self-hosted ChatGPT
```

This combo runs on anything — Raspberry Pi to multi-GPU servers.

## Quick Start

```bash
# Install (macOS / Linux / Windows)
curl -fsSL https://ollama.com/install.sh | sh

# Pull a model
ollama pull llama3.2

# Chat
ollama run llama3.2

# API (OpenAI compatible)
curl http://localhost:11434/v1/chat/completions \
  -d '{"model": "llama3.2", "messages": [{"role": "user", "content": "Hello!"}]}'
```

## Use Cases

- 🔒 **Privacy-first development** — sensitive code never leaves your machine
- 🏠 **Home lab AI** — your own personal assistant, always available
- 🧪 **Model experimentation** — test 10 models in 10 minutes
- 💰 **Cost savings** — zero API costs, unlimited usage
- 🏝️ **Offline AI** — code on planes, in remote areas, behind firewalls

## Ecosystem

| Integration | What It Does |
|-------------|-------------|
| **Open WebUI** | ChatGPT-like chat interface |
| **LangChain** | Build RAG pipelines with local models |
| **Continue.dev** | AI code completion in your IDE |
| **LM Studio** | GUI for model discovery and management |
| **Hermes Agent** | AI agent framework with local model support |

---

**Repo:** [github.com/ollama/ollama](https://github.com/ollama/ollama)

**Category:** [Local & Self-Hosted AI](../README.md#local--self-hosted-ai)
