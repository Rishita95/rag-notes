# LiteLLM Configuration

LiteLLM can be configured using environment variables or a configuration file primarily via a config.yaml file for the proxy server., which defines models, routing, and server settings.

## Basic Structure

The config file has four main sections:

> model_list: Defines available models and their provider details. Each entry maps a user-facing model name to a specific provider and model.
> litellm settings: LiteLLM core behaviour (logging, caching, callbacks).
> router_settings: Load balancing, fallbacks across models.
> general_settings: Proxy server options (master key, alerts, etc)

# 1. Creating the Config File

> Open Finder and go to your home folder.
> Create a folder named .litellm
> Inside .litellm folder, create a file named config.yaml
> Add the following content to config.yaml:

# 2. Config template

The below template sets up a cloud model (Gemini) and a local model (Ollama). Copy and paste this into your config.yaml file:

```yaml
# ~/.litellm/config.yaml

litellm_settings:
  drop_params: True

model_list:
  # A local model using Ollama (Wildcard route for ANY Ollama model)
  - model_name: ollama/*
    litellm_params:
      model: ollama/*
      api_base: "http://localhost:11434" 

  # A cloud model using Gemini (Wildcard route for ANY Gemini model)
  - model_name: gemini/*
    litellm_params:
      model: gemini/*
      api_key: "os.environ/GEMINI_API_KEY"
```

# 3. Set your API Key

The config file searches your Mac's environment for the GEMINI_API_KEY variable. We need to save it to your Terminal profile so its available every time you open terminal.

> Open Finder and go to your home folder.
> Press Command + Shift + . to show hidden files.
> Find .zshrc file. If not found, create it.
> Open .zshrc file in a text editor or Antigravity.
> Add the following line at the end of the file, replacing your-key-here with your actual Gemini API key:

```bash
export GEMINI_API_KEY="your-key-here"
```

> Save the file and close it.

