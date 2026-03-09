# petstore

## Connect a custom MCP in Cursor

This repository includes a project-scoped MCP config at `.cursor/mcp.json`.
Cursor will load it for this workspace and expose tools from the configured MCP server.

### Quick start (already configured)

1. Open this repo in Cursor.
2. Restart Cursor (or reload the window) so MCP servers are discovered.
3. In chat, ask: "List available MCP tools from `postman`."

The included server uses:

- URL: `https://mcp.postman.com/minimal`
- Authentication: OAuth (recommended, no static key required in config)
- Tool mode: Minimal (switch URL to `https://mcp.postman.com/mcp` for Full mode, or `https://mcp.postman.com/code` for Code mode)

### Use your own custom MCP server

Edit `.cursor/mcp.json` and replace the `postman` entry with your own.

#### Option A: local stdio server

```json
{
  "mcpServers": {
    "my-custom-server": {
      "command": "node",
      "args": ["/absolute/path/to/server.js"],
      "env": {
        "MY_API_KEY": "replace-me"
      }
    }
  }
}
```

#### Option B: remote HTTP/SSE MCP server

```json
{
  "mcpServers": {
    "my-remote-server": {
      "url": "https://your-mcp-host.example.com/sse",
      "headers": {
        "Authorization": "Bearer replace-me"
      }
    }
  }
}
```

After saving changes, restart Cursor again.