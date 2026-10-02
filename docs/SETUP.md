# Setup and Running Guide

This guide explains what is required before running the Digiwise notebook.

## 1. Enter the project folder

```bash
cd Digiwise-RAG-Chatbot
```

## 2. Optional: create a virtual environment

Windows:

```powershell
python -m venv .venv
.venv\Scripts\activate
```

macOS/Linux:

```bash
python3 -m venv .venv
source .venv/bin/activate
```

Google Colab does not require a local virtual environment.

## 3. Install dependencies

```bash
pip install -r requirements.txt
```

The notebook also contains its own installation cell for notebook/Colab use.

## 4. Use a compatible GPU environment

The current notebook is designed around a 4-bit Llama configuration and raises an error when CUDA is unavailable.

No specific GPU model or minimum VRAM figure is claimed here because the project has not established a formal hardware benchmark.

## 5. Provide the ChromaDB vector store

The notebook does not create the knowledge base.

### Google Colab

The original location is:

```text
/content/drive/MyDrive/chromadb_vectorstore
```

The notebook mounts Google Drive when it detects Colab.

### Local

The default is:

```text
./data/chromadb_vectorstore
```

### Custom location

PowerShell:

```powershell
$env:VECTOR_STORE_PATH="C:\path\to\chromadb_vectorstore"
```

macOS/Linux:

```bash
export VECTOR_STORE_PATH="/path/to/chromadb_vectorstore"
```

## 6. Hugging Face authentication

The notebook uses:

```python
from huggingface_hub import notebook_login
notebook_login()
```

If access to the model requires approval, the account running the notebook must have access.

Never hard-code a Hugging Face token.

## 7. Run the notebook

Open:

```text
Rag_ChatBot_llama.ipynb
```

Run the cells in order. A clean runtime is recommended when testing.

The expected sequence is:

1. install dependencies
2. configure paths and model settings
3. validate the vector store
4. authenticate with Hugging Face
5. import libraries
6. load the language model
7. load the embedding model
8. initialize Digiwise
9. run a test query
10. launch Gradio

## 8. If the vector store is missing

The notebook intentionally stops with an explanatory error. The knowledge base must be supplied, or an ingestion/build pipeline must be added.

The current project does not invent that missing pipeline.
