# Code with Claude - Microsoft Foundry Workshop

Build an AI agent with **Microsoft Foundry** and the **Microsoft Agent Framework** that uses a Foundry-hosted model and calls tools through an MCP server.

## What you will build

A simple cupcake-ordering agent that:

- Uses a model deployed in Microsoft Foundry, with support for **Claude Sonnet 4.6** or **GPT** deployments
- Follows a custom persona via a system prompt (`instructions.md`)
- Calls live tools from the **Cupcake Store MCP server**

## Repository layout

```
.
├── workshop/
│   └── workshop.md              # Step-by-step lab manual
├── agent-framework/             # Your working folder for the workshop
│   ├── agent.py                 # Completed workshop implementation
│   ├── instructions.md          # System prompt for the workshop agent
│   └── requirements.txt         # Python dependencies
└── sample/
    ├── .env.sample              # Shareable environment template
    ├── agent.py                 # Final reference implementation
    ├── instructions.md          # System prompt for the agent
    └── requirements.txt         # Python dependencies
```

## Prerequisites

- An Azure subscription with access to **Microsoft Foundry**
- A deployed model, such as `claude-sonnet-4-6` or `gpt-5-1`
- Python 3.10+

## Quick start

1. Follow the [workshop lab manual](workshop/workshop.md) to build the agent step-by-step in `agent-framework/`.
2. Or, to run the finished reference agent directly:

   ```bash
   cd sample
   pip install -r requirements.txt
    cp .env.sample .env
    # Edit .env with your Foundry deployment values
   python agent.py
   ```

On Windows PowerShell, use:

```powershell
cd sample
pip install -r requirements.txt
Copy-Item .env.sample .env
# Edit .env with your Foundry deployment values
python agent.py
```

## Environment variables

Local `.env` files are ignored by git. Use `sample/.env.sample` as the template, copy it to `.env`, and fill in the values for the provider you want to use.

### Anthropic/Claude on Microsoft Foundry

| Variable | Description |
|---|---|
| `MODEL_PROVIDER` | Set to `anthropic` or omit it; Anthropic is the default. |
| `FOUNDRY_ENDPOINT` | Target URI of your Foundry deployment, e.g. `https://<resource>.services.ai.azure.com/anthropic` |
| `FOUNDRY_API_KEY` | API key for the Foundry deployment |
| `FOUNDRY_MODEL_DEPLOYMENT` | Deployment name (e.g. `claude-sonnet-4-6`) |

### OpenAI/GPT on Microsoft Foundry

| Variable | Description |
|---|---|
| `MODEL_PROVIDER` | Set to `openai`. |
| `FOUNDRY_PROJECT_ENDPOINT` | Foundry project or resource endpoint, e.g. `https://<resource>.cognitiveservices.azure.com/` |
| `FOUNDRY_MODEL_DEPLOYMENT` | Deployment name (e.g. `gpt-5-1`) |

The OpenAI/GPT path uses `DefaultAzureCredential`, so sign in with Azure CLI or another supported Azure identity before running the sample.
