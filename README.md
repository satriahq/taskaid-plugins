# Taskaid plugins

Plugins that connect AI assistants and coding tools to [Taskaid](https://taskaid.ai), published by Satria Technologies Private Limited.

Taskaid is task management between you and your agents. Work, context and next steps stay connected across conversations and assistants. In a coding tool, the agent can park something you noticed mid-change as a task with a day on it, pick a task up by its reference and carry on from its note, and mark it done when the fix is merged.

**Connection.** The plugin talks only to taskaid.ai: the MCP server at `https://taskaid.ai/mcp`, and Taskaid's OAuth sign-in under `https://taskaid.ai/.well-known/` and `https://taskaid.ai/oauth/`. You sign in with your Taskaid account in the browser; there's no API key, and the plugin stores no credentials.

## Cursor

1. Add Taskaid from the [Cursor Marketplace](https://cursor.com/marketplace).
2. In **Customize**, choose **Authenticate** on the Taskaid server and approve the access you want to grant.

If you added Taskaid to `mcp.json` before, Cursor treats that entry and the plugin as two sources for one server and runs only one of them. Choose the plugin as the source in **Customize**, or remove the entry.

[Taskaid for Cursor](https://taskaid.ai/integrations/cursor) has prompts to try and troubleshooting.

## Grok Build

1. Add Taskaid from the xAI Official marketplace: type `/marketplace` in Grok Build, or run `grok plugin install taskaid --trust`.
2. In a session, open `/mcps`, select **taskaid**, press `i` and approve the access you want to grant.

## Disconnect

Log out of the server in Cursor's **Customize**, or run `grok plugin uninstall taskaid`. You can also disconnect an app under **Connected apps** in Taskaid's [Settings](https://taskaid.ai/settings).

The [MCP server reference](https://taskaid.ai/docs/mcp) describes the tools. Taskaid's [Privacy Policy](https://taskaid.ai/privacy) and [Terms of Service](https://taskaid.ai/terms) apply.

## License

[MIT](LICENSE)
