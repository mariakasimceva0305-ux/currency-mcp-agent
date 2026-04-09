# Currency MCP Agent

Educational MCP-based assistant for currency workflows, organized as a **tools server + agent orchestration layer**. The project is useful for demonstrating structured tool use, modularity, and local reproducibility.

## Why This Project
Tool-based assistants are easier to reason about when responsibilities are separated:
- the **server** exposes tools,
- the **agent** decides when and how to call them,
- configuration and tests keep the system inspectable.

This repository follows that design.

## Problem Statement
Support currency-related workflows such as querying rates and conversion through a structured assistant interface rather than a single monolithic script.

## Repository Structure
```text
agent/
  agent.py               # orchestration / agent logic
mcp_server/
  server.py              # MCP tools server
config/                  # configuration
tests/                   # test suite
.env.example
Dockerfile
docker-compose.yml
requirements.txt
README.md
```

## Architecture
### MCP Server
Defines and exposes tool functionality.

### Agent Layer
Consumes the tool interface and orchestrates user-facing currency workflows.

### Containerized Runtime
Docker and Compose make it easy to run the project locally and keep dependencies reproducible.

## What This Project Demonstrates
- separation of concerns between tools and orchestration
- a structured approach to agentic workflows
- project layout that is easier to extend than prompt-only demos
- testable local setup for experiments with tool invocation

## When This Design Makes Sense
This pattern is useful when you want:
- explicit tool boundaries
- easier debugging of tool calls
- extensibility for new tools
- clearer architecture than a notebook or one-file prototype

## Running Locally
```bash
python -m venv .venv
source .venv/bin/activate  # Linux / macOS
pip install -r requirements.txt
python mcp_server/server.py
python agent/agent.py
```

Or with Docker:
```bash
docker compose up --build
```

## Evaluation Ideas
For a project like this, good evaluation is less about one ML score and more about system behavior:
- tool call correctness
- response consistency
- failure handling when tools are unavailable
- ease of extension with new tools
- latency of the full workflow

## Suggested Next Improvements
- add a trace log for tool selection and responses
- document tool schemas and expected inputs/outputs
- include failure mode examples in the README
- add retry / fallback logic for unreliable tools
- separate business logic from orchestration even further if the project grows

## Limitations
- educational scope rather than production agent platform
- the value of agent orchestration depends on task complexity
- not every currency use case requires an agent; sometimes a direct API wrapper is enough

## Takeaway
The strength of this repository is not “agent hype.” It is the more grounded engineering point: **tooling should be modular, inspectable, and easy to extend**.
