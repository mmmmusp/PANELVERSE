# PANELVERSE 0.3.0

Offline Android comic reader built with Kotlin, Jetpack Compose, Material 3 and Room. Android 12+ (API 31); ARM64 phones and x86-64 emulator builds.

The current design follows the user's choice of a light, glass-inspired reading experience: floating navigation, large covers, quiet white surfaces, grouped settings, and bundled Noto Sans Arabic. Dark/system themes and English remain available. New installs default to light; upgrades preserve the existing preference.

Home and Stats show current/best reading streak, a weekly view and today's progress. One minute of accumulated foreground reading qualifies a day. The reader stops counting after 90 seconds without interaction.

## Build

Open the project in Android Studio, use JDK 17, Android SDK Platform 35 and Build Tools 35.0.0. The first dependency sync requires network access; the installed app does not request Internet permission.

```powershell
.\gradlew.bat :app:assembleDebug :app:testDebugUnitTest
.\gradlew.bat :app:connectedDebugAndroidTest
```

APK: `app/build/outputs/apk/debug/app-debug.apk`. Delivery copy: `dist/PANELVERSE-0.3.0-debug.apk`.

Use Library → Add folder to grant read access through Android's document picker. Originals remain in the chosen folder; catalog, covers, progress, bookmarks and statistics remain local. Numeric-only filenames infer their series from the parent folder on rescan, preserving manual edits.

## Validation

Six JVM tests and eight instrumented tests passed on a physical Android 12 ARM64 phone. The suite includes CBZ, a stored RAR4 CBR, PDF, a 12-megapixel image, corrupt/missing files, Arabic/English navigation, and 500 real synthetic CBZ files accessed through a separate test APK's SAF provider. Test data uses an isolated Room database.

See [Arabic test report](replica/qa-v2/REPORT-ar.md), [test evidence](replica/qa-v2/final-tests-03.txt), [limitations and parity](replica/parity.md) and [bug fixes](replica/bugs.md). RAR5/solid archive variety, gigabyte archives, tablets and sustained performance remain unverified. Archive encryption and multipart volumes are not supported workflows.

Noto Sans Arabic is distributed under SIL OFL; its license is in the app assets and `replica/design/`. Public reference screenshots are research material outside Android source sets.
