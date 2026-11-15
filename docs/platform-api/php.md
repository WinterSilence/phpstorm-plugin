# com.jetbrains.php

PHP index and class hierarchy. `PhpTypeProvider4` and `PhpInspection` live under `lang`. Those are the types [php.md](../php.md) and [inspections.md](../inspections.md) use. Confirm a signature in the [IntelliJ Platform Explorer](https://jb.gg/ipe) before calling it.

## Entry points

- `PhpIndex` — finds PHP classes, functions, and files in the project index.
- `PhpClassHierarchyUtils` — walks superclasses and interfaces.

## Icons

- `PhpIcons` — icons for PHP files and structure nodes.

## Subpackages

Counts are stable classes in that subtree.

- `arrangement` — 7
- `codeInsight` — 41
- `completion` — 1
- `config` — 3
- `lang` — 436
- `refactoring` — 1
- `util` — 1


--- Rules in scope for this file ---
[From: AGENTS.md]
# PhpStorm plugin

SDK pages linked from `build.gradle.kts`, `gradle.properties`, `README.md`, and `CHANGELOG.md` win over these articles. Use public stable API only: no `@Deprecated`, `@ApiStatus.ScheduledForRemoval`, `@ApiStatus.Internal`, or `@ApiStatus.Experimental`. Confirm a signature in the [IntelliJ Platform Explorer](https://jb.gg/ipe) or the attached platform sources.

Read one article:

- Build, Gradle, run, publish: [docs/build.md](docs/build.md)
- `plugin.xml`, dependencies, services, icons: [docs/registration.md](docs/registration.md)
- EDT, actions, UI, strings: [docs/runtime.md](docs/runtime.md)
- PHP types, suppressors, Structure: [docs/php.md](docs/php.md)
- Local inspections: [docs/inspections.md](docs/inspections.md)
- Stable platform and PHP types: [docs/platform-api.md](docs/platform-api.md)
