# macOS Android CLI Setup (No Android Studio)

## 1) Install required tools

```bash
brew install --cask temurin
brew install gradle android-commandlinetools
```

Optional helpful tools:

```bash
brew install --cask visual-studio-code
brew install adb
```

## 2) Configure SDK environment variables

Add this to `~/.zshrc`:

```bash
export ANDROID_SDK_ROOT="$HOME/Library/Android/sdk"
export ANDROID_HOME="$ANDROID_SDK_ROOT"
export PATH="$PATH:$ANDROID_SDK_ROOT/cmdline-tools/latest/bin"
export PATH="$PATH:$ANDROID_SDK_ROOT/platform-tools"
export PATH="$PATH:$ANDROID_SDK_ROOT/emulator"
```

Apply changes:

```bash
source ~/.zshrc
```

## 3) Install SDK components with `sdkmanager`

```bash
yes | sdkmanager --licenses
sdkmanager "platform-tools"
sdkmanager "build-tools;35.0.0"
sdkmanager "platforms;android-35"
```

## 4) (Optional) Android TV emulator image

```bash
sdkmanager "emulator"
sdkmanager "system-images;android-35;android-tv;x86_64"
```

## 5) Create Android TV AVD from terminal

```bash
avdmanager create avd -n FireTVSimTvApi35 -k "system-images;android-35;android-tv;x86_64"
```

## 6) Start emulator

```bash
emulator -avd FireTVSimTvApi35
```

## 7) Build app from terminal

```bash
cd android-tv-launcher
./gradlew :app:assembleDebug
```

## 8) Install app to running emulator/device

```bash
cd android-tv-launcher
adb devices
./gradlew :app:installDebug
```

## 9) Run app manually on Android TV launcher

- Open app list on emulator/device.
- Launch `FireTV Simulator`.
