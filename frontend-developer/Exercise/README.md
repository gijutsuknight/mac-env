# Frontend Developer Exercises

Use these tasks to prove your environment works and that version switching takes effect.

---

## 1. Node version switch and echo

1. Install two Node versions (if not already):
   ```bash
   nvm install 18
   nvm install 20
   ```
2. Switch to Node 18 and print versions:
   ```bash
   nvm use 18
   node -v
   npm -v
   ```
3. Switch to Node 20 and print again:
   ```bash
   nvm use 20
   node -v
   npm -v
   ```
4. **(Optional)** Run a minimal React app once:
   ```bash
   npx create-react-app test-app && cd test-app && npm start
   ```
   Stop with Ctrl+C and remove the folder if desired.

---

## 2. Java version switch and echo

1. If using SDKMAN, list and use two versions:
   ```bash
   sdk list java
   sdk use java 17.0.9-tem
   java -version
   javac -v
   sdk use java 21.0.1-tem
   java -version
   javac -v
   ```
2. If using Homebrew, switch PATH to a different JDK and run `java -version` and `javac -v` to confirm.

---

## 3. Package managers (yarn, bun)

In a temporary directory:

```bash
mkdir -p /tmp/frontend-exercise && cd /tmp/frontend-exercise
npm init -y
npm -v
yarn -v
yarn add lodash
bun -v
bun add lodash
```

Echo versions again to confirm yarn and bun work. You can delete `/tmp/frontend-exercise` when done.

---

## 4. Android (optional)

- Start an emulator from Android Studio or run `emulator -list-avds` then `emulator -avd <name>`.
- In a minimal Android project (or one from Android Studio), run:
  ```bash
  ./gradlew tasks
  ./gradlew assembleDebug
  ```
- Confirm `adb devices` lists your device/emulator.

---

## 5. iOS (optional)

- Open a minimal Xcode project (or create one) and run:
  ```bash
  xcodebuild -list
  ```
- Start a simulator from Xcode or: `open -a Simulator`.

---

## Quick version check (all tools)

Run in one go to echo all frontend-related versions:

```bash
echo "Node: $(node -v)" && echo "npm: $(npm -v)" && echo "Yarn: $(yarn -v)" && echo "Bun: $(bun -v)" && echo "Java: $(java -version 2>&1 | head -1)" && echo "Xcode: $(xcodebuild -version | head -1)"
```

Success: you see the expected versions and can switch Node/Java and see the output change.
