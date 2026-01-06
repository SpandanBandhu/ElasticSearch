# APOD Search and Analytics with Elasticsearch

Backend-only search and analytics service built with Python and Elasticsearch.  
The project uses separate indices for raw documents, n‑gram based search, and embedding-based semantic search, and is designed to be run via Docker Compose.

---

## Features

- Full-text search over APOD titles and explanations
- N‑gram based search (autocomplete / partial matching) using an edge n‑gram tokenizer
- Embedding-based semantic search (e.g., using sentence-transformers)
- Time-series analytics using Elasticsearch aggregations (for example, documents per year via date_histogram)
- Clear index separation:
  - `apod_raw` for raw documents
  - `apod_n_gram` for n‑gram search
  - `apod_embedding` for vector search
- API documentation and testing through Swagger
- Docker-based local environment

---

## Architecture Overview

### Indices

- `apod_raw`  
  Stores the original APOD documents with fields such as `title`, `explanation`, and `date`. This index is useful for normal search and for having a clean source of truth.

- `apod_n_gram`  
  Uses a custom analyzer with an `edge_ngram` tokenizer to support prefix and partial matching on titles and explanations. This is suited for search-as-you-type and autocomplete-like functionality.

- `apod_embedding`  
  Stores vector embeddings of documents (for example, produced by a sentence-transformers model) to support semantic similarity search.


