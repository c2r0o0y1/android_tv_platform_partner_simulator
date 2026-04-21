# Android TV Launcher (CLI + VS Code)

This module is designed for a terminal-first workflow on macOS without Android Studio.

## Structure

- Kotlin + Gradle Android app module (`app/`)
- Android TV-focused manifest (`LEANBACK_LAUNCHER`)
- Minimal activity flow: Splash -> Main -> Home/Settings
- Placeholder packages for future simulator modules:
  - `partner`
  - `content`
  - `telemetry`
  - `diagnostics`

## Prerequisites (macOS)

```bash
brew install --cask temurin
brew install gradle android-commandlinetools
```

Add to `~/.zshrc`:

```bash
export ANDROID_SDK_ROOT="$HOME/Library/Android/sdk"
export ANDROID_HOME="$ANDROID_SDK_ROOT"
export PATH="$PATH:$ANDROID_SDK_ROOT/cmdline-tools/latest/bin"
export PATH="$PATH:$ANDROID_SDK_ROOT/platform-tools"
export PATH="$PATH:$ANDROID_SDK_ROOT/emulator"
```

Then:

```bash
source ~/.zshrc
yes | sdkmanager --licenses
sdkmanager "platform-tools" "build-tools;35.0.0" "platforms;android-35"
```

## Build from terminal

```bash
cd android-tv-launcher
gradle :app:assembleDebug
```

## Optional: generate Gradle wrapper after Gradle is installed

```bash
cd android-tv-launcher
gradle wrapper
./gradlew :app:assembleDebug
```

## Install on emulator/device

```bash
adb devices
gradle :app:installDebug
```

## Optional Android TV emulator

```bash
sdkmanager "emulator" "system-images;android-35;android-tv;x86_64"
avdmanager create avd -n FireTVSimTvApi35 -k "system-images;android-35;android-tv;x86_64"
emulator -avd FireTVSimTvApi35
```
