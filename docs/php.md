# PHP PSI

`com.jetbrains.php` is already a `<depends>` and a `bundledPlugin`. Call only the public PHP API. Register PHP points on `com.jetbrains.php`. Platform points stay on `com.intellij`. Local inspections: [inspections.md](inspections.md).

## Property type

```xml
<extensions defaultExtensionNs="com.jetbrains.php">
    <typeProvider4 implementation="com.example.ExampleTypeProvider"/>
</extensions>
```

`PhpTypeProvider4`:

- `getKey()` is a character no other provider uses.
- `getType` catches `RuntimeException` and returns `null`. It runs during indexing.
- `complete` and `getBySignature` return `null` when unused. Do not touch the index from them.
- Return `null` when `getTypeDeclaration()` is set or the field has a `@var` tag.
- During indexing, use only the current file: `PsiTreeUtil` and attributes in that file. Do not resolve across the project or read the stub index.
- Compare FQNs with a leading `\`. Expand a `PhpUse` in the same file.

A live IDE needs Invalidate Caches after a provider change. The `runIde` sandbox needs a restart.

## Suppression

```xml
<extensions defaultExtensionNs="com.intellij">
    <lang.inspectionSuppressor language="PHP"
        implementationClass="com.example.ExampleSuppressor"/>
</extensions>
```

`isSuppressedFor` matches the exact `toolId` and returns `false` for every other id. Walk supers with `PhpClassHierarchyUtils.processSupers`. On any exception, return `false`. Without a custom fix, `getSuppressActions` returns `SuppressQuickFix.EMPTY_ARRAY`.

## Structure view

```xml
<lang.psiStructureViewFactory language="PHP"
    implementationClass="com.example.ExampleStructureViewFactory"
    order="first"/>
```

Take the delegate from `LanguageStructureViewBuilder.getInstance().allForLanguage(...)` and drop this class from that list. Wrap only a `TreeBasedStructureViewBuilder`. Return any other builder unchanged. Set the renderer on the tree of the `StructureViewComponent` already created.

A tree filter implements `Filter`. Detect PHPDoc members from PSI (`PhpDocProperty`, `PhpDocMethod`, tags), not from the node text.
