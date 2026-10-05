# HeyJarvis 🤖

> **Status: In Active Development**

HeyJarvis is an AI-powered WhatsApp assistant built by [heyjarvis.ai](https://heyjarvis.ai). It connects businesses to their customers through intelligent, conversational automation on WhatsApp — handling support, bookings, FAQs, and more, 24/7.

This repo contains the core WhatsApp agent platform. It is currently under active development, and features are evolving rapidly. Expect breaking changes until the first stable release.

## What it does

- **WhatsApp-native automation**: Meets users where they already are.
- **Conversational AI**: Stateful, tool-using agent built on LangGraph.
- **Extensible tool layer**: Clean MCP-based architecture for adding new capabilities.
- **Persistent memory**: Conversation history survives restarts.

## Architecture

- **Agent** (`src/app`): LangGraph `StateGraph` managing conversation flow, tool routing, and message queue.
- **MCP Server** (`src/heyjarvis_mcp`): Exposes business logic as tools + system prompts for the agent.
- **Shared Library** (`src/shared`): Database models and data access used by both.

```
WhatsApp Message → Webhook → Queue → Agent (LangGraph) → MCP Tools → Database
```

## Tech stack

- Python 3.13+
- FastAPI
- LangChain + LangGraph
- MCP
- SQLite

## Getting started

### Prerequisites

- Python 3.13+
- [uv](https://github.com/astral-sh/uv)

### Installation

```sh
git clone https://github.com/divyanshu652/Heyy_jarvis_Whatsapper.git
cd Heyy_jarvis_Whatsapper
uv sync
cp example.env .env
```

Edit `.env` and add your API credentials.

### Running

```sh
uv run server
```

### Verify MCP tools

```sh
uv run src/app/mcp_client.py
```

## Project structure

```
.
├── data/
│   └── heyjarvis_app.db
├── src/
│   ├── app/
│   │   ├── agent.py
│   │   ├── main.py
│   │   ├── mcp_client.py
│   │   └── whatsapp.py
│   ├── heyjarvis_mcp/
│   │   └── server.py
│   └── shared/
│       ├── db.py
│       ├── logger_config.py
│       └── models.py
├── .env
├── example.env
├── pyproject.toml
└── README.md
```

## Contributing

Contributions are welcome.

1. Fork the Project
2. Create your Feature Branch
3. Commit your Changes
4. Push to the Branch
5. Open a Pull Request

## License

MIT — see [LICENSE.txt](LICENSE.txt).
