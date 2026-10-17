# RAG From Scratch

A hands-on Retrieval-Augmented Generation (RAG) project that lets you ask
questions about PDF documents and get grounded answers with sources.

## Features
- Loads and chunks PDF documents
- Generates embeddings locally with sentence-transformers (384-dim)
- Stores and searches vectors with a similarity score threshold
- Generates answers with Google Gemini via LangChain
- Returns the answer, source file and page, similarity scores, and a
  confidence value
- Says so when the answer isn't in the retrieved context

## How it works
1. **Ingest:** PDFs are loaded and split into chunks
2. **Embed:** each chunk is converted to a vector and stored
3. **Retrieve:** the query is embedded and the top-k similar chunks are fetched
4. **Generate:** the chunks plus the question are sent to the LLM, which
   answers using only that context

## Setup
```bash
git clone https://github.com/<your-username>/rag-from-scratch.git
cd rag-from-scratch
python -m venv .venv
.venv\Scripts\activate        # Windows
pip install -r requirements.txt
cp .env.example .env          # then add your GOOGLE_API_KEY
```

## Usage
```python
result = rag_advanced("What is attention mechanism?", rag_retriever, llm, top_k=3)
print(result["answer"])
print(result["sources"])
```

## Tech stack
Python, LangChain, Google Gemini, sentence-transformers, (your vector store)

## Notes
Built as a learning project to understand each RAG component end to end.