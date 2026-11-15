# PhpStorm plugin

SDK pages linked from `build.gradle.kts`, `gradle.properties`, `README.md`, and `CHANGELOG.md` win over these articles. Use public stable API only: no `@Deprecated`, `@ApiStatus.ScheduledForRemoval`, `@ApiStatus.Internal`, or `@ApiStatus.Experimental`. Confirm a signature in the [IntelliJ Platform Explorer](https://jb.gg/ipe) or the attached platform sources.

Read one article:

- Build, Gradle, run, publish: [docs/build.md](docs/build.md)
- `plugin.xml`, dependencies, services, icons: [docs/registration.md](docs/registration.md)
- EDT, actions, UI, strings: [docs/runtime.md](docs/runtime.md)
- PHP types, suppressors, Structure: [docs/php.md](docs/php.md)
- Local inspections: [docs/inspections.md](docs/inspections.md)
- Stable platform and PHP types: [docs/platform-api.md](docs/platform-api.md), then the package page it links for the types you call
