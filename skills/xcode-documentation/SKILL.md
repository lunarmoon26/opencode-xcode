---
name: xcode-documentation
description: Apple Developer Documentation searches via Xcode. Use when a task asks for Swift, SwiftUI, UIKit, or Apple framework API documentation and an Xcode-backed documentation lookup is appropriate.
---

# Xcode Documentation

Use the native `xcode` tool with `tool: "DocumentationSearch"` and an
`arguments` object containing a focused `query`. Add a `frameworks` string array
when the framework is known; omit it for a broader Apple Developer Documentation
search.
