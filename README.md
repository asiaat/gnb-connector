# GNB Connector — Google Notebook Connector

A connector that lets AI agents and LLM-powered applications interact with **Google Notebooks** — Google's browser-based notebook environment (including Colab-style notebooks).

## Overview

The **GNB Connector** bridges AI agents with Google Notebooks. Once connected, an agent can:

- List the notebooks available to the user
- Read notebook metadata and cell contents (code, markdown, raw)
- Execute notebook cells / run notebooks
- Retrieve execution outputs and errors

## Features

- 🔍 **List notebooks** — enumerate notebooks associated with a Google account
- 📖 **Read notebooks** — fetch metadata and cell structure
- 🧠 **Agent-friendly cell access** — pull code/markdown cells with stable identifiers
- ▶️ **Execute notebooks** — run code cells and capture outputs
- ⚠️ **Error capture** — surface execution errors and stack traces to the agent

## How It Works

1. The connector authenticates against Google's notebook APIs using OAuth 2.0 / service credentials.
2. The agent retrieves a notebook, identifies cell IDs, and issues execution commands.
3. Execution results (stdout, stderr, outputs) are returned to the agent in a structured format.

## Installation

```bash
pip install gnb-connector
```

## Configuration

| Variable | Description |
|---|---|
| `GNB_CLIENT_ID` | Google OAuth client ID |
| `GNB_CLIENT_SECRET` | Google OAuth client secret |
| `GNB_PROJECT_ID` | Google Cloud project ID (for service auth) |
| `GNB_OAUTH_SCOPES` | Requested OAuth scopes |

## Usage

```python
from gnb_connector import GoogleNotebookClient

client = GoogleNotebookClient()

notebooks = client.list_notebooks()
nb = client.get_notebook(notebooks[0].id)
cells = client.get_cells(nb.id)
result = client.run_cell(cells[1].id)
```

## Roadmap

- [ ] Notebook CRUD (create / update / delete)
- [ ] Cell-level execution status tracking
- [ ] Scheduled / background notebook runs
- [ ] Multi-user / multi-tenant support

## License

MIT
