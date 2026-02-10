# Getting Started

To set up a documentation site like this, we used `uv` for dependency management and `mkdocs-material` for the theme.

## 1. Initialize Project

First, create a new project directory and initialize it with `uv`:

```bash
mkdir -p ~/RAGprojects
cd ~/RAGprojects
uv init rag-notes --no-package
cd rag-notes
```

## 2. Install Dependencies

Add `mkdocs` and `mkdocs-material`:

```bash
uv add mkdocs mkdocs-material
```

## 3. Create MkDocs Components

Initialize the MkDocs structure:

```bash
uv run mkdocs new .
```

This creates `mkdocs.yml` and `docs/index.md`.

## 4. Run Development Server

To see your changes in real-time:

```bash
uv run mkdocs serve
```
