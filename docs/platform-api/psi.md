# com.intellij.psi

The PSI tree, files, and references. `PsiTreeUtil` is one of the 29 stable classes in `util`. Confirm a signature in the [IntelliJ Platform Explorer](https://jb.gg/ipe) before calling it.

## Entry points

- `PsiElement` — a node in the PSI tree.
- `PsiFile` — a file node.
- `PsiElementVisitor` — visits one node; override the methods for the types you handle.

## Tree

Recursive visitors, whitespace, errors, comments, and tokens.

- `CustomHighlighterTokenType`
- `PlainTextTokenTypes`
- `PsiChildLink`
- `PsiComment`
- `PsiErrorElement`
- `PsiRecursiveElementVisitor`
- `PsiRecursiveElementWalkingVisitor`
- `PsiRecursiveVisitor`
- `PsiWalkingState`
- `PsiWhiteSpace`
- `StringEscapesTokenTypes`
- `SyntaxTraverser`
- `SyntheticElement`
- `TokenType`

## Files

Files, directories, view providers, and the document bound to a file.

- `AbstractFileViewProvider`
- `DummyHolderViewProvider`
- `FileTypeFileViewProviders`
- `FileViewProvider`
- `FileViewProviderFactory`
- `LanguageFileViewProviders`
- `MultiplePsiFilesPerDocumentFileViewProvider`
- `PackagePrefixFileSystemItem`
- `PsiAnchor`
- `PsiBinaryFile`
- `PsiCodeFragment`
- `PsiCompiledElement`
- `PsiCompiledFile`
- `PsiDirectory`
- `PsiDirectoryContainer`
- `PsiDocumentListener`
- `PsiDocumentManager`
- `PsiFileFactory`
- `PsiFileSystemItem`
- `PsiFileWithOneLanguage`
- `PsiInvalidElementAccessException`
- `PsiLargeBinaryFile`
- `PsiLargeFile`
- `PsiLargeTextFile`
- `PsiManager`
- `PsiPlainText`
- `PsiPlainTextFile`
- `SingleRootFileViewProvider`

## Names and stubs

Named elements, literals, and elements backed by stubs.

- `CommonClassNames`
- `ExternallyAnnotated`
- `ExternallyDefinedPsiElement`
- `NavigatablePsiElement`
- `OriginInfoAwareElement`
- `PsiDocCommentBase`
- `PsiListLikeElement`
- `PsiLiteralValue`
- `PsiMirrorElement`
- `PsiNameIdentifierOwner`
- `PsiNamedElement`
- `PsiQualifiedNamedElement`
- `StubBasedPsiElement`
- `StubBuilder`

## References and resolve

References, their providers, and the resolve result.

- `ContributedReferenceHost`
- `DelegatePsiTarget`
- `EmptyResolveResult`
- `FileResolveScopeProvider`
- `HintedReferenceHost`
- `ManipulatableTarget`
- `MultiRangeReference`
- `PsiElementResolveResult`
- `PsiPolyVariantReference`
- `PsiPolyVariantReferenceBase`
- `PsiQualifiedReference`
- `PsiQualifiedReferenceElement`
- `PsiRefElementCreator`
- `PsiReference`
- `PsiReferenceBase`
- `PsiReferenceContributor`
- `PsiReferenceFactory`
- `PsiReferenceProvider`
- `PsiReferenceProviderBean`
- `PsiReferenceRegistrar`
- `PsiReferenceService`
- `PsiReferenceWrapper`
- `PsiTarget`
- `ReferenceProviderType`
- `ReferenceRange`
- `RenameableDelegatePsiTarget`
- `ResolveResult`
- `ResolveScopeEnlarger`
- `ResolveScopeProvider`
- `ResolveState`
- `ResolvingHint`

## Language injection

Hosts that accept an injected language, and language substitution.

- `InjectedLanguagePlaces`
- `LanguageInjector`
- `LanguageSubstitutor`
- `LanguageSubstitutors`
- `LiteralTextEscaper`
- `PsiLanguageInjectionHost`
- `PsiLanguageInjectionHostVisitor`

## Tree changes

Listeners notified when the PSI tree changes.

- `ExternalChangeActionUtil`
- `PsiTreeAnyChangeAbstractAdapter`
- `PsiTreeChangeAdapter`
- `PsiTreeChangeEvent`
- `PsiTreeChangeListener`

## Smart pointers

Pointers that survive a reparse of the same element.

- `PsiElementRef`
- `SmartPointerManager`
- `SmartPointersKt`
- `SmartPsiElementPointer`
- `SmartPsiFileRange`

## Manipulation

Changing an element's text and the text used to describe it.

- `AbstractElementManipulator`
- `ElementDescriptionLocation`
- `ElementDescriptionProvider`
- `ElementDescriptionUtil`
- `ElementManipulator`
- `ElementManipulators`

## File properties

Keys stored on a file view provider.

- `FileContextProvider`
- `FilePropertyIntKey`
- `FilePropertyStringKey`

## Weighers

Comparable weights used when several targets match.

- `ForceableComparable`
- `Weigher`
- `WeigherExtensionPoint`
- `WeighingComparable`
- `WeighingService`

## Other

- `DummyBlockType` — a marker for a dummy block in a code fragment.
- `IntentionFilterOwner` — an element that can hide intentions.
- `PsiCheckedRenameElement` — an element whose rename is checked before it is applied.
- `PsiLock` — the lock used around PSI reads and writes.
- `PsiParserFacade` — creates PSI for a language from text.

## Do not call

Implementation types. Call the interface beside each one.

- `FilePropertyKeyImpl`
- `ParsingDiagnosticsHandlerImplKt`

## Subpackages

Counts are stable classes in that subtree. Do not depend on `impl`. `PsiTreeUtil` is in `util`.

- `codeStyle` — 129
- `css` — 1
- `file` — 1
- `filters` — 14
- `formatter` — 22
- `impl` — 225
- `injection` — 2
- `jsp` — 7
- `meta` — 7
- `presentation` — 1
- `scope` — 4
- `search` — 88
- `statistics` — 5
- `stubs` — 53
- `targets` — 4
- `templateLanguages` — 19
- `text` — 1
- `tree` — 20
- `util` — 29
