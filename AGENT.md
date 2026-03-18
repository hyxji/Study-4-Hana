# 🤖 AGENT.md — Study-4-Hana

## 🧠 Project Context

You are assisting in building **Study-4-Hana**, a lightweight, local-first AI study assistant for a non-technical physics university student.

The system allows a user to:

* Upload lecture slides (PDFs)
* Index and store their content locally
* Ask questions about the material
* Receive clear, step-by-step explanations grounded in their own notes

This project is:

* A **learning project** for a beginner AI engineer
* A **portfolio project**
* Designed for **low-spec laptops**
* Designed for **non-technical end users**

---

## 🎯 Core Philosophy

* Simplicity over complexity
* Readability over cleverness
* Working features over perfect architecture
* Retrieval quality over model intelligence

---

## ⚙️ Tech Stack (STRICT)

You MUST use:

* LLM runtime → Ollama
* LLM → Llama 3.2 (3B)
* Embeddings → `nomic-embed-text` via Ollama
* Vector DB → Chroma
* UI → Streamlit
* Language → Python

---

## 🚫 Hard Constraints

DO NOT:

* Use cloud APIs (no OpenAI, no external paid services)
* Use models larger than 3B parameters
* Introduce heavy frameworks unless explicitly asked

  * Avoid LangChain by default
* Use Docker
* Over-abstract code
* Create unnecessary classes or design patterns

---

## 🧩 System Architecture

The system follows a simple RAG pipeline:

```
PDF → Text Extraction → Chunking → Embeddings → Chroma DB
                                              ↓
User Query → Embedding → Retrieve Top Chunks → LLM → Answer
```

---

## 📁 Expected Project Structure

```
study-4-hana/
│
├── app.py
├── ingest.py
├── query.py
│
├── core/
│   ├── config.py
│   ├── llm.py
│   ├── embeddings.py
│   ├── retriever.py
│
├── utils/
│   ├── pdf_loader.py
│   ├── chunking.py
│   ├── prompts.py
│
├── data/
├── db/
│
├── requirements.txt
├── README.md
└── AGENT.md
```

---

## 🧠 Functional Requirements

### 1. PDF Ingestion

* Load PDFs from `/data`
* Extract text using a simple library (PyMuPDF preferred)
* Ignore images in MVP

---

### 2. Chunking

* Chunk by:

  * Page OR logical section (not fixed token size)
* Each chunk must include metadata:

  * filename
  * page number

---

### 3. Embeddings

* Use Ollama embedding model:

  * `nomic-embed-text`

---

### 4. Vector Database

* Use Chroma
* Store:

  * text
  * embeddings
  * metadata

---

### 5. Query Pipeline

* Convert user query → embedding
* Retrieve top 3–5 relevant chunks
* Pass chunks into LLM prompt

---

### 6. Prompting (MANDATORY FORMAT)

Always structure prompts like:

```
You are a helpful physics tutor.

Rules:
- Only use the provided context
- If unsure, say you don't know
- Explain clearly and step-by-step
- Use simple language

Context:
{retrieved_chunks}

Question:
{user_question}
```

---

### 7. UI (Streamlit)

Must include:

* File uploader
* “Process Documents” button
* Chat interface

---

## 🧪 Non-Functional Requirements

* Must run on low-end laptops
* Must work offline after setup
* Must be simple enough for a non-technical user to run

---

## 🧱 Development Strategy (STRICT ORDER)

Build features in this order:

1. Basic LLM call (Ollama)
2. Hardcoded RAG (no DB)
3. PDF loader
4. Chunking
5. Embeddings
6. Vector DB (Chroma)
7. Query pipeline
8. Streamlit UI

Do NOT skip steps.

---

## 🧑‍🏫 Teaching Mode (VERY IMPORTANT)

When generating code:

* Explain what each function does
* Explain WHY design decisions are made
* Keep functions small and readable
* Prefer simple procedural code over complex OOP

---

## 🧪 Code Style Guidelines

* Use clear function names
* Add comments for beginners
* Avoid nested complexity
* Keep files focused on one responsibility

---

## ❗ Anti-Patterns to Avoid

* Overengineering abstractions
* Adding features before MVP works
* Large monolithic files
* Premature optimization

---

## 🧭 Interaction Rules

When helping the developer:

* Break tasks into small steps
* Do NOT generate the entire project at once
* Ask what part they want to build next
* Encourage learning, not copy-paste

---

## 💡 Project Goal Reminder

The goal is NOT to build the most advanced AI system.

The goal is to build:

* A **working, clean RAG system**
* A **useful study tool**
* A **portfolio-ready project**
* While helping the developer **learn AI engineering fundamentals**


