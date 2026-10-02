# Digiwise — RAG-Powered Digital Literacy Chatbot

Digiwise is a retrieval-augmented generation (RAG) chatbot prototype designed to provide clear, supportive, beginner-friendly guidance on digital literacy.

## Technology used

- **Meta Llama 3.2 3B Instruct** — response generation
- **ChromaDB** — vector retrieval
- **Sentence Transformers** — semantic embeddings
- **Hugging Face Transformers** — model loading and generation
- **LangChain integrations** — embeddings and ChromaDB
- **Gradio** — browser-based interface
- **4-bit NF4 quantization** — reduced model memory requirements

> **Project status:** This repository contains the polished prototype notebook and supporting documentation for learning, experimentation, demonstration, and further development.

## How the RAG workflow works

```text
User Question
      │
      ▼
Query Embedding
      │
      ▼
ChromaDB Vector Search
      │
      ▼
Top-k Relevant Documents
      │
      ▼
System Prompt + Retrieved Context
      │
      ▼
Llama 3.2 3B Instruct
      │
      ▼
Generated Response
      │
      ▼
Local Conversation History
```

The chatbot first retrieves relevant information from an existing ChromaDB knowledge base and then provides that context to the language model when generating a response.

## Repository structure

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

## Important prerequisite: ChromaDB

The current notebook **expects an existing ChromaDB vector store**. It does not currently create the knowledge base, ingest source documents, or build the vector store.

Supported locations are:

- Google Colab default: `/content/drive/MyDrive/chromadb_vectorstore`
- Local default: `./data/chromadb_vectorstore`
- Custom location: set `VECTOR_STORE_PATH`

This is documented in [`data/README.md`](data/README.md).

## Models

Generation model:

```text
meta-llama/Llama-3.2-3B-Instruct
```

Embedding model:

```text
sentence-transformers/all-MiniLM-L6-v2
```

The notebook uses 4-bit NF4 quantization and expects a CUDA-compatible GPU for the current configuration.

## Installation

```bash
pip install -r requirements.txt
```

Then open `Rag_ChatBot_llama.ipynb` and follow the cells in order.

For the complete beginner-friendly procedure, see [`docs/SETUP.md`](docs/SETUP.md).

## Hugging Face authentication

The notebook contains **no Hugging Face access token**. It uses:

```python
from huggingface_hub import notebook_login
notebook_login()
```

Never place a token in a notebook, comment, README, `.env` file that is committed, or other source file.

If a credential was exposed in an older copy of this project, revoke or rotate it before publishing.

## Current configuration

| Setting | Value |
|---|---|
| Generation model | `meta-llama/Llama-3.2-3B-Instruct` |
| Embedding model | `sentence-transformers/all-MiniLM-L6-v2` |
| Retrieved documents (`k`) | `3` |
| Maximum new tokens | `2050` |
| Temperature | `0.7` |
| Top-p | `0.9` |
| Maximum history sent to model | `12` messages |
| Local conversation directory | `./USERS` |

These are the notebook's current settings, not claims that they are experimentally optimal.

## Conversation history

The prototype stores conversation history as JSON files under `USERS/`. That directory is ignored by Git.

The current implementation does **not** provide production-grade authentication, encryption, access control, database management, or privacy controls. Do not use it with sensitive personal information unless appropriate safeguards have been added.

## Limitations

- Retrieval quality depends on the contents of the ChromaDB knowledge base.
- The language model can produce incorrect or incomplete information.
- The current notebook is GPU-oriented.
- Conversation history is stored locally as JSON.
- Gradio `share=False` is used by default; temporary sharing is not production hosting.
- The repository does not yet contain a documented end-to-end knowledge-base ingestion pipeline.

## Future development

Possible next steps include:

1. Add and document the source-document ingestion pipeline.
2. Move reusable chatbot code from the notebook into Python modules.
3. Add automated tests.
4. Add retrieval and response evaluation.
5. Improve conversation storage and user management.
6. Add deployment configuration when the project moves beyond demonstration use.
7. Pin dependency versions after establishing a tested environment.
8. Add approved screenshots and diagrams.

These are future directions; they are not claims about features already implemented.

## Documentation

- [`docs/SETUP.md`](docs/SETUP.md) — setup and execution
- [`docs/PROJECT_STRUCTURE.md`](docs/PROJECT_STRUCTURE.md) — repository organization
- [`docs/GITHUB_PUBLISHING.md`](docs/GITHUB_PUBLISHING.md) — first-time GitHub publishing and future updates
- [`docs/SECURITY.md`](docs/SECURITY.md) — credentials and data safety
- [`data/README.md`](data/README.md) — ChromaDB and data expectations

## License

This project is distributed under the MIT License. See [`LICENSE`](LICENSE).

Review the copyright-holder line in `LICENSE` before public release if your ownership/attribution arrangement requires different wording.

## Release checklist

- [ ] Run the notebook from a clean runtime.
- [ ] Confirm no tokens, passwords, or API keys are present.
- [ ] Confirm no private conversation files are present.
- [ ] Confirm the ChromaDB requirement is documented.
- [ ] Review staged Git files before pushing.
- [ ] Review the license and ownership information.
