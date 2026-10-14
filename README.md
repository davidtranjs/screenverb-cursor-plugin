# ScreenVerb

Cursor plugin that connects agents to [ScreenVerb](https://screenverb.com) through ScreenVerb's hosted remote [Model Context Protocol](https://modelcontextprotocol.io/) server.

ScreenVerb is a screenshot app for Mac, iPhone and iPad. This plugin lets the agent find, read and organize the screenshots you save to your ScreenVerb cloud library, including the text inside them. Pull an error message, a design mock or an API response out of a screenshot without leaving the editor.

## Install

1. Open **Cursor Settings → Plugins**.
2. Search for **ScreenVerb**.
3. Click **Install**, then complete the ScreenVerb sign-in prompt.

Or run `/add-plugin screenverb` in chat.

## MCP

```json
{
  "mcpServers": {
    "screenverb": {
      "type": "http",
      "url": "https://mcp.screenverb.com/mcp"
    }
  }
}
```

Auth is OAuth 2.1 with PKCE against ScreenVerb. Cursor prompts for ScreenVerb sign-in when the plugin connects. There is no API key or client ID to configure.

## Before you connect

You need a ScreenVerb account with cloud library access.

## What agents can do

| Tool | What it does | Access |
| --- | --- | --- |
| `list_screenshots` | List the newest screenshots with names, dates, captions and tags | Read |
| `search_screenshots` | Search filenames, recognized text, captions, tags and labels | Read |
| `get_screenshot` | Open one screenshot to see the image, its OCR text and metadata | Read |
| `rename_screenshot` | Rename a screenshot | Update |
| `delete_screenshot` | Remove a screenshot from the library | Update, destructive |

The hosted server is the source of truth for tool names and schemas.

## Example prompts

- Find the screenshot of the stack trace I took this morning and fix the error it shows.
- Search my screenshots for the expired token error and tell me what it says.
- Open my latest screenshot of the settings mock and build that layout.
- Rename my latest screenshot to Q3 roadmap draft.

## Notes

- When you connect, you choose read access, update access or both. The agent only sees the tools for the access you grant.
- Tool calls run as the ScreenVerb user who authorizes the connection.
- `delete_screenshot` is annotated as destructive, and the server tells agents to ask you before calling it.
- ScreenVerb hosts the server itself; this plugin does not run a local process.
- Revoke access at any time from the MCP page in your ScreenVerb dashboard.

## Docs

- ScreenVerb MCP docs: https://screenverb.com/docs/mcp
- Server URL: https://mcp.screenverb.com/mcp
- Privacy: https://screenverb.com/privacy
- Terms: https://screenverb.com/terms
- Support: support@screenverb.com

## License

MIT
