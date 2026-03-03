# 4.Run the Server

1. Start the Server

    1. Open Terminal.
    2. Run this command:

        cd ~/LightRAG && lightrag-server

    3. Wait a few seconds until you see Uvicorn running on http://127.0.0.1:8020.

2. Test the Server

    1. Open your web browser and go to http://127.0.0.1:8020.
    2. You should see the LightRAG UI.
    3. Click on "Upload Files" and select a PDF or text file.
    4. Click on "Index" to index the file.
    5. Click on "Chat" and ask a question about the file.

3. Stop the Server

    1. Open Terminal.
    2. Press Ctrl + C to stop the server.
    3. You should see the Uvicorn server stopped message.   