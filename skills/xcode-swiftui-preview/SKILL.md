---
name: xcode-swiftui-preview
description: SwiftUI previews and contextual Swift snippets in Xcode. Use when a task requests a SwiftUI preview render, preview debugging, or evaluating a small Swift snippet in an open Xcode target.
---

# Xcode SwiftUI Preview

Use the native `xcode` tool, backed by MCPorter. Obtain the workspace
`tabIdentifier` with `XcodeListWindows`, then inspect the Swift source with
`XcodeRead` or `XcodeGetCurrentFile`.

- Render a preview with `RenderPreview`, supplying `sourceFilePath` and
  `tabIdentifier`; optionally select a preview index or returned variants.
- Use `RunCodeSnippet` only for short observational Swift code. Its `purpose`
  must be a plain description and must not contain the word `test`.
- After edits, rebuild before rendering again when compilation state may be
  stale.
