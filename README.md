# simple-mcp-ollama-server

A minimal MCP server for remote Ollama access from VS Code. Running on a Mini PC with Intel N150, 16GB RAM, Windows 11.

## Hardware Setup

- **Device:** Mini PC (Intel N150)
- **Memory:** 16GB RAM
- **OS:** Windows 11
- **Purpose:** Dedicated Ollama server for remote LLM access

## Quick Start

### 1. Run Ollama (on Mini PC)

```bash
# Install and run Ollama, then pull a model
ollama pull Gamma3
ollama serve
```

### 2. Run MCP Server (on Mini PC)

```bash
pip install fastmcp ollama
python mcp-server.py
```

### 3. Connect from VS Code (Remote Client)

Add to your VS Code settings (`settings.json`):

```json
"mcp.servers": {
    "mini-pc-ollama": {
        "url": "http://mini-pc-ip-address:8000/mcp",
        "type": "http"
    }
}
```

> **Note:** Replace `mini-pc-ip-address` with your Mini PC's local IP address (e.g., `192.168.1.100`). Ensure both devices are on the same network.
