# Project Structure

```text
Digiwise-RAG-Chatbot/
├── README.md
├── Rag_ChatBot_llama.ipynb
├── requirements.txt
├── .gitignore
├── LICENSE
├── data/
│   └── README.md
├── assets/
│   └── README.md
└── docs/
    ├── SETUP.md
    ├── PROJECT_STRUCTURE.md
    ├── GITHUB_PUBLISHING.md
    └── SECURITY.md
```

## Root files

- `README.md` — public overview and quick orientation.
- `Rag_ChatBot_llama.ipynb` — current implementation notebook.
- `requirements.txt` — packages used by the notebook.
- `.gitignore` — files Git should not commit.
- `LICENSE` — project license.

## Folders

### `data/`

Documents the external/local knowledge-base requirement. The current ChromaDB store is not included.

### `assets/`

Reserved for approved screenshots and diagrams.

### `docs/`

Longer documentation:

- `SETUP.md` — how to run the project.
- `PROJECT_STRUCTURE.md` — why the repository is organized this way.
- `GITHUB_PUBLISHING.md` — how to publish and update the repository.
- `SECURITY.md` — credentials and data-safety notes.

## Intentionally not included

The repository does not currently contain:

- a source-document ingestion pipeline
- a separate Python application package
- automated tests
- production deployment configuration
- a distributed ChromaDB knowledge base

Those should only be added when they actually exist and can be documented.
