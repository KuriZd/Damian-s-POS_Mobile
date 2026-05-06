# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

**Damian's POS Mobile** is an Android point-of-sale application built with Kotlin and Jetpack Compose. The project is in early development — the foundational structure is in place, but business logic, navigation, state management, and API integration are not yet implemented.

## Build Commands

```bash
./gradlew assembleDebug          # Build debug APK
./gradlew assembleRelease        # Build release APK
./gradlew test                   # Run unit tests (JVM)
./gradlew connectedAndroidTest   # Run instrumented tests (requires device/emulator)
./gradlew lint                   # Run Android Lint
./gradlew clean                  # Clean build artifacts
```

To run a single unit test class:
```bash
./gradlew test --tests "com.example.damian_s_pos_mobile.ExampleUnitTest"
```

## Tech Stack

- **Language**: Kotlin 2.0.21
- **UI**: Jetpack Compose with Material 3
- **Build**: Gradle 8.12.3 with Kotlin DSL (`build.gradle.kts`)
- **Dependency management**: Gradle Version Catalog at `gradle/libs.versions.toml`
- **Min SDK**: 24 | **Target/Compile SDK**: 36 | **JVM**: Java 11

## Architecture

Currently a single-module project under `app/`. Source lives at `app/src/main/java/com/example/damian_s_pos_mobile/`.

- `MainActivity.kt` — single entry point; sets Compose content
- `ui/theme/` — Material 3 color palette (`Color.kt`), theme composition (`Theme.kt`), and typography (`Type.kt`)

All dependencies are declared in `gradle/libs.versions.toml` — add new dependencies there, not directly in `build.gradle.kts`.

`settings.gradle.kts` enforces `RepositoriesMode.FAIL_ON_PROJECT_REPOS`, meaning all repositories must be declared in the settings file, not in module build files.

## Development Notes

- No navigation framework is wired up yet; the app is a single-screen template.
- No state management (ViewModel, StateFlow) has been added yet.
- No HTTP client or backend integration exists yet.
- Compose compiler uses the Kotlin Compose plugin — do not add the separate `kotlinCompilerExtensionVersion` config.
- Compose BOM version is pinned in `gradle/libs.versions.toml` under `compose-bom`; bump it there to update all Compose artifacts together.
