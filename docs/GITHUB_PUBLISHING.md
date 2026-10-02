# GitHub Publishing and Updating Guide

This guide is for a first-time Git/GitHub user.

## The basic workflow

```text
Edit files
   ↓
git status
   ↓
git add .
   ↓
git commit -m "Describe the change"
   ↓
git push
   ↓
GitHub
```

## Part 1 — First publication

### 1. Create a GitHub repository

Suggested name:

```text
Digiwise-RAG-Chatbot
```

Because this prepared project already contains a README, do not create a second README when creating the remote repository.

Do not upload the older notebook that contained the exposed Hugging Face credential.

### 2. Open Git Bash/PowerShell in the project folder

```bash
cd path/to/Digiwise-RAG-Chatbot
```

### 3. Initialize Git

```bash
git init
```

### 4. Use `main` as the branch

```bash
git branch -M main
```

### 5. Inspect the project

```bash
git status
```

Look carefully for credentials, private data, notebook outputs, and large files.

### 6. Stage the files

```bash
git add .
```

Then inspect again:

```bash
git status
```

### 7. Create the first commit

```bash
git commit -m "Initial Digiwise RAG chatbot project"
```

### 8. Connect Git to GitHub

Use the repository URL GitHub gives you:

```bash
git remote add origin https://github.com/YOUR-USERNAME/Digiwise-RAG-Chatbot.git
```

Check it:

```bash
git remote -v
```

### 9. Push

```bash
git push -u origin main
```

After this first push, future pushes normally use:

```bash
git push
```

## Part 2 — Updating the project later

After editing the notebook or documentation:

```bash
git status
git add .
git commit -m "Describe the change"
git push
```

Example:

```bash
git add Rag_ChatBot_llama.ipynb
git commit -m "Improve Digiwise chatbot interface"
git push
```

## Part 3 — Safer routine before every push

Use:

```bash
git status
git diff
git add .
git status
git commit -m "Describe the change"
git push
```

For notebooks, review cell outputs especially carefully.

## Part 4 — Common situations

### Nothing to commit

If Git says:

```text
nothing to commit, working tree clean
```

there are no detected changes since the last commit.

### Remote already exists

Check:

```bash
git remote -v
```

If the URL is wrong:

```bash
git remote set-url origin https://github.com/YOUR-USERNAME/Digiwise-RAG-Chatbot.git
```

### Undo an uncommitted file change

First inspect:

```bash
git diff
```

If you are certain you want to discard the uncommitted change:

```bash
git restore path/to/file
```

This discards the local change to that file.

## Part 5 — If a secret is accidentally committed

1. Revoke or rotate the credential immediately.
2. Remove the secret from the project.
3. Do not assume deleting the current file removes the secret from Git history.
4. Review and clean the Git history as appropriate before considering the repository safe.

For the old Digiwise notebook, the previously exposed Hugging Face credential should not be reused.

## Part 6 — Useful commit messages

Good:

```text
Initial Digiwise RAG chatbot project
Update chatbot prompt
Improve Gradio interface
Document ChromaDB setup
Update project dependencies
```

Avoid vague messages such as:

```text
changes
update
stuff
```

## Final pre-publication checklist

- [ ] No API keys or access tokens
- [ ] No private conversations
- [ ] No confidential documents
- [ ] No unintended large files
- [ ] README is present
- [ ] requirements.txt is present
- [ ] .gitignore is present
- [ ] License has been reviewed
- [ ] ChromaDB dependency is explained
- [ ] Notebook has been reviewed from a clean runtime
