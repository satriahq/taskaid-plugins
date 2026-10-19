# Contributing

Cursor and xAI review every update before users get it, so test each change in both first.

Each client reads its own manifest: `.cursor-plugin/plugin.json` for Cursor and `.grok-plugin/plugin.json` for Grok Build. Both point at the one `mcp.json`. Keep the fields they share identical, `version` included.

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

## Test in Grok Build

1. Run `grok plugin validate .` and check that it reports the MCP server.
2. Install from the repository root with `grok plugin install "$PWD" --trust`.
3. In a session, open a task by its reference, then create a task, add to its note and complete it. Check the changes in Taskaid. If the server asks for sign-in, open `/mcps`, select **taskaid** and press `i`.
4. Remove the local copy with `grok plugin uninstall taskaid`.

A `taskaid` server added with `grok mcp add` shares its name and sign-in with the plugin's, so Grok runs one of them. `grok mcp doctor` doesn't list servers from plugins installed through Grok; a session's debug log does (`grok --debug-file <file>`, then look for `source="plugin:taskaid"`).

## Publish

Merging here publishes nothing.

- **Cursor:** the first listing is the team's application at [cursor.com/marketplace/publish](https://cursor.com/marketplace/publish), made while signed in to cursor.com as the team that owns it. Later updates and new plugins need no new application: ask Cursor to re-index. Questions go to marketplace-publishing@cursor.com.
- **Grok Build:** the listing is an entry in xAI's [plugin marketplace](https://github.com/xai-org/plugin-marketplace) that points at this repository, pinned to a commit. When `version` changes, xAI's bot moves the pin.

Cursor's Publisher Terms bind every update: the plugin stays free to use, and the README keeps linking Taskaid's Privacy Policy and Terms of Service. The manifest formats are in Cursor's [plugin reference](https://cursor.com/docs/reference/plugins) and xAI's [marketplace README](https://github.com/xai-org/plugin-marketplace#readme).
