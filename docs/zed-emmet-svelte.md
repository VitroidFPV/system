# Use Emmet wrapping in Svelte

The [Emmet thread](t3-thread://v1/c07dee0f-c3f0-4f56-8b24-293037626722) confirmed that wrapping works after adding Emmet to Zed's Svelte language servers and reloading extensions. The installed extension manifest was edited during diagnosis, but its current copy no longer lists Svelte. The persistent setting and shortcut are below.

1. Install Zed's Emmet extension.
2. Add this entry inside `languages` in `~/.config/zed/settings.json`:

   ```jsonc
   "Svelte": {
     "language_servers": ["emmet-language-server", "..."]
   }
   ```

3. In `~/.config/zed/keymap.json`, unbind the dock shortcut and bind wrapping:

   ```jsonc
   { "context": "Workspace", "unbind": { "ctrl-alt-w": "workspace::CloseActiveDock" } },
   { "context": "Editor && mode == full", "bindings": { "ctrl-alt-w": "editor::WrapWithAbbreviation" } }
   ```

4. Run `zed: reload extensions`. In a `.svelte` file, select markup, run `editor: wrap with abbreviation`, and then test `Ctrl+Alt+W`.

Add these objects to the existing JSONC arrays; do not replace the rest of either file. If the command is absent, inspect the file's language server list in Zed.
