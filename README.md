# Taskaid plugins

Official Taskaid plugins for AI assistants and coding tools, maintained by Satria Technologies Private Limited.

Connect your assistant to [Taskaid](https://taskaid.ai) to capture tasks, keep their context in notes, organize lists, and plan your day. The plugins connect to Taskaid's hosted MCP server at `https://taskaid.ai/mcp`. You need a Taskaid account; no API key or local server is required.

## Cursor

The first package in this repository is a Cursor plugin named `taskaid`. It provides the Taskaid MCP connection, with seven tools for tasks, lists, and daily plans. Tools are available within the permissions you approve during sign-in.

The plugin is being prepared for submission to the Cursor Marketplace. To connect today without installing this package, follow the [Taskaid for Cursor guide](https://taskaid.ai/integrations/cursor). To review this package before publication, use the local installation below.

### Install locally

1. Clone this repository and check out the branch or commit you want to test.
2. From the repository root, copy the plugin files into Cursor's local plugins folder:

   ```sh
   mkdir -p "$HOME/.cursor/plugins/local/taskaid"
   cp -R .cursor-plugin mcp.json assets README.md LICENSE \
     "$HOME/.cursor/plugins/local/taskaid/"
   ```

3. Restart Cursor or run **Developer: Reload Window**.
4. Open **Customize** and confirm the Taskaid plugin and its MCP server appear.
5. Sign in to Taskaid when prompted, review the requested permissions, and approve the connection.

Leave headers, client ID, and client secret empty. Cursor and Taskaid handle OAuth registration and sign-in.

Teams and Enterprise administrators may need to enable **Allow Local Plugin Imports**. Copy the files into the local folder rather than symlinking to a checkout outside it. See [Cursor's local plugin instructions](https://cursor.com/docs/plugins#test-plugins-locally).

If you already added Taskaid directly through `mcp.json`, disable that connection while testing so you can verify the plugin's connection. An installed marketplace plugin with the same name takes precedence over a local copy.

### Try it

- "Show my Taskaid tasks for today, grouped by list."
- "Create a task called Review the retry policy in my Inbox."
- "Read TASKAID-45 and summarize what remains."
- "Add what we decided about retries to TASKAID-45's note."
- "Read today's tasks and write a focused daily plan."

Use your own task references and list names. Taskaid's [tools reference](https://taskaid.ai/docs/tools) describes the current tools and their behavior.

### Verify before submission

- Confirm the plugin loads from the local folder and exposes Taskaid's MCP tools.
- Complete OAuth sign-in and confirm the connected Taskaid account is the one you intended.
- Read your tasks, lists, and daily plan, and open a task by reference.
- Create a temporary task named **Cursor plugin smoke test**, update its note, and mark it complete. Confirm the changes in Taskaid.
- Disable and re-enable the plugin, then confirm it reconnects successfully.

These checks require Cursor and an authorized Taskaid account. A valid manifest alone does not verify the sign-in flow.

### Manage access and troubleshoot

Disable or uninstall the plugin from Cursor's **Customize** panel. To revoke its access from Taskaid, open [Settings](https://taskaid.ai/settings) and disconnect Cursor under **Connected apps**.

- **The plugin does not appear:** confirm `.cursor-plugin/plugin.json` was copied, reload Cursor, and check whether local plugin imports are allowed.
- **No tools appear:** confirm `mcp.json` points to `https://taskaid.ai/mcp`, enable the server, and sign in when prompted.
- **Unauthorized or insufficient permissions:** reconnect and approve the permissions needed for the action.

See the [Cursor setup guide](https://taskaid.ai/integrations/cursor), [MCP reference](https://taskaid.ai/docs/mcp), [Privacy Policy](https://taskaid.ai/privacy), and [Terms of Service](https://taskaid.ai/terms). Report packaging problems through [GitHub Issues](https://github.com/satriahq/taskaid-plugins/issues).

## Package contents

| Path | Purpose |
| --- | --- |
| `.cursor-plugin/plugin.json` | Cursor manifest, publisher, version, logo, and MCP configuration path |
| `mcp.json` | Connection to the hosted Taskaid MCP server |
| `assets/taskaid.png` | Existing Taskaid icon |
| `LICENSE` | MIT license for this repository |

The repository name is client-neutral so packaging for other clients can be added later. This initial version contains one plugin at the repository root and does not need a multi-plugin marketplace manifest. See [Cursor's plugin reference](https://cursor.com/docs/reference/plugins) for the format and submission checklist.

## Publication

After the local checks above pass and the changes are merged, submit `https://github.com/satriahq/taskaid-plugins` at [Cursor's publish form](https://cursor.com/marketplace/publish). Cursor reviews the plugin before listing it and reviews subsequent updates. Opening or merging a GitHub PR does not submit the plugin to Cursor.

## License

[MIT](LICENSE).
