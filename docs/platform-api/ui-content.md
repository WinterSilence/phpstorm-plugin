# com.intellij.ui.content

Tabs inside a tool window. Public stable classes in this package. Confirm a signature in the [IntelliJ Platform Explorer](https://jb.gg/ipe) before calling it.

## Entry points

- `Content` — one tab.
- `ContentFactory` — creates tab content.

## Tabs

The tab, its manager, and events when tabs change.

- `ContentManager`
- `ContentManagerEvent`
- `ContentManagerListener`
- `ContentManagerUtil`
- `ContentUI`
- `TabbedContent`
- `TabDescriptor`
- `TabGroupId`

## Message view

- `AlertIcon` — the icon shown for an alert in the message view.
- `MessageView` — the tool window that lists messages.

## Do not call

Implementation type. Call `ContentFactory`.

- `ContentFactoryImpl`

## Subpackages

Counts are stable classes in that subtree. Do not depend on `impl`.

- `impl` — 4
- `tabs` — 1
