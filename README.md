# SQuAD Vector Database for Semantic Search

A vector database implementation that enables semantic search over the SQuAD dataset. Instead of keyword matching, it understands what you're actually asking and finds relevant answers based on meaning.

## What it does

Give it a question like "Who invented the telephone?" and it'll find paragraphs mentioning Alexander Graham Bell - even if your exact words don't appear in the text. That's semantic search.

The system:
- Loads the SQuAD dataset (streaming to save memory)
- Converts text into vector embeddings using Sentence-Transformers
- Stores them in ChromaDB for fast similarity search
- Finds the most relevant documents based on query meaning

## How it works

Traditional search matches keywords. This matches **meaning**.

Every document and query gets converted into a high-dimensional vector (embedding). The database then finds documents whose vectors are closest to your query vector using cosine similarity. It's like asking "what documents are most similar in meaning to my question?"

## Setup

**Requirements:**
- Python 3.8+
- Google Colab or local Python environment

**Install dependencies:**
```bash
pip install datasets sentence-transformers chromadb
```

The script handles this automatically when you run it.

## Usage

**Quick start:**
```bash
python vector_database.py
```

The script will:
1. Load the SQuAD dataset (streamed, not all at once)
2. Remove duplicate documents
3. Generate embeddings for each document
4. Populate ChromaDB with the vectors
5. Run a sample semantic search query

**Test your own queries:**
```bash
python vector_database_test.py
```

**Example output:**
See `vector_database_results.py` for sample query results.

## Project Structure

```
├── vector_database.py          # Main implementation
├── vector_database_test.py     # Query testing script
├── vector_database_results.py  # Example results
└── README.md
```

## Key Features

- **Semantic search** - Finds meaning, not just keywords
- **Deduplication** - Removes duplicate documents automatically
- **Memory efficient** - Uses streaming to handle large datasets
- **Fast retrieval** - ChromaDB handles similarity search efficiently
- **Pre-trained models** - Uses Sentence-Transformers (no training needed)

## Tech Stack

- **Datasets** (Hugging Face) - SQuAD dataset loading
- **Sentence-Transformers** - Text to vector embeddings
- **ChromaDB** - Lightweight vector database for storage and retrieval

## Why I built this

Wanted to explore how vector databases enable semantic search at scale. Traditional keyword search breaks down when users phrase questions differently than how information is written - vector embeddings solve this by capturing meaning rather than exact matches.

Also, it's a building block for RAG (Retrieval-Augmented Generation) systems where you need to find relevant context before generating answers.

## Example

**Query:** "Who invented the telephone?"

**Traditional keyword search:** Might miss documents that don't contain "invented" or "telephone"

**Vector search:** Finds documents about Alexander Graham Bell and early telephony even with different wording, because the **meaning** matches.

## Questions?

Open an issue or reach out on [LinkedIn](https://www.linkedin.com/in/maitri-dodiya-a054012a4/)

---

Built to explore semantic search and vector databases in practice.
