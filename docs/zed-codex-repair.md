# Repair Zed's bundled Codex

In the [Codex startup thread](t3-thread://v1/4a5f6334-2d0f-4dee-a5d2-6173994c738d), Zed's `codex-acp` package contained metadata for `@openai/codex-linux-x64` but lacked its executable. The matching Codex 0.159.3 executable was restored from the official package. The command that had failed then reported `codex-cli 0.159.3`. A Zed AI thread was not tested afterward.

1. Reproduce the missing optional dependency error. Find Zed's `codex-acp` directory under `~/.local/share/zed/external_agents/registry/npx/`.
2. Read the required `@openai/codex` version from that installation's `package.json`. Do not assume that 0.159.3 is still the correct version.
3. Reinstall the matching official `@openai/codex-linux-x64` package in Zed's existing `node_modules`. Check that its `vendor/x86_64-unknown-linux-musl/bin/codex` file exists and is executable.
4. Run that executable with `--version`, then retry a Zed AI thread.

An update to Zed's external agent package can replace this repaired directory. If the error returns, prefer a clean reinstall through Zed's agent management before manually restoring a binary.
