# Taskaid for Hermes Agent

Connects [Hermes Agent](https://hermes-agent.nousresearch.com) to [Taskaid](https://taskaid.ai), published by Satria Technologies Private Limited.

Taskaid is task management between you and your agents. Work, context and next steps stay connected across conversations and assistants. Hermes can capture something as a task with a day on it, pick a task up by its reference and carry on from its note, and plan your day.

**Connection.** The plugin talks only to taskaid.ai: the MCP server at `https://taskaid.ai/mcp`, and Taskaid's OAuth sign-in under `https://taskaid.ai/.well-known/` and `https://taskaid.ai/oauth/`. You sign in with your Taskaid account in the browser; there's no API key. Hermes keeps the sign-in, and the plugin holds no credentials. Each action runs as your own account, limited to what you approved. Taskaid is a paid service with a free trial; see [Pricing](https://taskaid.ai/pricing).

## Set up

1. Install the plugin: `hermes plugins install taskaid --enable`.
2. Sign in. Hermes signs in to a server only from your own configuration, so this adds the same server there:

   ```sh
   hermes mcp add taskaid --url https://taskaid.ai/mcp --auth oauth --connect-timeout 300
   ```

   Approve the access you want to grant in the browser. Over SSH, paste the address your browser lands on back into the terminal.
3. Optionally, add Taskaid's skills, which tell Hermes when and how to use Taskaid:

   ```sh
   hermes skills install https://taskaid.ai/.well-known/agent-skills/taskaid/SKILL.md
   hermes skills install https://taskaid.ai/.well-known/agent-skills/getting-started/SKILL.md
   ```

   `hermes skills update` picks up changes to them.

[Taskaid for Hermes Agent](https://taskaid.ai/integrations/hermes) has prompts to try and troubleshooting.

## Disconnect

Run `hermes mcp remove taskaid`, which also deletes the saved sign-in, then `hermes plugins uninstall taskaid`. You can also disconnect **Hermes Agent** under **Connected apps** in Taskaid's [Settings](https://taskaid.ai/settings).

The [MCP server reference](https://taskaid.ai/docs/mcp) describes the tools. Taskaid's [Privacy Policy](https://taskaid.ai/privacy) and [Terms of Service](https://taskaid.ai/terms) apply.

## License

[MIT](../LICENSE)
