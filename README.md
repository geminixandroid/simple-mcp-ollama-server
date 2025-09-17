# simple-mcp-ollama-server 🚀

A minimal MCP server for remote Ollama access from VS Code\Rider via Continue plugin. Running on a Mini PC with Intel N150, 16GB RAM, Windows 11.

## Hardware Setup 🖥️

- **Device:** Mini PC (Intel N150) 
- **Memory:** 16GB RAM 🧠
- **OS:** Windows 11 🪟
- **Purpose:** Dedicated Ollama server for remote LLM access 🤖

## Quick Start ⚡
### 1. Run Ollama (on Mini PC) 🔧

```bash
# Install and run Ollama, then pull a model
ollama pull Gamma3
ollama serve
```

### 2. Run MCP Server (on Mini PC) 🌐

```bash
pip install fastmcp ollama
python mcp-server.py
```
<img width="640" alt="server running" src="https://github.com/user-attachments/assets/32cd09bf-708e-45d7-9cd0-40502e8f6799" />

### 3. Continue plugin config.yaml (Rider, VS Code) ⚙️
```yaml
name: Local Agent
version: 1.0.0
schema: v1
models:
  - name: Qwen3 1.7B
    provider: ollama
    model: qwen3:1.7b
    apiBase: "http://mini-pc-ip-address:11434"
  - name: Qwen2.5-Coder 1.5B
    provider: ollama
    model: qwen2.5-coder:1.5b-base
    apiBase: "http://mini-pc-ip-address:11434"
    roles:
      - autocomplete

rules:
  - name: Custom rule
    rule: Some custom rules text

mcpServers:
  - name: My MCP server
    type: streamable-http
    url: http://mini-pc-ip-address:8000/mcp
    schema: 0.1.0

# Context providers define what information the assistant can access 📁
context:
  - provider: code
  - provider: docs
  - provider: diff
  - provider: terminal
  - provider: problems
  - provider: folder
  - provider: codebase
  - provider: mcp
```

> **Note:** 📍 Replace `mini-pc-ip-address` with your Mini PC's local IP address (e.g., `192.168.1.100`). Ensure both devices are on the same network 🌐.
