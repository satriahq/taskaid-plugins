# Contributing

Cursor reviews the plugin before listing it and reviews each update before publishing it, so test a change in Cursor before submitting it.

## Test locally

1. From the repository root, copy the plugin into Cursor's local plugins folder:

   ```sh
   mkdir -p "$HOME/.cursor/plugins/local/taskaid"
   cp -R .cursor-plugin mcp.json assets README.md LICENSE \
     "$HOME/.cursor/plugins/local/taskaid/"
   ```

2. Run **Developer: Reload Window**, open **Customize** and check that Taskaid and its MCP server appear.
3. Sign in to Taskaid when prompted and approve the connection.

Copy rather than symlink: Cursor skips a symlink to a folder outside its local plugins folder. On Teams and Enterprise, an admin may need to turn on **Allow Local Plugin Imports**. Disable any Marketplace copy of the plugin, which takes precedence over the local one, and any Taskaid entry in `mcp.json`, so the test exercises the plugin's own connection.

## Before submitting

- Taskaid's tools appear, and sign-in connects the account you intended.
- The agent can read your tasks and open one by its reference.
- It can create a task, add to its note and complete it, and the changes show in Taskaid.
- After turning the plugin off and on again, it reconnects.

## Submit

Merging here publishes nothing. The first submission is an application at [cursor.com/marketplace/publish](https://cursor.com/marketplace/publish), made while signed in to cursor.com as the team that owns the listing. Updates and new plugins need no new application: ask Cursor to re-index instead. Questions go to marketplace-publishing@cursor.com.

The manifest format and Cursor's submission checklist are in the [plugin reference](https://cursor.com/docs/reference/plugins).
