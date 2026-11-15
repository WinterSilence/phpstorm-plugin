# Build

IntelliJ Platform Gradle Plugin 2.x only. Do not add the 1.x `intellij { }` block or `platformType` / `platformVersion`. Plugin versions stay in `settings.gradle.kts`. Kotlin 2.x is required for platform 2025.1 and later.

## Coordinate

Keep `mavenCentral()` and `intellijPlatform { defaultRepositories() }`. The `phpstorm(...)` version already in `build.gradle.kts` is the current IDE, not a ceiling. A newer release is allowed. Raise `sinceBuild` together with that version. Leave `untilBuild = provider { null }`.

Do not write `<idea-version>` or `<version>` in `plugin.xml`. Gradle patches both. `<version>` comes from `gradle.properties`.

`bundledPlugin` is a plugin shipped inside that IDE. `com.jetbrains.php` is already declared. A Marketplace plugin uses `plugin(id, version)`. `localPlugin` is only for a plugin on disk.

IDE tests use `testFramework(TestFrameworkType.Platform)` and JUnit 4 from `gradle/libs.versions.toml`, plus `testImplementation(kotlin("test"))`. Do not add `TestFrameworkType.JUnit5`: it is missing `opentest4j` and pulls JUnit 4. Pure logic with no platform classes may use JUnit 5 on the test classpath alone.

## CDN HTTP 451

`phpstorm(...)` downloads a distribution. If that download returns HTTP 451, point `local()` at the installed IDE and set `instrumentCode = false` and `buildSearchableOptions = false`. Instrumentation otherwise downloads `java-compiler-ant-tasks` from the same CDN. Leave both flags alone until a task fails on that download.

## Libraries and caches

`kotlin.stdlib.default.dependency = false` stays. Do not ship `kotlin-stdlib` or the coroutines modules the platform already provides.

`org.gradle.configuration-cache` and `org.gradle.caching` stay on. A task must not read `Project` at execution time.

## Run

Restart `runIde` after a change to `plugin.xml` or classes. The sandbox log is `.intellijPlatform/sandbox/*/*/log/idea.log`.

- `runIde` — UI, `plugin.xml`, or platform class loading. Debug from the Run IDE configuration.
- `check` — tests. Same as Run Tests.
- `verifyPlugin` — a new platform API dependency. Same as Run Verifications.
- `buildPlugin` — the archive.
- `publishPlugin` — only when asked. It runs `signPlugin` first. See [Publishing a Plugin](https://plugins.jetbrains.com/docs/intellij/publishing-plugin.html).

Do not add a changelog version or date unless asked. Add the note to the current section of `CHANGELOG.md` ([Keep a Changelog 1.1.0](https://keepachangelog.com/en/1.1.0/)).

## Identifiers

Change `template-project-name`, `template.gradle.group`, `template.plugin.id`, and `template.kotlin.package` only with `./customize` from the repository root. `./customize --help` lists the flags. The script edits `settings.gradle.kts`, `gradle.properties`, `plugin.xml`, the Kotlin package, the tool window `factoryClass`, and the titles in `README.md` and `CHANGELOG.md`.

`rootProject.name` and `group` need not match `<id>` and `<name>`. `<id>` does not change between versions.
