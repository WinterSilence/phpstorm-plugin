# com.intellij.ui.components

Platform Swing wrappers. Prefer these over the Swing classes they wrap. See [runtime.md](../runtime.md). Confirm a signature in the [IntelliJ Platform Explorer](https://jb.gg/ipe) before calling it.

## Entry points

- `JBLabel` — a label that follows the platform font.
- `JBPanel` — a panel that follows platform borders and spacing.
- `JBTextField` — a text field that follows the platform font.

## JB wrappers

These wrap the Swing component of the same name and follow the platform font and borders.

- `JBBox`
- `JBCheckBox`
- `JBCheckBoxMenuItem`
- `JBComboBoxLabel`
- `JBHtmlPane`
- `JBHtmlPaneConfiguration`
- `JBHtmlPaneStyleConfiguration`
- `JBLabelDecorator`
- `JBLayeredPane`
- `JBList`
- `JBLoadingPanel`
- `JBLoadingPanelListener`
- `JBMenu`
- `JBOptionButton`
- `JBOptionButtonKt`
- `JBPanelWithEmptyText`
- `JBPasswordField`
- `JBRadioButton`
- `JBScrollBar`
- `JBScrollPane`
- `JBSlider`
- `JBSlidingPanel`
- `JBTabbedPane`
- `JBTextArea`
- `JBThinOverlappingScrollBar`
- `JBViewport`

- `JBFontScaler` — scales fonts to the platform size.

## Links

Clickable labels and actions that open a URL.

- `ActionLink`
- `AnActionLink`
- `BrowserLink`
- `CopyLinkAction`
- `DropDownLink`
- `OpenLinkInBrowser`

## Badges and buttons

Badges, option buttons, and small toggle controls.

- `Badge`
- `BadgeKt`
- `BasicOptionButtonUI`
- `DefaultLinkButtonUI`
- `DefaultLinkButtonUIKt`
- `DisclosureButtonKt`
- `IconLabelButton`
- `OnOffButton`
- `OptionButtonUI`
- `PillButtonKt`

## Lists

List models and a selection model for bulk updates.

- `BulkDefaultListSelectionModel`
- `BulkListModelKt`
- `FixedColumnsModel`
- `MultiColumnList`
- `MultiColumnListModel`
- `WideSelectionListUI`

## Search field

A search field with an extension and its borders.

- `DarculaSearchBorder`
- `DarculaSearchFieldWithExtensionBorder`
- `DarculaSearchFieldWithExtensionUI`
- `SearchFieldWithExtension`
- `SearchFieldWithExtensionKt`

## Scroll bars

Platform scroll-bar UI and its show-hide animation.

- `DefaultScrollBarAnimationBehavior`
- `DefaultScrollBarUIKt`
- `DefaultScrollbarUiInstalledState`
- `MacScrollBarAnimationBehavior`
- `MacScrollBarUI`
- `MacScrollBarUIKt`
- `MacScrollbarStyle`
- `ScrollSettings`
- `TabMacScrollBarUI`
- `TabScrollBarUI`
- `ThinMacScrollBarUI`
- `ThinMacScrollBarUIKt`
- `ThinScrollBarUI`
- `ThinScrollBarUIKt`
- `ToggleableScrollBarAnimationBehaviorDecorator`

## Viewport

Zoom and gradient behavior for a viewport.

- `GradientViewport`
- `Interpolable`
- `Interpolator`
- `Magnificator`
- `ZoomableViewport`
- `ZoomingDelegate`

## Other

- `ComponentsKt` — Kotlin helpers for these components.
- `DialogManager` — shows platform dialogs.
- `LegalNoticeDialog` — a dialog for a legal notice.
- `ProgressBarLoadingDecorator` — paints a progress bar over a component while it loads.
- `ShimmerLabelKt` — a label with a loading shimmer.
- `TextComponentEmptyText` — placeholder text for an empty text component.
- `TwoSideComponent` — a component with a leading and a trailing side.

## Subpackages

Counts are stable classes in that subtree. Do not depend on `impl`.

- `breadcrumbs` — 2
- `editors` — 1
- `fields` — 10
- `impl` — 5
- `labels` — 3
- `panels` — 14
