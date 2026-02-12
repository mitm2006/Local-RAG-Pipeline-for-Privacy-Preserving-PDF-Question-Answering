# Local RAG Pipeline for PDF-Based Question Answering

This project implements a **Retrieval-Augmented Generation (RAG)** pipeline that allows users to query PDF documents locally while preserving **data privacy**. The system retrieves relevant document chunks using semantic embeddings and generates accurate, context-aware responses using a lightweight causal language model.

The pipeline is tested using an **AWS Guide Book (PDF)** as a sample knowledge source.

---

## Key Features

- **PDF-based knowledge ingestion**
- **Fully local execution** (no external APIs)
- **Semantic retrieval using dense embeddings**
- **Lightweight causal reasoning LLM**
- Efficient and privacy-preserving RAG workflow

---

##  Architecture Overview

1. **Document Ingestion**
   - Load and parse PDF documents
   - Chunk text into manageable segments

2. **Embedding Generation**
   - Generate dense vector embeddings for each chunk
   - Store embeddings for similarity search

3. **Retrieval**
   - Retrieve top-k relevant chunks based on user query
   - Cosine similarity–based semantic search

4. **Augmented Generation**
   - Inject retrieved context into the prompt
   - Generate a final answer using the LLM

---

## Models Used

| Component | Model |
|---------|-------|
| Embeddings | `all-mpnet-base-v2` | https://huggingface.co/sentence-transformers/all-mpnet-base-v2 |
| LLM | `Qwen3 Causal Reasoning (0.7B parameters)` | https://huggingface.co/Qwen/Qwen3-0.6B |

Both models are executed **locally** to ensure privacy and offline capability.

---

## Project Structure

```text
.
├── Scripts/
│   └── RAG_passage_embedder.ipynb   # PDF loading, chunking, and embedding generation
│   └── RAG_retrieval.ipynb          # Semantic retrieval and answer generation
├── data/
│   └── aws_guidebook.pdf        # Sample PDF used for testing
├── embeddings/
│   └── vector_store.pkl         # Stored embeddings
└── README.md

