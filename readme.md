# RAG Teacher ChatBot

A personal AI study companion that lets students **chat with their own notes, lectures,
and study materials**. Built using **Retrieval-Augmented Generation (RAG)**, it answers
your questions directly from your uploaded documents — like having a private tutor
available 24/7.

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1tPTDTtVVsM4RCht2blabxBDHo9SxgCof)

---

## Problem Statement

Studying alone is hard. You read 50 pages of notes but can't find that *one* explanation
you need. You forget what was covered in Lecture 7. You wish someone could just
**explain your own notes back to you**.

**RAG Teacher ChatBot solves this:**

- Upload your notes, lectures, or any PDF
- Ask questions in plain language
- Get answers sourced **only from your material** — no hallucination, no random internet answers
- Revise faster, understand deeper, study smarter

---

## Who Is This For?

| User | Use Case |
|------|----------|
| **Students** | Revise lecture notes before exams by asking questions |
| **Self-Learners** | Upload any PDF book or guide and learn interactively |
| **Study Groups** | Share a chatbot loaded with shared class notes |
| **Exam Prep** | Quickly find answers from 100+ pages of material |

**In simple terms:** You upload your notes --> The bot reads and understands them -->
You ask questions --> It explains using *only your notes*, like a teacher would.

---

## Features

- **Upload Any PDF** — Lecture slides, handwritten note scans, textbooks, anything
- **Answers From YOUR Material** — Strictly uses your uploaded document as context
- **Referenced Answers** — The bot cites relevant parts of your notes in every answer
- **Teacher-Style Explanations** — Responses are clear, simple, and educational
- **Smart Retrieval** — Finds the top 3 most relevant chunks from your entire document
- **Zero Setup** — Runs fully in Google Colab, no local installation needed

---

## Tech Stack

| Component         | Technology                                  |
|-------------------|---------------------------------------------|
| Language          | Python                                      |
| Framework         | LangChain                                   |
| LLM               | Groq API — LLaMA 3.3 70B Versatile          |
| Embeddings        | HuggingFace — `all-MiniLM-L6-v2`           |
| Vector Store      | ChromaDB                                    |
| Document Loader   | PyPDFLoader                                 |
| Text Splitter     | RecursiveCharacterTextSplitter              |
| Environment       | Google Colab                                |

---

## Getting Started

### Requirements

- A free **Groq API key** — get one at [console.groq.com](https://console.groq.com)
- [`requirements.txt`](requirements.txt) — available in this repository

### Steps

1. Click the **"Open in Colab"** badge above
2. Add your `GROQ_API_KEY` to Colab Secrets (key icon in left sidebar)
3. Download [`requirements.txt`](requirements.txt) from this repository
4. Upload `requirements.txt` to your Colab session (folder icon in left sidebar --> Upload)
5. Run **Cell 1** — installs all dependencies from `requirements.txt`
6. Run **Cell 2** — upload your PDF when prompted
7. Run **Cells 3 to 5** — loads, chunks, embeds your document, and builds the RAG chain
8. Run **Cell 6** — start chatting with your notes
9. Type `q` to exit the chat

---

## Project Structure

```
RAG-Teacher-ChatBot/
├── RAG_Teacher_ChatBot.ipynb   # Main Colab notebook
├── requirements.txt            # Python dependencies
└── README.md
```

---

## Roadmap

- [x] Core RAG pipeline in Google Colab
- [x] PDF upload and chunking
- [x] Interactive chat loop with exit command
- [ ] **Local Web App** — a full browser-based UI to run everything locally without Colab (coming soon)

---

## Configuration

| Parameter       | Value  | What It Does                                        |
|-----------------|--------|-----------------------------------------------------|
| `chunk_size`    | 500    | Size of each text chunk in characters               |
| `chunk_overlap` | 50     | Overlap between chunks to avoid cutting context     |
| `top_k`         | 3      | Number of relevant chunks retrieved per question    |
| `temperature`   | 0.3    | Low value keeps answers factual and grounded        |
| `DB_PATH`       | ./db   | Local ChromaDB persistence directory               |
