# Running the LiteLLM Proxy Server

Since all settings and keys are saved in your config and .zshrc file, you can start the server by running the following command in your terminal:

## 1. Start the Server

> Open a new Terminal.
> Run the following command to start the server:

```bash
litellm --config ~/.litellm/config.yaml
```

> The server will start running and you will see the following output:

```text
python-dotenv could not parse statement starting at line 9
python-dotenv could not parse statement starting at line 11
python-dotenv could not parse statement starting at line 9
python-dotenv could not parse statement starting at line 11
INFO:     Started server process [1777]
INFO:     Waiting for application startup.

██╗     ██╗████████╗███████╗██╗     ██╗     ███╗   ███╗
██║     ██║╚══██╔══╝██╔════╝██║     ██║     ████╗ ████║
██║     ██║   ██║   █████╗  ██║     ██║     ██╔████╔██║
██║     ██║   ██║   ██╔══╝  ██║     ██║     ██║╚██╔╝██║
███████╗██║   ██║   ███████╗███████╗███████╗██║ ╚═╝ ██║
╚══════╝╚═╝   ╚═╝   ╚══════╝╚══════╝╚══════╝╚═╝     ╚═╝


#------------------------------------------------------------#
#                                                            #
#           'It would help me if you could add...'           #
#        https://github.com/BerriAI/litellm/issues/new       #
#                                                            #
#------------------------------------------------------------#

Thank you for using LiteLLM! - Krrish & Ishaan


Give Feedback / Get Help: https://github.com/BerriAI/litellm/issues/new


LiteLLM: Proxy initialized with Config, Set models:
    ollama/*
    gemini/*
INFO:     Application startup complete.
INFO:     Uvicorn running on http://127.0.0.1:8020 (Press CTRL+C to quit)
INFO:     127.0.0.1:52552 - "GET / HTTP/1.1" 200 OK
INFO:     127.0.0.1:52552 - "GET /swagger/swagger-ui.css HTTP/1.1" 200 OK
INFO:     127.0.0.1:52553 - "GET /swagger/swagger-ui-bundle.js HTTP/1.1" 200 OK
INFO:     127.0.0.1:52553 - "GET /openapi.json HTTP/1.1" 200 OK
INFO:     127.0.0.1:52552 - "GET /swagger/favicon.png HTTP/1.1" 200 OK 
```

> You will see Uvicorn running on http://127.0.0.1:8020 (Press CTRL+C to quit).

> Your AI proxy is now successfully hosting all your local and cloud models.

## 2. Test the Server

LiteLLM comes with a built-in terminal CLI to easily test your models without writing code.

Keep the server running in one terminal and open a new terminal and follow the below steps to test your models:

### 2.1 List all available models

```bash
curl -s http://127.0.0.1:8020/v1/models | jq '.data |= if length > 3 then .[0:3] + [{"id": "... (\(length - 3) more models hidden)", "object": "model"}] else . end'
```

Example output:

```json
{
  "data": [
    {
      "id": "ollama/*",
      "object": "model",
      "created": 1677610602,
      "owned_by": "openai"
    },
    {
      "id": "gemini/*",
      "object": "model",
      "created": 1677610602,
      "owned_by": "openai"
    },
    {
      "id": "ollama/llama2",
      "object": "model",
      "created": 1677610602,
      "owned_by": "openai"
    },
    {
      "id": "... (88 more models hidden)",
      "object": "model"
    }
  ],
  "object": "list"
}
```

### 2.2 Test with a Cloud Model (Gemini)

```bash
curl -X POST "http://127.0.0.1:8020/v1/chat/completions" \
-H "Content-Type: application/json" \
-d '{
    "model": "gemini/gemini-2.5-flash",
    "messages": [
    {
        "role": "user",
        "content": "Hello, how are you?"
    }
    ]
}'
```

<b>Example output:</b>

```json
{
  "id": "6VqkabzlFIW5juMPo43tuA8",
  "created": 1772378857,
  "model": "gemini/gemini-2.5-flash",
  "object": "chat.completion",
  "choices": [
    {
      "finish_reason": "stop",
      "index": 0,
      "message": {
        "content": "Hello! As an AI, I don't have feelings or physical states in the way humans do, but I am functioning perfectly and ready to assist you.\n\nHow are **you** doing today? What can I help you with?",
        "role": "assistant"
      }
    }
  ],
  "usage": {
    "completion_tokens": 224,
    "prompt_tokens": 7,
    "total_tokens": 231,
    "completion_tokens_details": {
      "reasoning_tokens": 176,
      "text_tokens": 48
    },
    "prompt_tokens_details": {
      "text_tokens": 7
    }
  }
}
```

