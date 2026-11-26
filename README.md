# Taskaid plugins

Plugins that connect AI assistants and coding tools to [Taskaid](https://taskaid.ai), published by Satria Technologies Private Limited.

Taskaid is task management between you and your agents. Work, context and next steps stay connected across conversations and assistants. In a coding tool, the agent can park something you noticed mid-change as a task with a day on it, pick a task up by its reference and carry on from its note, and mark it done when the fix is merged.

**Connection.** The plugin talks only to taskaid.ai: the MCP server at `https://taskaid.ai/mcp`, and Taskaid's OAuth sign-in under `https://taskaid.ai/.well-known/` and `https://taskaid.ai/oauth/`. You sign in with your Taskaid account in the browser; there's no API key, and the plugin stores no credentials. Each action runs as your own account, limited to what you approved.

## Cursor

1. Add Taskaid from the [Cursor Marketplace](https://cursor.com/marketplace).
2. In **Customize**, choose **Authenticate** on the Taskaid server and approve the access you want to grant.

If you added Taskaid to `mcp.json` before, Cursor treats that entry and the plugin as two sources for one server and runs only one of them. Choose the plugin as the source in **Customize**, or remove the entry.

[Taskaid for Cursor](https://taskaid.ai/integrations/cursor) has prompts to try and troubleshooting.

## Grok Build

1. Add Taskaid from the xAI Official marketplace: type `/marketplace` in Grok Build, or run `grok plugin install taskaid --trust`.
2. In a session, open `/mcps`, select **taskaid**, press `i` and approve the access you want to grant.

## Gemini CLI

1. Install the extension: `gemini extensions install https://github.com/satriahq/taskaid-plugins`.
2. In a session, run `/mcp auth taskaid` and approve the access you want to grant.

## Google Antigravity

1. Install the plugin: `agy plugin install https://github.com/satriahq/taskaid-plugins`.
2. In `agy`, open `/plugin`, expand **taskaid** under **Installed** and choose **Sign in**; the Antigravity app opens the sign-in itself when the server first connects. Approve the access you want to grant. In `agy`, paste the code Antigravity's page then shows.

The server is named **taskaid_taskaid**, as it is when `agy plugin import gemini` brings over the Gemini CLI extension. [Taskaid for Google Antigravity](https://taskaid.ai/integrations/antigravity) has prompts to try and troubleshooting.

## Hermes Agent

1. Install the plugin: `hermes plugins install taskaid --enable`.
2. Sign in with `hermes mcp add taskaid --url https://taskaid.ai/mcp --auth oauth --connect-timeout 300` and approve the access you want to grant.

[The plugin's README](hermes/README.md) adds Taskaid's skills, and [Taskaid for Hermes Agent](https://taskaid.ai/integrations/hermes) has prompts to try and troubleshooting.

## Kiro

[![Add to Kiro](https://kiro.dev/images/add-to-kiro.svg)](https://kiro.dev/launch/mcp/add?name=taskaid&config=%7B%22url%22%3A%22https%3A%2F%2Ftaskaid.ai%2Fmcp%22%7D)

1. Choose **Add to Kiro**, or add `"taskaid": { "url": "https://taskaid.ai/mcp" }` under `mcpServers` in Kiro's MCP configuration.
2. Under **MCP Servers** in Kiro's panel, choose **Authenticate** on **taskaid**, then **Open** to let Kiro open the sign-in in your browser. Approve the access you want to grant.

## Disconnect

Log out of the server in Cursor's **Customize**, run `grok plugin uninstall taskaid`, `gemini extensions uninstall taskaid` or `agy plugin uninstall taskaid`, run `hermes mcp remove taskaid` and `hermes plugins uninstall taskaid`, or remove `taskaid` from Kiro's MCP configuration. You can also disconnect an app under **Connected apps** in Taskaid's [Settings](https://taskaid.ai/settings); for Antigravity, do that too, since it keeps its sign-in after the plugin is gone.

The [MCP server reference](https://taskaid.ai/docs/mcp) describes the tools. Taskaid's [Privacy Policy](https://taskaid.ai/privacy) and [Terms of Service](https://taskaid.ai/terms) apply.

## Support

Write to [support@taskaid.ai](mailto:support@taskaid.ai) or use [taskaid.ai/support](https://taskaid.ai/support).

## License

[MIT](LICENSE)
