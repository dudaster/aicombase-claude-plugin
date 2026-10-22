# AICOMBase plugin for Claude

Let Claude work on your WordPress sites through [AICOMBase](https://aicombase.com): create and edit pages and posts, Elementor pages, WooCommerce products, translations, menus and media — or fix what AICOMBase's site checks found — with the permissions you choose, a session and Undo for every job, and your approval for risky actions (MCP Guard).

## What you need

- An AICOMBase account (one site is free) with at least one WordPress site connected through the free [AICOM plugin](https://aicombase.com/docs/aicom).
- You must be an Owner or Administrator of the AICOMBase workspace to approve Claude's access.

## Install

In Claude Code:

```
/plugin marketplace add dudaster/aicombase-claude-plugin
/plugin install aicombase@aicombase
```

Then run `/mcp`, choose **aicombase** and sign in. AICOMBase asks which sites, which permissions and which mode Claude may use. That access appears on the Keys page in AICOMBase, where you can change it or disconnect Claude at any time.

On claude.ai and in the Claude apps you can also add AICOMBase as a connector: Settings → Connectors → Add custom connector → `https://aicombase.com/api/mcp`.

## What's inside

- `.mcp.json` — the AICOMBase MCP server (`https://aicombase.com/api/mcp`, OAuth sign-in, no key to copy).
- `skills/aicombase` — how to work with AICOMBase: one session per job, drafts first, read back, close with a summary, and what to do when something is refused.

## Try it

- "On example.com, create a draft page called Contact with our address and phone, and send me the preview link."
- "What did the site checks find on example.com? Fix what you can safely."
- "On every site in the category Clients, set the page Terms to draft."

## Support and privacy

- Help: <https://aicombase.com/docs/ai/aicombase> · Issues: <https://github.com/dudaster/aicom/issues>
- Privacy: <https://aicombase.com/privacy> · Terms: <https://aicombase.com/terms>
