# Frontend Developer Environment

Setup for frontend and mobile development: APK/AAB build, IPA build, Xcode, Android Studio, Java, bun, yarn, npm, nvm. Frameworks: Android Native, iOS Native, React Native, React.

---

## Installation

### nvm (Node Version Manager)

```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.1/install.sh | bash
# Restart terminal or: source ~/.zshrc (or ~/.bashrc)
```

### Node / npm / yarn / bun

- **Node & npm:** Install via nvm (e.g. `nvm install 20`); npm is included with Node.
- **Yarn:** `corepack enable` then `corepack prepare yarn@stable --activate`, or `npm install -g yarn`.
- **Bun:** `curl -fsSL https://bun.sh/install | bash`

### Java

- **Homebrew (single version):** `brew install openjdk@17` and link: `brew link openjdk@17`.
- **SDKMAN (multiple versions):** `curl -s "https://get.sdkman.io" | bash` then `sdk install java 17.0.9-tem`.

### Android Studio

1. Download from [developer.android.com/studio](https://developer.android.com/studio).
2. Install and open; use SDK Manager to install SDK, build-tools, and CLI tools.
3. Add to PATH (e.g. in `~/.zshrc`):
   ```bash
   export ANDROID_HOME=$HOME/Library/Android/sdk
   export PATH=$PATH:$ANDROID_HOME/emulator:$ANDROID_HOME/platform-tools
   ```

### Xcode

1. Install Xcode from the App Store.
2. Install command-line tools: `xcode-select --install`.
3. Accept license: `sudo xcodebuild -license accept`.

### React / React Native

No separate install. After Node is set up:

- React: `npx create-react-app my-app`
- React Native: `npx react-native init MyApp` or use [Expo](https://expo.dev).

**Apple Silicon (M1/M2):** Android emulator may need Rosetta in some cases; prefer ARM-native images when available.

---

## Version checking

Run these to confirm installed versions:

```bash
node -v
npm -v
yarn -v
bun -v
java -version
javac -v
xcodebuild -version
adb --version
# If using Gradle in a project:
# ./gradlew --version
```

---

## Version switching

| Tool | Command |
|------|--------|
| **Node** | `nvm use 20` (or `18`); set default: `nvm alias default 20` |
| **Java (SDKMAN)** | `sdk use java 17.0.9-tem` (or other version from `sdk list java`) |
| **Java (Homebrew)** | Switch PATH to desired JDK (e.g. `export PATH="/opt/homebrew/opt/openjdk@17/bin:$PATH"`) |
| **Xcode** | `sudo xcode-select -s /Applications/Xcode.app/Contents/Developer` (or path to another Xcode) |

After switching, run the version-check commands above to confirm.
