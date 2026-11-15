# com.intellij.codeInspection

Local and global inspections, problem descriptors, and quick fixes. A PHP inspection extends `PhpInspection`, not `LocalInspectionTool`. See [inspections.md](../inspections.md). Confirm a signature in the [IntelliJ Platform Explorer](https://jb.gg/ipe) before calling it.

## Entry points

- `ProblemsHolder` — collects problems the visitor reports.
- `InspectionSuppressor` — decides whether a tool is suppressed at an element.
- `SuppressQuickFix` — a quick fix that suppresses a tool.
- `LocalInspectionTool` — a local inspection. A PHP inspection does not extend this class.

## Local and global tools

Visitors and the session they run in. Global tools cover the whole project.

- `CleanupLocalInspectionTool`
- `ExternalAnnotatorInspectionVisitor`
- `GlobalInspectionContext`
- `GlobalInspectionTool`
- `GlobalInspectionUtil`
- `GlobalSimpleInspectionTool`
- `LocalInspectionEP`
- `LocalInspectionToolSession`
- `LocalInspectionToolSessionKtKt`
- `ProblematicWhitespaceInspection`

## Problems

Descriptors for one problem and how it is highlighted.

- `CommonProblemDescriptor`
- `ModuleProblemDescriptor`
- `ProblemDescriptionsProcessor`
- `ProblemDescriptor`
- `ProblemDescriptorBase`
- `ProblemDescriptorUtil`
- `ProblemHighlightType`

## Quick fixes

Fixes attached to a problem, including fixes that are also intentions.

- `AddToInspectionOptionListFix`
- `BatchQuickFix`
- `CommonQuickFixBundle`
- `HintAction`
- `IntentionAndQuickFixAction`
- `IntentionWrapper`
- `LocalQuickFix`
- `LocalQuickFixAndIntentionActionOnPsiElement`
- `LocalQuickFixBackedByIntentionAction`
- `LocalQuickFixOnPsiElement`
- `LocalQuickFixProvider`
- `QuickFix`
- `RefactoringQuickFix`
- `UpdateInspectionOptionFix`

## Suppression

Suppressors, suppression fixes, and detection of a suppression that no longer matches.

- `BatchSuppressableTool`
- `ContainerBasedSuppressQuickFix`
- `CustomSuppressableInspectionTool`
- `InjectionAwareSuppressQuickFix`
- `LanguageInspectionSuppressors`
- `RedundantSuppressionDetector`
- `SuppressableProblemGroup`
- `SuppressIntentionAction`
- `SuppressIntentionActionFromFix`
- `SuppressionUtil`

## Profiles and registration

The inspection profile, tool registration, and the manager that runs tools.

- `InspectionEngine`
- `InspectionEP`
- `InspectionManager`
- `InspectionManagerBase`
- `InspectionProfile`
- `InspectionProfileEntry`
- `InspectionProfileLoader`
- `InspectionProfileLoaderBase`
- `InspectionToolProvider`

## Batch run and export

Command-line inspection, HTML and XML export, and the application that runs a batch.

- `AbstractInspectionCmdlineOptions`
- `AbstractInspectionToolStarter`
- `ActionClassHolder`
- `AggregateResultsInspection`
- `DefaultInspectionToolResultExporter`
- `DeprecationUtil`
- `ExportedInspectionsResultModifier`
- `HTMLComposer`
- `InspectionApplicationBase`
- `InspectionApplicationException`
- `InspectionMain`
- `InspectionsBundle`
- `InspectionsReportConverter`
- `InspectionsResultUtil`
- `InspectionToolCmdlineOptionHelpProvider`
- `InspectionToolCmdlineOptions`
- `InspectionToolResultExporter`

## Do not call

Implementation type. Call `CommonProblemDescriptor`.

- `CommonProblemDescriptorImpl`

## Subpackages

Counts are stable classes in that subtree. Do not depend on `impl`.

- `actions` — 9
- `dataFlow` — 58
- `ex` — 51
- `export` — 1
- `incorrectFormatting` — 3
- `inspectionProfile` — 17
- `lang` — 4
- `longLine` — 1
- `naming` — 3
- `offline` — 1
- `offlineViewer` — 1
- `options` — 27
- `reference` — 19
- `ui` — 29
- `util` — 4
- `visibility` — 1
