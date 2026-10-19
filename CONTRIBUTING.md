# Contributing

Cursor reviews every update before publishing it, so test each change in Cursor first.

## Test in Cursor

1. From the repository root, copy the plugin into Cursor's local plugins folder. Copy rather than symlink: Cursor skips a symlink to a folder outside it.

   ```sh
   mkdir -p "$HOME/.cursor/plugins/local/taskaid"
   cp -R .cursor-plugin mcp.json assets README.md LICENSE \
     "$HOME/.cursor/plugins/local/taskaid/"
   ```

2. Run **Developer: Reload Window**. Taskaid appears in **Customize** as a **Local** plugin.
3. Open its MCP server. If Taskaid is also in `mcp.json`, choose **Plugin** as the source. Uninstall any Marketplace copy, which takes precedence over a local one.
4. Choose **Authenticate**, approve on Taskaid, and check that the tools are listed.
5. In Agent chat, open a task by its reference, then create a task, add to its note and complete it. Check the changes in Taskaid.
6. Turn the server off and on again and check that it reconnects.

On Teams and Enterprise, an admin may need to turn on **Allow Local Plugin Imports**.

## Publish

Merging here publishes nothing. The first listing is the team's application at [cursor.com/marketplace/publish](https://cursor.com/marketplace/publish), made while signed in to cursor.com as the team that owns it. Later updates and new plugins need no new application: ask Cursor to re-index. Questions go to marketplace-publishing@cursor.com.

Cursor's Publisher Terms bind every update: the plugin stays free to use, and the README keeps linking Taskaid's Privacy Policy and Terms of Service. The manifest format and the submission checklist are in Cursor's [plugin reference](https://cursor.com/docs/reference/plugins).
