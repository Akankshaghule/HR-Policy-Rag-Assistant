# 🤖 HR Policy Assistant

An AI-powered **HR Policy Assistant** that allows employees to ask questions about company HR policies using natural language.

The application uses **Retrieval-Augmented Generation (RAG)** to retrieve relevant information from HR policy documents and generate accurate, context-aware responses through an LLM.

The project combines **LangChain, LangGraph, Qdrant, Portkey, Groq, and Streamlit** to provide an end-to-end AI-powered HR policy question-answering system.

---

## 📸 Application Output

The HR Policy Assistant provides a simple Streamlit interface where users can ask questions about company policies.

### Example Output

![HR Policy Assistant Output](output.png)

### Example Question

> How many annual leave days do employees get?

### Example Response

The assistant retrieves the relevant HR policy information and provides the corresponding leave entitlement in a structured response.

---

## ✨ Features

- 📄 HR policy document processing
- 🔍 Semantic search using vector embeddings
- 🧠 Retrieval-Augmented Generation (RAG)
- 🤖 LangChain-based AI agent
- 🔄 LangGraph agent workflow
- 🗄️ Qdrant vector database
- 🚪 Portkey AI Gateway for LLM routing
- ⚡ Groq for fast LLM inference
- 🛡️ HR policy-focused guardrails
- 🖥️ Interactive Streamlit web application
- 🔐 Environment-based API key management
- 📊 Evaluation utilities for testing responses
- 📝 Logging and tracing support

---

# 🏗️ System Architecture

```text
                         ┌───────────────────┐
                         │       User        │
                         └─────────┬─────────┘
                                   │
                                   ▼
                         ┌───────────────────┐
                         │     Streamlit     │
                         │       app.py      │
                         └─────────┬─────────┘
                                   │
                                   ▼
                         ┌───────────────────┐
                         │  LangChain /      │
                         │  LangGraph Agent  │
                         └─────────┬─────────┘
                                   │
                                   ▼
                         ┌───────────────────┐
                         │      Qdrant       │
                         │   Vector Search    │
                         └─────────┬─────────┘
                                   │
                         Relevant Policy Data
                                   │
                                   ▼
                         ┌───────────────────┐
                         │      Portkey      │
                         │    AI Gateway     │
                         └─────────┬─────────┘
                                   │
                                   ▼
                         ┌───────────────────┐
                         │       Groq        │
                         │        LLM        │
                         └─────────┬─────────┘
                                   │
                                   ▼
                         ┌───────────────────┐
                         │   HR Policy       │
                         │      Answer       │
                         └───────────────────┘
