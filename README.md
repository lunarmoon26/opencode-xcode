# OpenCode Xcode

Native OpenCode plugin and focused skills for the local Xcode MCP, using
[MCPorter](https://github.com/openclaw/mcporter).

## Generation environment

- Xcode 26.6 (build 17F113)
- `xcrun mcpbridge` Xcode MCP with 21 discovered tools

## Install

The native plugin and skills install separately. The Skills CLI manages only
the `SKILL.md` files; it does not install OpenCode plugins. The plugin carries
its Xcode MCP definition in `plugin/xcode.mcp.jsonc`; no `~/.mcporter` config
is needed.

### 1. Install the native plugin

```bash
# Shell variables for these commands only; OpenCode does not read these names.
repo_dir=/path/to/opencode-xcode
opencode_dir="$HOME/.config/opencode"

# Install the plugin's runtime dependencies into OpenCode's global config.
cd "$opencode_dir"
bun add @opencode-ai/plugin mcporter

# Copy the plugin and its bundled MCP definition together.
mkdir -p "$opencode_dir/plugin"
cp "$repo_dir/plugin/xcode-mcporter.ts" \
  "$repo_dir/plugin/xcode.mcp.jsonc" \
  "$opencode_dir/plugin/"
```

Register the plugin in `~/.config/opencode/opencode.jsonc`. Merge this entry
with any existing `plugin` array; do not replace other configuration:

```jsonc
{
  "plugin": ["./plugin/xcode-mcporter.ts"]
}
```

Remove the direct `mcp.xcode` entry from OpenCode's config to avoid duplicate
Xcode tools. The native plugin uses its bundled definition instead.

### 2. Install the skills

Copy the bundled skills into OpenCode's global skill directory:

```bash
mkdir -p "$opencode_dir/skills"
cp -R "$repo_dir/skills/." "$opencode_dir/skills/"
```

Or let the [Vercel Skills CLI](https://github.com/vercel-labs/skills) manage
the skills:

```bash
npx skills add lunarmoon26/opencode-xcode
# or: bunx skills add lunarmoon26/opencode-xcode
```

Restart OpenCode after changing configuration, plugins, or skills.

## License

Licensed under [MIT](LICENSE).
