# Drict MCP — label-law checks for 48 countries

**Drict** checks the text of a product label against the label law of the country where it is sold. It covers 48 countries and lists what the law asks for: found (with the line it was found on), not found, needed only in some cases, and what to check by eye. Each point names its law and links to the official text.

This repository holds the setup files for the **hosted** Drict MCP server. There is nothing to install or run:

```
https://drint.io/drict/mcp
```

- Transport: Streamable HTTP (MCP 2025-11-25, 2025-06-18, 2025-03-26, 2024-11-05)
- Sign-in: none. The service is free and allows 120 checks per hour per address.
- Registry name: `io.drint/drict` ([MCP Registry](https://registry.modelcontextprotocol.io/v0/servers?search=io.drint/drict))
- Website: [drint.io/drict](https://drint.io/drict) · MCP page: [drint.io/drict/mcp](https://drint.io/drict/mcp)

> Drict looks for the items each label law names, by key words. It is **not legal advice** and never says a label is "compliant". Read the official text before printing.

## Tools

| Tool | What it does |
|---|---|
| `list_markets` | The 48 countries, each with its code and the products its label law is checked for |
| `list_requirements` | What a country's label law asks a product's label to carry, before a label exists: mandatory items, items needed only in some cases, the language rule, what to check by eye, each with its law and official sources |
| `check_label` | A label's printed text against one country's label law. Returns the points to check, each with its law and the line it was found on |

All three tools are read-only and keep nothing.

### What it covers

- **Food and drinks, and other consumer goods**, in all 48 countries.
- **Cosmetics, food supplements, alcoholic drinks, pet food, batteries, electrical goods, household chemicals, toys and textiles**, wherever an official text could be opened and read. Examples: the EU, the US, South Korea, Japan, China, Türkiye, the Gulf, Mexico, Brazil, Kazakhstan and Israel. `list_markets` gives the full list.
- **Medical devices** for the US, the EU, the UK and South Korea.

The 48 markets: United States, United Kingdom, European Union, France, Spain, Cyprus, Canada, Mexico, Brazil, Peru, China, Taiwan, Hong Kong, Japan, South Korea, Vietnam, Cambodia, Laos, Thailand, Malaysia, Singapore, Indonesia, Philippines, Myanmar, Timor-Leste, India, Pakistan, Bangladesh, Nepal, Bhutan, Sri Lanka, Maldives, Afghanistan, Iran, Saudi Arabia and the UAE, Israel, Egypt, Türkiye, Georgia, Armenia, Azerbaijan, Kazakhstan, Kyrgyzstan, Uzbekistan, Tajikistan, Turkmenistan, Mongolia and Angola.

## Connect

### Claude (claude.ai, Claude Desktop)

Settings → Connectors → **Add custom connector** → URL `https://drint.io/drict/mcp`.

### Claude Code

```bash
claude mcp add --transport http drict https://drint.io/drict/mcp
```

Or install it as a plugin from this repository:

```
/plugin marketplace add drint-io/drict-mcp
/plugin install drict@drict
```

### ChatGPT

Settings → Apps & Connectors → Advanced → Developer mode → **Create** → MCP server URL `https://drint.io/drict/mcp`, no authentication.

### Cursor

Add to `~/.cursor/mcp.json`:

```json
{
  "mcpServers": {
    "drict": { "url": "https://drint.io/drict/mcp" }
  }
}
```

### VS Code (GitHub Copilot)

Command Palette → **MCP: Add Server** → HTTP → `https://drint.io/drict/mcp`. Or add to `.vscode/mcp.json`:

```json
{
  "servers": {
    "drict": { "type": "http", "url": "https://drint.io/drict/mcp" }
  }
}
```

### Gemini CLI

```bash
gemini extensions install https://github.com/drint-io/drict-mcp
```

### Codex CLI

Add to `~/.codex/config.toml`:

```toml
[mcp_servers.drict]
url = "https://drint.io/drict/mcp"
```

### Windsurf, Cline, Kiro, goose and other clients

Use any "remote / Streamable HTTP server" option with the URL `https://drint.io/drict/mcp`. No headers and no key are needed.

## Try it

- "What must a cosmetics label for South Korea carry?"
- "Check this label for the US:" (then paste every line of the label)
- "We are shipping this granola to Japan and the EU. What is missing on the label?"
- "List the countries Drict covers for toys."

Give the label's printed text, every line of it: name, ingredients, net quantity, dates, addresses and warnings. To read a label from a photo or a PDF, use [drint.io/drict](https://drint.io/drict). That needs Drict Pro.

## Links

- Drict: https://drint.io/drict
- Pricing: https://drint.io/drict/pricing
- Support: support@drint.io
- Drint (packaging mockups and dielines) has its own MCP server: [drint-io/drint-mcp](https://github.com/drint-io/drint-mcp)

## License

The files in this repository are MIT-licensed. The drint.io service follows the [Drint Terms](https://drint.io/terms).
