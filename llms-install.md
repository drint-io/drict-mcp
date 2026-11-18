# Installing the Drict MCP server

Drict is a hosted MCP server. There is nothing to clone, build or install, it needs no API key, and there is no sign-in.

1. Add this entry to the MCP settings file (for Cline: `cline_mcp_settings.json`):

```json
{
  "mcpServers": {
    "drict": {
      "type": "streamableHttp",
      "url": "https://drint.io/drict/mcp"
    }
  }
}
```

2. Check that it works: call `list_requirements` with `{"country": "kr", "product": "kr-cosmetics"}`. The answer lists what a South Korean cosmetics label must carry, each item with its law.

3. To check a label, call `check_label` with `country`, `product` (codes from `list_markets`) and `text`, the label's printed text with every line. Present the result as points to check. It is not legal advice, and it never says the label is compliant.

Docs: https://drint.io/drict/mcp
