# Security Notes

## Credentials

Never commit Hugging Face tokens, API keys, passwords, or other credentials.

The polished notebook uses `huggingface_hub.notebook_login()` rather than embedding a token in source code.

If an older copy contains an exposed credential, revoke or rotate that credential before publishing.

## User data

The prototype stores conversation history under `USERS/`, which is ignored by Git.

Do not commit conversation histories or other personal/sensitive information.

## Knowledge-base data

The current repository does not include the ChromaDB vector store. If a future version adds it, review the source documents for privacy, licensing, redistribution rights, and repository-size implications.

## Important reminder

`.gitignore` reduces accidental commits, but it is not a security boundary. Always inspect the files you are about to commit.