### 2.3 Test Embeddings

```bash
curl -X POST "http://127.0.0.1:8020/v1/embeddings" \
-H "Content-Type: application/json" \
-d '{
    "model": "gemini/gemini-embedding-001",
    "input": "This request needs no LiteLLM key"
}' | jq '.data[0].embedding |= [.[0], .[1], .[2], "...", "(\(. | length) items)"]'
```

<b>Example output:</b>

```json
{
  "model": "gemini/gemini-embedding-001",
  "data": [
    {
      "embedding": [
        -0.015254181,
        0.018891979,
        0.0023873092,
        "...",
        "(1536 items)"
      ],
      "index": 0,
      "object": "embedding"
    }
  ],
  "object": "list",
  "usage": {
    "completion_tokens": 0,
    "prompt_tokens": 8,
    "total_tokens": 8
  }
}
```

<b>How the jq filter works:</b>

* `|=`: The update operator replaces the value of .data[0].embedding with the array defined on the right.
* `.[0], .[1], .[2]`: Extracts only the first three float values.
* `"..."`: Appends a literal ellipsis string.
* `\(. | length)`: Pipes the original, full embedding array (.) to the length function, calculates the total count (e.g., 3072), and dynamically injects the number into the final string.

### 2.4 Test Image Generation

1. Create the output folders first (if they dont exist)

```bash
mkdir -p ~/Downloads/litellm/images ~/Downloads/litellm/videos
```

2. Generate an Image: Run this command to generate 1 image and save the raw API JSON response into a variable.

```bash
response=$(curl -s -X POST "http://localhost:8020/v1/images/generations" \
-H "Content-Type: application/json" \
-d '{
    "model": "gemini/imagen-4.0-fast-generate-001",
    "prompt": "A minimalist logo of a mountain",
    "size": "1024x1024",
    "n": 1
}')
```

3. Decode and Open Images: Run this loop. It searches the JSON array, decodes every embedded base64 string into a unique PNG file, and opens each one side-by-side.

```bash
count=1
echo "$response" | jq -r '.data[].b64_json' | while read -r b64; do
    output_path=~/Downloads/litellm/images/mountain-logo-$count.png
    echo "$b64" | base64 -D > "$output_path"
    open "$output_path"
    ((count++))
done
```

4. View Clean JSON Metrics: Finally, print the structure of the JSON response to your terminal. This filter hides the massive base64 strings so you can easily review your token usage and execution metadata.

```bash
echo "$response" | jq '.data[].b64_json = ["...", "(base64 image data hidden)"]'
```

<b>Example output:</b>

```json
{
  "created": 1771923595,
  "data": [
    {
      "b64_json": [
        "...",
        "(base64 image data hidden)"
      ],
      "revised_prompt": null,
      "url": null
    }
  ],
  "usage": {
    "total_tokens": 0,
    "input_tokens": 0,
    "output_tokens": 0
  }
}
```

(Note: If you receive a "command not found: jq" error, you can install it via brew install jq).

### 2.5 Test Video Generation

Video generation is an asynchronous process, so it requires a multi-step script instead of a single pipeline.

1. Start Generation: Send the prompt to the Veo model and save the returned id string into a terminal variable.

```bash
video_id=$(curl -s -X POST "http://localhost:8020/v1/videos" \
-H "Content-Type: application/json" \
-d '{
  "model": "gemini/veo-3.1-fast-generate-preview",
  "prompt": "A cat playing with a ball of yarn in a sunny garden"
}' | jq -r '.id')

echo "Processing Video ID: $video_id"
```

2. Check Status: Run this command to poll your proxy. Wait until the status string changes from processing to completed.

```bash
curl -s -X GET "http://localhost:4000/v1/videos/$video_id" | jq
```

<b>Example Output:</b>

```json
{
  "id": "video_bGl0ZWxs...",
  "object": "video",
  "status": "processing",
  "created_at": null,
  "completed_at": null,
  "error": null
}
```

3. Download Video: Once completed, wait a few moments for the video to fully finalize on the servers, then run the /content endpoint to download the generated MP4 file to your Mac.

```bash
sleep 20
curl -s -X GET "http://localhost:4000/v1/videos/$video_id/content" \
  --output ~/Downloads/litellm/videos/cat-yarn.mp4

open ~/Downloads/litellm/videos/cat-yarn.mp4
```