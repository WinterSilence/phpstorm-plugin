# com.intellij.openapi.wm

Tool windows, the status bar, focus, and the welcome screen. Public stable classes in this package. Confirm a signature in the [IntelliJ Platform Explorer](https://jb.gg/ipe) before calling it.

## Entry points

- `ToolWindow` — one tool window in the IDE frame.
- `ToolWindowFactory` — creates one tool window.
- `ToolWindowManager` — registers and finds tool windows.

## Tool windows

Registration, anchors, content style, and the stored window layout.

- `RegisterToolWindowTask`
- `RegisterToolWindowTaskBuilder`
- `ToolWindowAllowlistEP`
- `ToolWindowAnchor`
- `ToolWindowBalloonShowOptions`
- `ToolWindowContentUiType`
- `ToolWindowContextMenuActionBase`
- `ToolWindowEP`
- `ToolWindowId`
- `ToolWindowType`
- `WindowInfo`
- `WindowInfoKt`

## Status bar

The status bar and the widgets it hosts.

- `CustomStatusBarWidget`
- `IconLikeCustomStatusBarWidget`
- `StatusBar`
- `StatusBarInfo`
- `StatusBarListener`
- `StatusBarWidget`
- `StatusBarWidgetFactory`

## Focus and frame

Focus requests, the IDE frame, and its glass pane.

- `BaseFocusWatcher`
- `FocusRequestor`
- `FocusWatcher`
- `IdeFocusManager`
- `IdeFocusUtilKt`
- `IdeFrame`
- `IdeGlassPane`
- `IdeGlassPaneUtil`
- `IdeRootPaneNorthExtension`
- `PassThroughIdeFocusManager`
- `WeakFocusStackManager`
- `WindowManager`

## Welcome screen

The welcome frame, light edit, and start-page promotion.

- `AppIconScheme`
- `BannerStartPagePromoter`
- `InteractiveCourseData`
- `InteractiveCourseFactory`
- `LightEditFrame`
- `WelcomeFrameProvider`
- `WelcomeScreen`
- `WelcomeScreenProvider`
- `WelcomeScreenTab`
- `WelcomeTabFactory`

## Subpackages

Counts are stable classes in that subtree. Do not depend on `impl`.

- `ex` — 14
- `ext` — 2
- `impl` — 303
