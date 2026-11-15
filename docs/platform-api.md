# Stable platform and PHP types

These names are public top-level classes in the current IDE. The class itself is not marked `@Deprecated`, `@ApiStatus.Internal`, `@ApiStatus.Experimental`, `@ApiStatus.ScheduledForRemoval`, or `@ApiStatus.Obsolete`. A newer IDE can add or remove names. Confirm a signature in the [IntelliJ Platform Explorer](https://jb.gg/ipe) before calling it.

A class whose name ends with `Impl` is an implementation type. Call the interface next to it. Do not depend on an `impl` subpackage. Counts on each package page include every stable class in that subtree.

Open the one package page for the types you are about to call:

- [com.intellij.openapi.project](platform-api/project.md) — the open project, dumb mode, and lifecycle
- [com.intellij.openapi.wm](platform-api/wm.md) — tool windows, status bar, focus, and the welcome screen
- [com.intellij.ui.components](platform-api/ui-components.md) — platform Swing wrappers
- [com.intellij.ui.content](platform-api/ui-content.md) — tabs inside a tool window
- [com.jetbrains.php](platform-api/php.md) — PHP index and class hierarchy
- [com.intellij.codeInspection](platform-api/code-inspection.md) — inspections, problems, and quick fixes
- [com.intellij.psi](platform-api/psi.md) — the PSI tree, files, and references
