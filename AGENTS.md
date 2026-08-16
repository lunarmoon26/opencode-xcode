# OpenCode Xcode

## Structure

- `plugin/xcode-mcporter.ts` is the runtime entrypoint. It resolves the sibling
  `plugin/xcode.mcp.jsonc` with `import.meta.url`; always ship/copy those two
  files together.
- The bundled MCP definition intentionally launches `xcrun mcpbridge` under
  the server name `xcode`.
- The plugin exposes one native `xcode` tool, not one tool per MCP method. Pass
  the exact MCP method in `tool` and its payload in `arguments`; use
  `tool: "list"` to inspect the live method catalog.
- Each skill lives at `skills/<skill-name>/SKILL.md`; its frontmatter `name`
  must match the directory name.

## Setup and verification

- Use Bun: `bun install`. This repository has no package scripts or test suite.
- With Xcode running, smoke-test the bundled configuration:

  ```bash
  bun -e 'import plugin from "./plugin/xcode-mcporter.ts"; const hooks = await plugin({}); const result = await hooks.tool.xcode.execute({ tool: "XcodeListWindows", arguments: {} }, { metadata() {} }); console.log(result.title); await hooks.dispose?.()'
  ```
- Before handoff, validate the install path too: copy both `plugin/` files and
  the `skills/` directories into `$HOME/.config/opencode`, register the plugin
  in `opencode.jsonc`, restart OpenCode, then call the native `xcode` tool.

## Installation constraints

- OpenCode must register `./plugin/xcode-mcporter.ts` in its `plugin` config
  array. Copying files into the global plugin directory alone is not reliable.
- The Vercel Skills CLI installs only `SKILL.md` files, not this native plugin.
- Restart OpenCode after changing the plugin, bundled MCP config, or skills.
