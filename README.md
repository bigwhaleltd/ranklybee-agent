# RanklyBee for AI agents

Let your AI agent work with your [RanklyBee](https://ranklybee.com) account:
Google Search Console and Bing data, content plans and articles, backlinks and
outreach, community leads, and AI visibility tracking.

This repository packages two ways for agents to use RanklyBee:

- **The hosted RanklyBee MCP server** at `https://api.ranklybee.com/mcp`, which
  signs in with OAuth and needs nothing installed.
- **The `backlink-submission` skill**: instructions for a guided, human-approved
  backlink submission workflow.

You need a RanklyBee account. See the
[MCP setup guide](https://ranklybee.com/docs/mcp) for client configuration.

## Connect

### Claude Code, Codex, Cursor and other MCP clients

Add the remote server `https://api.ranklybee.com/mcp` to your client. A
ready-made config is in [`.mcp.json`](.mcp.json):

```json
{
  "mcpServers": {
    "ranklybee": {
      "type": "http",
      "url": "https://api.ranklybee.com/mcp"
    }
  }
}
```

Your client opens a RanklyBee sign-in and consent page. You choose the
permissions the connection gets. Reading is on by default; anything that
changes data, sends email or publishes stays off until you turn it on. No API
token or Project ID is stored in this repository or needed in the chat.

## What you can ask

- "Show my Search Console clicks and impressions for the last 28 days."
- "Which of my pages get impressions but few clicks?"
- "How healthy is my site's SEO right now?"
- "Check whether my backlink submission profile is ready."

## The backlink-submission skill

[`skills/backlink-submission/SKILL.md`](skills/backlink-submission/SKILL.md)
teaches an agent to read your confirmed submission profile, check the target
source, avoid duplicate backlinks, and record the real outcome. It needs
`backlink-submissions:read` and `backlink-submissions:submit` permissions and a
browser tool for the third-party form.

Safeguards built into the workflow:

- You review and approve each submission before the final submit action.
- It never bypasses CAPTCHA, MFA, payment, email verification or a site's terms.
- Each project can start at most 15 submission attempts per calendar day.

## Links

- Website: <https://ranklybee.com>
- MCP setup guide: <https://ranklybee.com/docs/mcp>
- Help: <https://ranklybee.com/help>
- [Privacy Policy](https://ranklybee.com/privacy) · [Terms of Service](https://ranklybee.com/terms)

Built by [Big Whale Ltd](https://github.com/bigwhaleltd). Licensed under MIT.
