# Threads, actions, and UI

Use `JBLabel`, `JBPanel`, `JBUI`, and the Kotlin UI DSL ([UI guidelines](https://plugins.jetbrains.com/docs/intellij/ui-guidelines-welcome.html)). Do not set a custom Look and Feel. The UI Designer does not work with Kotlin. Raw Swing follows the [javax.swing](../.cursor/skills/javax-swing/SKILL.md) skill, and AWT follows the [java.awt](../.cursor/skills/java-awt/SKILL.md) skill. Icons are in [registration.md](registration.md). Prefer `AllIcons` from the [icon list](https://intellij-icons.jetbrains.design/).

## EDT and background

Touch Swing only on the EDT. Long work is a cancellable `Task.Backgroundable` on `ProgressManager`:

- Return to the UI with `invokeLater(..., ModalityState.defaultModalityState())`.
- Before updating, check a request generation and `project.isDisposed`. Increment the generation when a new run starts so a cancelled run cannot paint.
- Rethrow `ProcessCanceledException`. Show other failures in the status line.
- From the background task set `indicator.fraction`, `indicator.text`, and call `indicator.checkCanceled()`.

Call Git through `GitLineHandler` with `setSilent(true)` and `withNoTty()`, then `Git.getInstance().runCommand`. Do not start it with `ProcessBuilder`.

Wrap a PSI read outside the EDT in a read action. PSI writes and document edits go in a write action. Do not query indexes during dumb mode. An action that does not need the index extends `DumbAwareAction`.

## Actions

```kotlin
override fun getActionUpdateThread(): ActionUpdateThread = ActionUpdateThread.EDT
```

`update` only changes `presentation`. `actionPerformed` starts with `event.project ?: return`.

## Settings

`SearchableConfigurable` implements `getId`, `getDisplayName`, `createComponent`, `isModified`, `apply`, and `reset`. Lay it out with `panel { row { } }` from `com.intellij.ui.dsl.builder`. After `apply`, refresh open views that show the new state.

Persist with `@Service` and `PersistentStateComponent` ([registration.md](registration.md)). Store XML-friendly values, not `Color` or `Set`. Fall back to the default when the stored value does not parse.

## Strings

Follow `MyMessageBundle`: `DynamicBundle` for `messages.MyMessageBundle`, `message` annotated `@PropertyKey` and `@Nls`, and `lazyMessage` where the platform wants `Supplier<@Nls String>`. Add a properties key instead of a Kotlin literal. Parameters are `{0}`, `{1}`.

## Controls

Put these in `panel { row { } }` from `com.intellij.ui.dsl.builder`. One control, one job.

- [Button](https://plugins.jetbrains.com/docs/intellij/button.html) — an immediate action. Use `button`.
- [Checkbox](https://plugins.jetbrains.com/docs/intellij/checkbox.html) — yes/no, or several items in a group. Use `checkBox` (`JBCheckBox`).
- [Combo box](https://plugins.jetbrains.com/docs/intellij/combo-box.html) — a value from a list, or a custom value. Use `comboBox`.
- [Context help](https://plugins.jetbrains.com/docs/intellij/context-help.html) — a short explanation when the control is not clear. Use `contextHelp`.
- [Description text](https://plugins.jetbrains.com/docs/intellij/description-text.html) — an explanation of a setting or a list item. Use `text` or `rowComment`.
- [Drop-down list](https://plugins.jetbrains.com/docs/intellij/drop-down.html) — a button that opens a list in a dialog. Use `dropDownLink` (`DropDownLink`).
- [Got It tooltip](https://plugins.jetbrains.com/docs/intellij/got-it-tooltip.html) — a first-time note about a new feature. Use `GotItTooltip`, not a custom popup.
- [Group header](https://plugins.jetbrains.com/docs/intellij/group-header.html) — a label for a group of controls. Use `group`.
- [Icon button](https://plugins.jetbrains.com/docs/intellij/icon-button.html) — an action on a toolbar. Use an `ActionToolbar` action, not a `JButton`.
- [Input field](https://plugins.jetbrains.com/docs/intellij/input-field.html) — one line of text. Use `textField` (`JBTextField`).
- [Link](https://plugins.jetbrains.com/docs/intellij/link.html) — navigation inside the same window. Use `link` (`ActionLink`). A URL uses `browserLink` (`BrowserLink`).
- [Notification balloon](https://plugins.jetbrains.com/docs/intellij/balloon.html) — status of an operation that just finished. Use a `Notification` balloon.
- [Banner](https://plugins.jetbrains.com/docs/intellij/banner.html) — a persistent message on that surface. Use the platform banner, not a custom colored strip.
- [Loader](https://plugins.jetbrains.com/docs/intellij/loader.html) — an indeterminate wait. Use `JBLoadingPanel`.
- [Progress bar](https://plugins.jetbrains.com/docs/intellij/progress-bar.html) — a known amount of work. Set `indicator.fraction` on the background task.
- [Progress text](https://plugins.jetbrains.com/docs/intellij/progress-text.html) — what that work is doing now. Set `indicator.text`.
- [Radio button](https://plugins.jetbrains.com/docs/intellij/radio-button.html) — one choice from two to four. Use `radioButton` (`JBRadioButton`) inside `buttonsGroup`.
- [Scrollbar](https://plugins.jetbrains.com/docs/intellij/scrollbar.html) — content larger than the view. Use `scrollCell` (`JBScrollPane`).
- [Search field](https://plugins.jetbrains.com/docs/intellij/search-field.html) — find an object, action, or text. Use `SearchTextField`.
- [Split button](https://plugins.jetbrains.com/docs/intellij/split-button.html) — a main action plus a menu of secondary actions. Use `JBOptionButton`.
- [Split icon button](https://plugins.jetbrains.com/docs/intellij/split-icon-button.html) — the same split on a toolbar, with an icon. Use `JBOptionButton`.
- [Table](https://plugins.jetbrains.com/docs/intellij/table.html) — review or edit uniform rows. Use `JBTable`.
- [Tabs](https://plugins.jetbrains.com/docs/intellij/tabs.html) — dialog tabs are `JBTabbedPane`. Tool-window tabs are `Content` ([ui-content](platform-api/ui-content.md)).
- [Text area](https://plugins.jetbrains.com/docs/intellij/text-area.html) — more than one line. Use `textArea` (`JBTextArea`).
- [Toggle button](https://plugins.jetbrains.com/docs/intellij/toggle-button.html) — on or off. Use `OnOffButton`.
- [Toolbar](https://plugins.jetbrains.com/docs/intellij/toolbar.html) — frequent actions and filters. Use `ActionToolbar`.
- [Toolbar drop-down](https://plugins.jetbrains.com/docs/intellij/toolbar-drop-down.html) — a toolbar button that opens a list. Use a toolbar action, not `comboBox`.
- [Tool window](https://plugins.jetbrains.com/docs/intellij/tool-windows.html) — a pane in the IDE frame. Register it as in [registration.md](registration.md). Do not build a frame.
