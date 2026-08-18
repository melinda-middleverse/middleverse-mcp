# MiddleVerse Business Directory — MCP Server

> Search, explore, and book local businesses from the MiddleVerse AI-native directory.

**Endpoint:** `https://middleverse.ai/mcp` (HTTP, no auth required)  
**Protocol:** Model Context Protocol 2024-11-05  
**Transport:** HTTP POST (JSON-RPC 2.0)  
**Discovery:** `GET https://middleverse.ai/mcp` returns server info + tool list

---

## Tools (6)

| Tool | Description |
|------|-------------|
| `search_businesses` | Search by category, location, or keywords |
| `get_business` | Full details for a business by slug or name |
| `get_directory_stats` | Directory totals, categories, coverage stats |
| `check_availability` | Check booking availability for a business |
| `book_business` | Create a real booking on behalf of a user |
| `find_by_category_location` | Natural-language category + location search |

---

## Quick install

### Claude Desktop

Add to `~/Library/Application Support/Claude/claude_desktop_config.json` (macOS):

```json
{
  "mcpServers": {
    "middleverse-directory": {
      "url": "https://middleverse.ai/mcp",
      "transport": "http"
    }
  }
}
```

### Cursor

Add to `~/.cursor/mcp.json`:

```json
{
  "mcpServers": {
    "middleverse-directory": {
      "url": "https://middleverse.ai/mcp"
    }
  }
}
```

### Windsurf

Add to `~/.codeium/windsurf/mcp_config.json`:

```json
{
  "mcpServers": {
    "middleverse-directory": {
      "serverUrl": "https://middleverse.ai/mcp"
    }
  }
}
```

---

## Example prompts

- *"Find me a plumber in Cle Elum, WA"*
- *"Book a haircut tomorrow at 2pm at Joe's Barber in Leavenworth"*
- *"What restaurants in Ellensburg take online bookings?"*
- *"Show me details for the business 'Roslyn Café'"*

---

## Verify the server

```bash
# Discovery
curl -s https://middleverse.ai/mcp | jq .

# List tools
curl -s -X POST https://middleverse.ai/mcp \
  -H 'Content-Type: application/json' \
  -d '{"jsonrpc":"2.0","id":1,"method":"tools/list"}' | jq .
```

---

**Homepage:** https://middleverse.ai  
**Docs:** https://middleverse.ai/api-docs  
**Support:** support@middleverse.ai
