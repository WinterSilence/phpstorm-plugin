# Local inspections

```xml
<extensions defaultExtensionNs="com.intellij">
    <localInspection language="PHP"
        shortName="ExampleParams"
        displayName="Parameter type"
        groupPath="PHP"
        groupName="Type compatibility"
        enabledByDefault="true"
        level="WARNING"
        implementationClass="com.example.ExampleParamsInspection"/>
</extensions>
```

`shortName` is the id. The description is `src/main/resources/inspectionDescriptions/ExampleParams.html`. `<!-- tooltip end -->` ends the tooltip. `level` is a severity such as `WARNING` or `WEAK WARNING`. `groupPath` and `groupName` place it in the settings tree.

## Visitor

Extend `com.jetbrains.php.lang.inspections.PhpInspection`. `buildVisitor` returns a `PhpElementVisitor` and reports through `ProblemsHolder`. Copy option fields into locals before creating the visitor. The visitor must not read the inspection later:

```kotlin
class ExampleParamsInspection : PhpInspection() {
    @JvmField
    var treatVoidReturnAsNull: Boolean = false

    override fun buildVisitor(holder: ProblemsHolder, isOnTheFly: Boolean): PsiElementVisitor {
        val voidAsNull = treatVoidReturnAsNull
        return object : PhpElementVisitor() {
            override fun visitPhpElement(element: PhpPsiElement) {
                if (element is FunctionReference) checkCall(element, holder, voidAsNull)
            }
        }
    }
}
```

Use `FunctionReference`, `MethodReference`, `FieldReference`, `Parameter`, `PhpType`, and `PhpIndex`. Do not import `com.jetbrains.php.lang.psi.elements.impl`.

## Options

Options are public `@JvmField` properties. `createOptionsPanel` passes `this` to `MultipleCheckboxOptionsPanel` and binds each checkbox to the property name.

## Types

- A native type wins over a plain `@param`, `@return`, or `@var`. The plain tag applies only when there is no native type.
- `@phpstan-*` and `@psalm-*` override the plain tag. When both are present, the value must match each of them.
- `self` is the class that declares the method. `static` is the class of the call. `$this` is the receiver of an instance call, and the called class of a static call.
- Resolve a chain one call at a time. `static` and `$this` keep that call's class. `self` switches to the declaring class.
- `instanceof` and configured type-guard functions narrow a variable, property, or method return inside `if`, `elseif`, `while`, `do`/`while`, and a `match` arm. `||`, `else`, and `default` do not.
- A leading `!` on `instanceof` or on a type-guard call excludes those types. `(!value) instanceof Foo` tests a different value and does not exclude `Foo`.
