# Assignment_1_Multimedia
# Multi-Modal Document Intelligence (RAG-Based QA System)

##  Overview
This repository implements a **Multi-Modal Retrieval-Augmented Generation (RAG)** system designed to parse, index, and query complex documents.

Unlike traditional text-only QA systems that depend on OCR (which often loses layout, tables, and visual structure), this system uses **Vision-Language Models (VLMs)** to process documents as full-page images, preserving spatial and visual semantics.

---

##  Key Features

-  **Multi-Modal Ingestion**  
  Directly processes PDF pages as high-fidelity images, avoiding OCR loss.

-  **Unified Embedding Space**  
  Uses **ColPali (v1.3)** to generate multi-modal page embeddings.

-  **Late-Interaction Retrieval**  
  Powered by **Qdrant** with MaxSim-based multi-vector search.

-  **Context-Grounded QA**  
  Uses **Gemini Flash** to answer strictly based on retrieved visual context.

-  **Source Attribution**  
  Provides exact page-level citations for every answer.

---

##  Architecture

### 1. Ingestion Pipeline
- `pdf2image` converts PDFs into 150 DPI page images.

### 2. Embedding Pipeline
- `ColPaliProcessor` + `ColPali` generate multi-vector embeddings.

### 3. Vector Database
- `Qdrant` stores embeddings using cosine similarity + multi-vector support.

### 4. Generation & Interface
- `Gradio` UI retrieves Top-K pages and sends them to Gemini with strict grounding prompts.
