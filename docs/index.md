# 🛠️ RAG Infrastructure & Notes

Welcome! This site is your central hub for architecting a high-performance, local **Retrieval-Augmented Generation (RAG)** system on macOS.

---

## 🎯 Project Overview
We are building a unified ecosystem for local AI development. By integrating a powerful model proxy with a specialized retrieval server, we eliminate the need to switch between fragmented APIs. The result is a seamless, localized workflow for private, document-based AI applications.

## 🚀 Core Objectives
Our implementation focuses on three primary pillars:

1.  **Documentation Architecture**
    *   Using **MkDocs** to maintain a clean, versioned guide for our local infrastructure.
2.  **Unified Model Access**
    *   Leveraging **LiteLLM** to proxy local models (Ollama) and cloud models (Gemini, Imagen) through a single, OpenAI-compatible endpoint.
3.  **Intelligent Knowledge Retrieval**
    *   Deploying **LightRAG** to index personal datasets, enabling advanced semantic search and chat capabilities based on your own data.

---

## 📂 Table of Contents

1.  **[MkDocs Setup](MkDocs Setup/Prerequisites.md)**
    *   *The foundation: Building the documentation framework used to manage and publish these guides.*
2.  **[LiteLLM Server](LiteLLM Server/LLM Setup.md)**
    *   *The model proxy: Configuring the core server that connects all local and cloud AI models into one stream.*
3.  **[LightRAG Server](LightRAG Server/IntroductionRAG.md)**
    *   *The retrieval engine: Step-by-step setup for document indexing and local knowledge base chat.*
