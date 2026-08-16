---
name: xcode-build-test
description: Xcode builds, compiler diagnostics, and XCTest execution. Use when a task asks to build an open Xcode project, inspect build errors, run an Xcode test plan, or run selected XCTest cases.
---

# Xcode Build and Tests

Use the native `xcode` tool, backed by MCPorter. Start with `XcodeListWindows`
to obtain the `tabIdentifier`.

1. Run `BuildProject`.
2. Inspect failures using `GetBuildLog` and `XcodeListNavigatorIssues`; use
   `XcodeRefreshCodeIssuesInFile` for a specific source file.
3. Use `GetTestList` before `RunSomeTests`; pass each returned target name and
   XCTest identifier unchanged. Use `RunAllTests` only when the full plan is
   requested.

All workspace-specific calls require the same `tabIdentifier` in `arguments`.
