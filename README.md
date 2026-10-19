# Taskaid plugins

Plugins that connect AI assistants and coding tools to [Taskaid](https://taskaid.ai), published by Satria Technologies Private Limited.

Taskaid is task management between you and your agents. Work, context and next steps stay connected across conversations and assistants.

## Cursor

Cursor's agent can read and update your tasks from inside the editor. Park something you noticed mid-change as a task with a day on it, pick a task up by its reference and carry on from its note, and mark it done when the fix is merged.

1. Add Taskaid from the [Cursor Marketplace](https://cursor.com/marketplace).
2. In **Customize**, choose **Authenticate** on the Taskaid server and approve the access you want to grant.

You need a Taskaid account; there's no API key. Each action runs as your own account, limited to what you approved.

If you added Taskaid to `mcp.json` before, Cursor treats that entry and the plugin as two sources for one server and runs only one of them. Choose the plugin as the source in **Customize**, or remove the entry.

To disconnect, log out of the server in **Customize**, or disconnect Cursor under **Connected apps** in Taskaid's [Settings](https://taskaid.ai/settings).

[Taskaid for Cursor](https://taskaid.ai/integrations/cursor) has prompts to try and troubleshooting, and the [MCP server reference](https://taskaid.ai/docs/mcp) describes the tools. Taskaid's [Privacy Policy](https://taskaid.ai/privacy) and [Terms of Service](https://taskaid.ai/terms) apply.

## License

[MIT](LICENSE)
