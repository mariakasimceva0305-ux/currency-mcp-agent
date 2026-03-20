# Currency-mcp-agent

Educational MCP-based currency assistant with a tool server and agent layer.

## Repository Contents

- `mcp_server/server.py` - MCP server with currency tools.
- `agent/agent.py` - agent interface for query handling.
- `config/tools.json` - MCP tool configuration.
- `tests/test_mcp_server.py` - server tests.
- `Dockerfile` and `docker-compose.yml` - container run configuration.

## Implemented Functionality

The repository code provides:

- exchange rate retrieval,
- currency conversion,
- available currency listing,
- agent-side invocation of MCP tools.
