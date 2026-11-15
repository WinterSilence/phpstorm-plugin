# Registration in plugin.xml

File: `src/main/resources/META-INF/plugin.xml`. Schema: [Plugin Configuration File](https://plugins.jetbrains.com/docs/intellij/plugin-configuration-file.html). `<name>` is Title Case. `<description>` is HTML in CDATA. See [listing guidelines](https://plugins.jetbrains.com/docs/marketplace/best-practices-for-listing.html). Identifiers are still placeholders; change them with `./customize` ([build.md](build.md)). `<id>` does not change between versions.

## Dependencies

A plugin with no platform module dependency is legacy and loads only in IntelliJ IDEA ([compatibility](https://plugins.jetbrains.com/docs/intellij/plugin-compatibility.html)). `com.intellij.modules.platform` and `com.jetbrains.php` are already declared. `com.jetbrains.php` is also `bundledPlugin` in Gradle.

Any further module is declared twice: `<depends>` or `<dependencies><module name="..."/>`, and `bundledPlugin` or `bundledModule`. Do not depend on a `*.impl` module. Do not add `<content><module>` (Plugin Model V2).

## Strings and logo

`<resource-bundle>messages.MyMessageBundle</resource-bundle>` supplies XML labels, including `toolwindow.stripe.MyToolWindow`. Keys live in `src/main/resources/messages/MyMessageBundle.properties`. Read them from code as in [runtime.md](runtime.md).

Logo: `src/main/resources/META-INF/pluginIcon.svg`. [Requirements](https://plugins.jetbrains.com/docs/intellij/plugin-icon-file.html): SVG, 40×40, at least 2px of padding, preferably under 3 KB. `pluginIcon_dark.svg` is optional. Do not trace a bitmap into SVG.

An action icon referenced from XML is a `@JvmField`. Without it the attribute does not resolve:

```kotlin
object ExampleIcons {
    @JvmField
    val ACTION: Icon = IconLoader.getIcon("/icons/example.svg", ExampleIcons::class.java)
}
```

`icon="com.example.ExampleIcons.ACTION"`.

## Extensions

Look up a point in [Plugin Extension Points](https://plugins.jetbrains.com/docs/intellij/plugin-extension-points.html) or the [IntelliJ Platform Explorer](https://jb.gg/ipe). Platform points use `com.intellij`. PHP points such as `typeProvider4` use `com.jetbrains.php`. A wrong namespace is ignored.

The implementation is a fully qualified class the platform constructs, not a Kotlin `object` and not a companion object.

Keep the `errorHandler` on `JetBrainsMarketplaceErrorReportSubmitter` ([error handler](https://plugins.jetbrains.com/docs/marketplace/error-handler.html#developers-side)).

A light service is not registered in XML:

```kotlin
@Service(Service.Level.PROJECT)
@State(name = "ExampleSettings", storages = [Storage("exampleSettings.xml")])
class ExampleSettings : PersistentStateComponent<ExampleSettings.State>
```

Read it with `project.service()`. Do not use `<projectService>` or `ServiceManager.getService`.

Register a settings page with `projectConfigurable` and set `parentId` to the page it belongs under. Implement `SearchableConfigurable` as in [runtime.md](runtime.md).

Put an action in an existing group with `<add-to-group>`, `anchor`, and `relative-to-action`. Do not create a group for that. A Changes tab is `changesViewContent`, not a new tool window. Set `predicateClassName` when the tab should hide.
