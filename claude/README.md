# Taskaid for Claude

Connects Claude to [Taskaid](https://taskaid.ai), published by Satria Technologies Private Limited.

Taskaid is task management between you and your agents. Work, context and next steps stay connected across conversations and assistants. Claude can read your real tasks and daily plan, capture something as a task with a day on it, pick a task up by its reference and carry on from its note, and mark it done.

**Connection.** The plugin adds one MCP server, `https://taskaid.ai/mcp`, and nothing else: no bundled skills, hooks, scripts or local programs. Taskaid's server provides its own skills wherever Claude supports skills over MCP. It talks only to taskaid.ai: that server, and Taskaid's OAuth sign-in under `https://taskaid.ai/.well-known/` and `https://taskaid.ai/oauth/`. You sign in with your Taskaid account in the browser; there's no API key, and the plugin holds no credentials. Each action runs as your own account, limited to what you approved, and Taskaid doesn't use your data to train AI models. Taskaid has no delete tool, so Claude can't delete anything. Taskaid is a paid service with a free trial; see [Pricing](https://taskaid.ai/pricing).

## Set up

1. Add Taskaid from Claude's directory.
2. On claude.ai and in Cowork, open the plugin's **Connectors** tab and add or connect **taskaid**, then sign in to Taskaid and approve the access you want to grant. On Team and Enterprise plans, an Owner adds the connector for the organization first, and each member then connects their own account.
3. Claude Code picks the plugin up from the same account. If Taskaid is connected on claude.ai, Claude Code already has it as **claude.ai Taskaid**, so leave the plugin's own server, `plugin:taskaid:taskaid`, signed out: signing in to both shows Taskaid's tools twice. Without a claude.ai connection, open `/mcp` and sign in to the plugin's server.

On claude.ai and in Cowork, the plugin uses the same server as Taskaid's connector, so if you've already added Taskaid there, you see one set of tools.

## Try it

- "What's on my plate today? Include my daily plan."
- "Add a task to review the Q3 brief tomorrow morning and star it."
- "Read my tasks for this week, then write me a focused plan for today."

[Taskaid for Claude](https://taskaid.ai/integrations/claude) and [Taskaid for Claude Code](https://taskaid.ai/integrations/claude-code) have more prompts and troubleshooting.

## Disconnect

Remove Taskaid in Claude. Then, under **Connected apps** in Taskaid's [Settings](https://taskaid.ai/settings), disconnect **Claude**, and **Claude Code** too if you signed in there: Taskaid revokes each app's access separately.

The [MCP server reference](https://taskaid.ai/docs/mcp) describes the tools. Taskaid's [Privacy Policy](https://taskaid.ai/privacy) and [Terms of Service](https://taskaid.ai/terms) apply.

## License

MIT
