# Threads, actions, and UI

Use `JBLabel`, `JBPanel`, `JBUI`, and the Kotlin UI DSL ([UI guidelines](https://plugins.jetbrains.com/docs/intellij/ui-guidelines-welcome.html)). Do not set a custom Look and Feel. The UI Designer does not work with Kotlin.

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
