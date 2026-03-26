# Intelligent Document Q&A Assistant (Agentic RAG)

## Overview
This project implements an intelligent document assistant that allows users to upload PDF documents and interact with them using natural language queries.
The system combines **Retrieval-Augmented Generation (RAG)** with a **multi-tool agent architecture** to generate accurate, context-aware, and explainable responses grounded in the document.
---
## Key Features
- PDF document ingestion and processing  
- Semantic search using vector embeddings  
- Retrieval-Augmented Generation for grounded answers  
- Hybrid agent-based query routing  
- Multiple tools for different query types  
- Page-level citations for explainability  
- Interactive UI using Gradio  

---
## Core Components
### 1. Document Ingestion
- PDFs are loaded using PyMuPDF  
- Text is cleaned to remove formatting noise  
- Documents are split into overlapping chunks  
- Metadata such as page number and chunk ID is stored  
---
### 2. Embeddings and Vector Database
- Uses `sentence-transformers/all-MiniLM-L6-v2`  
- Stores embeddings in FAISS  
- Enables semantic search instead of keyword matching  
--
### 3. Retrieval-Augmented Generation (RAG)
1. Convert query into embedding  
2. Retrieve relevant chunks from FAISS  
3. Pass context to LLM  
4. Generate grounded response  
---
### 4. Agent-Based Routing
The system uses a **hybrid routing mechanism**:
- Rule-based routing for clear intents (summary, critique)  
- LLM-based classification for ambiguous queries  
This improves both stability and flexibility.
---
## Tools Implemented
### Summarizer Tool
- Generates overview of the document  
- Uses retrieval-based summarization  
- Outputs summary with citations  
### General Q&A Tool
- Answers specific questions  
- Uses RAG pipeline  
- Provides citations with page and chunk references  
### Critique Tool (Additional Feature)
- Evaluates strengths, weaknesses, and bias  
- Demonstrates analytical reasoning  
---
## Explainability
- Displays which tool handled the query  
- Provides page-level citations for all responses  
---
## Technologies Used
- LangChain  
- LangChain Community  
- Sentence Transformers  
- FAISS  
- PyMuPDF  
- OpenRouter API  
- Gradio  

---
## Additional Enhancements

- Hybrid intent classification (rule-based + LLM)  
- Retrieval-based summarization  
- Page-aware citations using metadata  
- Text preprocessing for better embeddings  
- Modular multi-tool architecture  
---
## Installation
```bash
pip install langchain langchain-community sentence-transformers faiss-cpu pymupdf gradio
```

## Setup
Set your OpenRouter API key:
import os
os.environ["OPENROUTER_API_KEY"] = "your_api_key"
Running the Project

Option 1: Notebook
Open the notebook
Run all cells
Launch the Gradio interface

Option 2: Script
python app.py
Usage
Upload a PDF document
Click Process Document
Ask queries such as:
"Give me an overview of the document"
"What does the document say about APIs?"
"Critique this document"

### Example Queries

Summarization
Summarize the document
Give an overview of the report

Q&A
What are the key responsibilities mentioned?
What does the document say about APIs?

Analysis
Critique this document
What are the strengths and weaknesses?

## Future Improvements
Multi-document support
Hybrid retrieval (BM25 + vector search)
Sentence-level evidence highlighting
Persistent vector storage
Advanced agent frameworks

## Conclusion
This project demonstrates a practical implementation of an agentic RAG system that combines retrieval, reasoning, and tool-based execution.
The system is designed for accuracy, explainability, and scalability, making it suitable for real-world document intelligence applications.
