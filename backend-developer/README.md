# Backend Developer Environment

Setup for running Python projects and Java Spring Boot projects on macOS.

---

## Installation

### Python

- **pyenv (recommended, multiple versions):**
  ```bash
  brew install pyenv pyenv-virtualenv
  # Add to ~/.zshrc: eval "$(pyenv init -)" and eval "$(pyenv virtualenv-init -)"
  pyenv install 3.11.5
  pyenv install 3.12.0
  pyenv global 3.12.0
  ```
- **Homebrew (single version):** `brew install python@3.12`

### Java

- **macOS (multiple versions, recommended on Mac):** Install JDKs from [Adoptium](https://adoptium.net), Oracle, or Homebrew. List and switch with the built-in helper:
  ```bash
  /usr/libexec/java_home -V                    # list all installed JVMs
  export JAVA_HOME=$(/usr/libexec/java_home -v 17)
  export PATH=$JAVA_HOME/bin:$PATH
  ```
  Use `-v 17`, `-v 21`, `-v 25` etc. to match the major version you want.
- **Homebrew:** `brew install openjdk@17` (or `openjdk@21`); then `brew link openjdk@17`.
- **SDKMAN (multiple versions, cross-platform):** `curl -s "https://get.sdkman.io" | bash` then `sdk install java 17.0.9-tem`.

### Spring Boot

No separate runtime. Use Maven or Gradle:

- **Maven:** `brew install maven` or use the wrapper (`./mvnw`) from a project generated at [start.spring.io](https://start.spring.io).
- **Gradle:** `brew install gradle` or use the wrapper (`./gradlew`) from a Spring Boot project.

Optional: `sdk install springboot` for the Spring Boot CLI.

---

## Version checking

Run these to confirm installed versions:

```bash
python3 --version
pip --version
java -version
javac -v
mvn -v
# or
gradle -v
```

---

## Version switching

| Tool | Command |
|------|--------|
| **Python (pyenv)** | `pyenv global 3.11.5` or `pyenv local 3.12.0` (per project); activate env: `pyenv activate myenv` |
| **Python (virtualenv)** | `source .venv/bin/activate` (after `python3 -m venv .venv`) |
| **Java (macOS)** | `export JAVA_HOME=$(/usr/libexec/java_home -v 17)` then `export PATH=$JAVA_HOME/bin:$PATH` (use `-v 21`, `-v 25`, etc.) |
| **Java (SDKMAN)** | `sdk use java 17.0.9-tem` (or version from `sdk list java`) |
| **Java (Homebrew only)** | Change PATH to the desired JDK (e.g. `export PATH="/opt/homebrew/opt/openjdk@21/bin:$PATH"`) |

After switching, run the version-check commands above to confirm.
