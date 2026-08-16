---
name: xcode-project-files
description: Xcode project navigation, Swift source reading, searching, and editing. Use when a task names an open Xcode project, project navigator paths, Swift files, or Xcode-backed file changes.
---

# Xcode Project Files

Use the native `xcode` tool, backed by MCPorter. First call
`XcodeListWindows` with `{}` and carry the returned `tabIdentifier` into every
workspace-specific call.

- Browse: `XcodeLS`, `XcodeGlob`, `XcodeRead`, `XcodeGrep`, or
  `XcodeGetCurrentFile`.
- Edit only after reading the target: use `XcodeUpdate` for an exact replacement
  or `XcodeWrite` to create/overwrite a file.
- Use `XcodeMakeDir` and `XcodeMV` for navigator-aware folder and move/copy
  changes. Use `XcodeRM` only when deletion was explicitly requested.

Invoke the native tool with `tool` set to the exact Xcode MCP name and
`arguments` set to that tool's object. Call `xcode` with `tool: "list"` when a
tool's exact name is uncertain.
