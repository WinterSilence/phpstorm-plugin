# com.intellij.openapi.project

The open project, indexing (dumb mode), and project lifecycle. Public stable classes in this package. Confirm a signature in the [IntelliJ Platform Explorer](https://jb.gg/ipe) before calling it.

## Entry points

- `Project` — the open project; services and PSI reads take it.
- `ProjectManager` — opens, closes, and lists projects.
- `DumbService` — reports indexing and runs work when smart mode returns.
- `DumbAware` — marks a component that works during indexing.

## Dumb mode

Actions, tasks, and helpers that run during indexing or wait until smart mode.

- `DumbAwareAction`
- `DumbAwareRunnable`
- `DumbAwareToggleAction`
- `DumbKt`
- `DumbModeBlockedFunctionality`
- `DumbModeStatisticsCollector`
- `DumbModeTask`
- `DumbServiceKt`
- `DumbServiceStartupActivity`
- `DumbUnawareHider`
- `IndexNotReadyException`
- `InitialDumbTaskRequiredForSmartMode`
- `PossiblyDumbAware`

## Project lifecycle

Listeners and helpers for the default project, light edit, close, rename, reload, and project type.

- `DefaultProjectFactory`
- `LightEditActionFactory`
- `ModuleListener`
- `ProjectBundle`
- `ProjectCloseHandler`
- `ProjectCloseListener`
- `ProjectCoreUtil`
- `ProjectLocator`
- `ProjectLocatorKt`
- `ProjectManagerListener`
- `ProjectNameListener`
- `ProjectReloadState`
- `ProjectType`
- `ProjectTypeService`
- `ProjectUtil`
- `ProjectUtilCore`
- `VetoableProjectManagerListener`

## Content roots

The project's content roots and the rescan info produced when they change.

- `BaseProjectDirectories`
- `BaseProjectDirectoriesDiff`
- `BaseProjectDirectoriesListener`
- `RootsChangeRescanningInfo`

## Storage and writes

External project storage, queued background work, and guards around PSI events and write actions.

- `ExternalStorageConfiguration`
- `ExternalStorageConfigurationManager`
- `IncompleteDependenciesServiceKt`
- `MergeableQueueTask`
- `NoAccessDuringPsiEvents`
- `SingleTaskExecutor`
- `WriteActionAutoCloseable`

## Other

- `ReadmeShownUsageCollector` — records that the project README was shown.

## Do not call

Implementation type. Call the interface beside it.

- `ExternalStorageConfigurationManagerImpl`

## Subpackages

Counts are stable classes in that subtree. Do not depend on `impl`.

- `configuration` — 3
- `ex` — 3
- `impl` — 30
