# Contributing

Cursor, xAI, Nous Research and Anthropic review every update before users get it, so test each change in every client first.

Each client reads its own manifest: `.cursor-plugin/plugin.json` for Cursor, `.grok-plugin/plugin.json` for Grok Build, `.antigravity-plugin/plugin.json` for Google Antigravity, `hermes/plugin.json` for Hermes Agent and `claude/.claude-plugin/plugin.json` for Claude. Cursor and Grok Build share the root `mcp.json`. Antigravity reads only `mcp_config.json`. Hermes reads `hermes/mcp.json`, because it accepts only the Agent Plugins format, with a `$schema` and a `type` on each server. Claude reads `claude/.mcp.json`. Keep the fields the manifests share identical, `version` included, and all four server files on the same URL. The one exception is the logo for Antigravity and Claude: Antigravity's Marketplace asks for transparent padding around the mark, so both use the transparent mark, `assets/taskaid-transparent.png`. Claude installs only the `claude/` folder, so it carries its own copy as `claude/assets/taskaid.png`.

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

## Test in Google Antigravity

1. Run `agy plugin validate .` and check that it passes with one warning: `mcp.json` is never loaded. That file is Cursor's and Grok Build's, so `--strict` fails here by design.
2. Install from the repository root with `agy plugin install .`, then check that `mcpServers` in `agy plugin list --json` lists `taskaid`.
3. In `agy`, open `/plugin`, expand **taskaid** under **Installed** and choose **Sign in**. Approve on Taskaid and paste the code Antigravity's page shows.
4. In a session, open a task by its reference, then create a task, add to its note and complete it. Check the changes in Taskaid.
5. Remove the local copy with `agy plugin uninstall taskaid`.

Antigravity names the server `taskaid_taskaid`, the same name an imported Gemini CLI extension gets, and keeps sign-ins by server URL, so the two share one sign-in.

## Test in Claude

1. Run `claude plugin validate --strict ./claude` and check that it passes. It also runs a subset of the directory's checks; the directory adds a security scan and a policy review.
2. Run `claude --plugin-dir ./claude plugin details taskaid` and check that it lists one MCP server, `taskaid`.
3. Start a session with `claude --plugin-dir ./claude`, open `/mcp`, sign in to the plugin's `taskaid` server and approve on Taskaid.
4. Open a task by its reference, then create a task, add to its note and complete it. Check the changes in Taskaid.

`--plugin-dir` loads the plugin for that session only, so there's nothing to remove afterwards. The plugin bundles no skills: Taskaid's server serves them over MCP itself.

## Test in Hermes Agent

1. Run `hermes plugins validate hermes --install-deps` and check that it passes. The catalog's CI runs the same check.
2. Copy the package into Hermes's plugins folder and enable it:

   ```sh
   cp -R hermes "$HOME/.hermes/plugins/taskaid"
   hermes plugins enable taskaid
   ```

3. Sign in with `hermes mcp add taskaid --url https://taskaid.ai/mcp --auth oauth --connect-timeout 300`, approve on Taskaid, and check that the tools are listed.
4. In a session, open a task by its reference, then create a task, add to its note and complete it. Check the changes in Taskaid.
5. Remove the local copy with `hermes mcp remove taskaid` and `hermes plugins uninstall taskaid`.

`hermes mcp list` and `hermes mcp login` see only servers in `config.yaml`, not the plugin's, which is why step 3 adds the server there. On macOS, servers named `Taskaid` and `taskaid` share one saved sign-in, because their token files differ only in case.

## Publish

Merging here publishes nothing.

- **Cursor:** the first listing is the team's application at [cursor.com/marketplace/publish](https://cursor.com/marketplace/publish), made while signed in to cursor.com as the team that owns it. Later updates and new plugins need no new application: ask Cursor to re-index. Questions go to marketplace-publishing@cursor.com.
- **Grok Build:** the listing is an entry in xAI's [plugin marketplace](https://github.com/xai-org/plugin-marketplace) that points at this repository, pinned to a commit. When `version` changes, xAI's bot opens a pull request to move the pin; users get the update once xAI reviews and merges it.
- **Google Antigravity:** the listing starts with Google's [plugin interest form](https://forms.gle/2EX5RFYPoJe1UgxR9), for a plugin that passes `agy plugin validate`. Google builds the Marketplace bundle itself, promoting `.antigravity-plugin/plugin.json` to the root.
- **Claude:** the listing is a plugin-bundle submission in Anthropic's [developer portal](https://claude.ai/directory/manage) for this repository with plugin path `claude`, made from the Satria organization on claude.ai, whose connected GitHub account must be able to push here. The directory follows `main`, scans each new commit, and publishes a version that passes according to the listing's publish setting. Taskaid's MCP connector is a separate listing from the same organization, and the two can be paired.
- **Hermes Agent:** the listing is `plugin-catalog/taskaid.yaml` in Nous Research's [hermes-agent](https://github.com/NousResearch/hermes-agent/tree/main/plugin-catalog) repository, pinned to a full commit of this repository with `subdir: hermes`. Moving the pin is a new pull request there, opened by an owner or major contributor of this repository, and Nous reviews the commits it adopts. Users get the update once it's merged and they run `hermes plugins update taskaid`. The Marketplace page shows `hermes/README.md` at the pinned commit.

Cursor's Publisher Terms bind every update: the plugin stays free to use, and the README keeps linking Taskaid's Privacy Policy and Terms of Service. The manifest formats are in Cursor's [plugin reference](https://cursor.com/docs/reference/plugins), xAI's [marketplace README](https://github.com/xai-org/plugin-marketplace#readme), Antigravity's [Build plugins](https://antigravity.google/docs/build-plugins) guide, Claude's [plugin manifest reference](https://code.claude.com/docs/en/plugins/manifest-reference) and [pre-submission checklist](https://claude.com/docs/plugins/pre-submission-checklist), and Hermes's [plugin guide](https://hermes-agent.nousresearch.com/docs/developer-guide/plugins), whose catalog rules are in [Submitting to the plugin catalog](https://hermes-agent.nousresearch.com/docs/developer-guide/plugins/catalog-submission).
