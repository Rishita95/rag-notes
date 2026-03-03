# 2. How to install LightRAG

    You install and run the LightRAG HTTP server on macOS by installing the lightrag-hku[api] package, setting your LLM/embedding backends via env or config, 
    and then starting lightrag-server. Steps below assume Python 3 is already installed.

##  Install the lightrag-server command-line tool. Open Terminal and run:


uv tool install "lightrag-hku[offline,observability]"

To confirm it installed correctly, run:


which lightrag-server

You should see a path like ~/.local/bin/lightrag-server.


