# Hitsteps MCP Server

Public metadata and setup notes for the Hitsteps remote Model Context Protocol
server.

Hitsteps exposes a hosted MCP server for analytics and website operations:

```text
https://www.hitsteps.com/mcp/
```

This repository is intentionally small. It contains public registry metadata and
client setup examples. It does not contain the production Hitsteps PHP service,
private OAuth keys, reviewer accounts, customer data, or deployment credentials.

## Install

Use the Hitsteps setup guide:

```text
https://www.hitsteps.com/plugin/?type=mcp
```

### Cursor

[Add to Cursor](cursor://anysphere.cursor-deeplink/mcp/install?name=Hitsteps&config=eyJ1cmwiOiJodHRwczovL3d3dy5oaXRzdGVwcy5jb20vbWNwLyJ9)

Manual Cursor configuration:

```json
{
  "mcpServers": {
    "Hitsteps": {
      "url": "https://www.hitsteps.com/mcp/"
    }
  }
}
```

Cursor install links and manual configuration use the compact connection format
above. Do not paste `server.json` into Cursor's manual MCP editor.

### VS Code And GitHub Copilot

Add Hitsteps to your user MCP configuration or to a workspace `.vscode/mcp.json`
file:

```json
{
  "servers": {
    "Hitsteps": {
      "type": "http",
      "url": "https://www.hitsteps.com/mcp/"
    }
  }
}
```

### Gemini CLI And Gemini Code Assist

```json
{
  "mcpServers": {
    "Hitsteps": {
      "httpUrl": "https://www.hitsteps.com/mcp/"
    }
  }
}
```

## Registry Metadata

The root [`server.json`](server.json) file is the canonical public metadata for
MCP registries and galleries. It includes:

- registry name: `com.hitsteps/analytics-operations`
- display title: `Hitsteps Analytics and Operations`
- transport: Streamable HTTP
- remote endpoint: `https://www.hitsteps.com/mcp/`
- icon: `https://www.hitsteps.com/favicon.png`
- documentation: `https://www.hitsteps.com/plugin/?type=mcp`

The `com.hitsteps/analytics-operations` name is domain-authenticated. Keep this
identity unless Hitsteps intentionally publishes a second GitHub-namespaced
entry such as `io.github.Hitsteps/...`.

## Authentication

Hitsteps uses OAuth for MCP access. Users should approve access through the
Hitsteps sign-in and consent flow. Do not paste Hitsteps account passwords,
tracking API keys, OAuth client secrets, private keys, or reviewer credentials
into MCP client configuration or this repository.

## Validation

Validate metadata before publishing:

```sh
mcp-publisher validate
```

Publish from this repository only after domain authentication is available to
the publisher environment:

```sh
mcp-publisher publish
```

Private signing keys and domain-authentication material must stay outside this
repository.
