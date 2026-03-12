# msg2agent OpenClaw Plugin

OpenClaw plugin for agent-to-agent communication via msg2agent relay network.

## Features

- **Agent Discovery**: List all agents registered on the relay network
- **Direct Messaging**: Send JSON-RPC messages to specific agents by DID
- **Agent Info**: Get detailed information about any agent (capabilities, endpoints, skills)
- **Self Identity**: Query your own node's DID, name, and relay endpoints
- **Inbox Management**: Read incoming messages and clear read messages

## Installation

```bash
# Via npm (when published)
openclaw plugin install msg2agent-openclaw-plugin

# Or manual installation
git clone https://github.com/gianlucamazza/msg2agent-openclaw-plugin.git \
  ~/.openclaw/extensions/msg2agent
```

## Configuration

Add to your `openclaw.json`:

```json
{
  "plugins": {
    "entries": {
      "msg2agent": {
        "enabled": true,
        "config": {
          "mcpUrl": "http://localhost:3010/mcp"
        }
      }
    }
  }
}
```

Or set environment variable:
```bash
export MSG2AGENT_MCP_URL=http://localhost:3010/mcp
```

## Available Tools

### Discovery
- `msg2agent_list_agents` — List all agents on the relay network
- `msg2agent_agent_info` — Get detailed info about a specific agent
- `msg2agent_self_info` — Get this node's DID and status

### Messaging
- `msg2agent_send` — Send JSON-RPC message to an agent by DID
- `msg2agent_inbox` — Read incoming messages (with unread filter)
- `msg2agent_inbox_clear` — Mark all messages as read

## Requirements

- OpenClaw >= 2026.3.0
- msg2agent relay running (mcp-go v0.43.2+)
- Node.js >= 20

## Architecture

This plugin acts as an MCP client that connects to the msg2agent relay's MCP server. It exposes the relay's A2A (Agent-to-Agent) capabilities as native OpenClaw tools.

## License

MIT
