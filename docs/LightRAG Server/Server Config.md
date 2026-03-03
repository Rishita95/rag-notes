# 3. Configuring the Server

1. Create folders

    1. Open Finder and go to Applications.
    2. Create a folder named LightRAG Server.
    3. Inside LightRAG Server, create two empty folders: inputs and rag_storage.
        1. inputs: where you drop your PDFs, text files, etc.
        2. rag_storage: where LightRAG will store its database and indexes.

2. Create a configuration file

    1. Open Antigravity and create a new blank document.
    2. Paste the following configuration:
    3. Save the file as .env in the LightRAG Server folder.

         --- General Server Settings ---
        HOST=127.0.0.1
        PORT=8020
        WEBUI_TITLE=My Personal RAG
        WEBUI_DESCRIPTION=A private RAG system powered by LightRAG

         --- Directory Settings (Optional) ---
         INPUT_DIR=/Users/your-username/LightRAG/inputs

        > [!TIP]
        > **Directory Setup:** We follow the official LightRAG standard by placing all database files inside the `rag_storage` folder. This keeps the root of `~/LightRAG` tidy, containing only your `.env` settings and the `inputs` folder.

         --- Indexing Performance ---
        MAX_ASYNC=4
        MAX_PARALLEL_INSERT=2
        CHUNK_SIZE=1200
        CHUNK_OVERLAP_SIZE=100

         ==========================================
         CHOOSE ONE PROVIDER BELOW
         ==========================================

         --- Option 1: LITELLM PROXY (Recommended) ---
         Use this for both LLM and Embeddings via your local LiteLLM Gateway
        LLM_BINDING=openai
        LLM_BINDING_HOST=http://localhost:4000/v1
        LLM_MODEL=gemini/gemini-2.5-flash
        LLM_BINDING_API_KEY=any-string-will-work

        EMBEDDING_BINDING=openai
        EMBEDDING_BINDING_HOST=http://localhost:4000/v1
        EMBEDDING_MODEL=gemini/gemini-embedding-001
        EMBEDDING_DIM=3072
        EMBEDDING_BINDING_API_KEY=any-string-will-work

         --- Option 2: OLLAMA ---
         LLM_BINDING=ollama
         LLM_BINDING_HOST=http://localhost:11434
         LLM_MODEL=mistral-nemo:latest
         OLLAMA_LLM_NUM_CTX=32768
         EMBEDDING_BINDING=ollama
         EMBEDDING_BINDING_HOST=http://localhost:11434
         EMBEDDING_MODEL=bge-m3:latest
         EMBEDDING_DIM=1024

         --- Option 3: OPENAI ---
         LLM_BINDING=openai
         LLM_BINDING_HOST=https://api.openai.com/v1
         LLM_MODEL=gpt-4o
         LLM_BINDING_API_KEY=sk-your-api-key-here

         --- OpenAI (Embedding) ---
         EMBEDDING_BINDING=openai
         EMBEDDING_MODEL=text-embedding-3-large
         EMBEDDING_DIM=3072
         EMBEDDING_SEND_DIM=false
         EMBEDDING_TOKEN_LIMIT=8192
         EMBEDDING_BINDING_HOST=https://api.openai.com/v1
         EMBEDDING_BINDING_API_KEY=sk-your-api-key-here

         --- Option 4: GEMINI ---
         LLM_BINDING=gemini
         LLM_MODEL=gemini-2.0-flash
         LLM_BINDING_HOST=https://generativelanguage.googleapis.com
         LLM_BINDING_API_KEY=your-gemini-api-key-here
         EMBEDDING_BINDING=gemini
         EMBEDDING_MODEL=gemini-embedding-001
         EMBEDDING_BINDING_HOST=https://generativelanguage.googleapis.com
         EMBEDDING_BINDING_API_KEY=your-gemini-api-key-here
         EMBEDDING_DIM=3072

            3. Replace YOUR_OPENAI_KEY with your actual OpenAI API key.
            4. Save the file as config.json in the LightRAG Server folder.


