# Backend Developer Exercises

Use these tasks to prove your environment works and that version switching takes effect.

---

## 1. Python version switch and echo

1. Install two Python versions with pyenv (if not already):
   ```bash
   pyenv install 3.11.5
   pyenv install 3.12.0
   ```
2. Set global to 3.11 and check:
   ```bash
   pyenv global 3.11.5
   python3 --version
   pip --version
   ```
3. Set global to 3.12 and check again:
   ```bash
   pyenv global 3.12.0
   python3 --version
   pip --version
   ```
4. Create a small script and run it with both versions:
   ```bash
   echo 'import sys; print("Hello from", sys.version)' > /tmp/main.py
   pyenv global 3.11.5 && python3 /tmp/main.py
   pyenv global 3.12.0 && python3 /tmp/main.py
   ```

---

## 2. Java / Spring Boot

1. Switch Java version (macOS example: use `-v 17`, `-v 21`, etc. as needed):
   ```bash
   export JAVA_HOME=$(/usr/libexec/java_home -v 17)
   export PATH=$JAVA_HOME/bin:$PATH
   java -version
   javac -version
   ```
   Or with SDKMAN: `sdk use java 17.0.9-tem` then run the version commands.
2. Create a minimal Spring Boot app from [start.spring.io](https://start.spring.io) (e.g. Java 17, Maven, no extra dependencies), download and unzip.
3. Run the app:
   ```bash
   cd <spring-boot-project>
   ./mvnw spring-boot:run
   ```
   Or with Gradle: `./gradlew bootRun`.
4. Confirm the app starts (e.g. visit http://localhost:8080 if there is a web dependency). Stop with Ctrl+C.
5. **(Optional)** Switch to another Java version and run again to confirm the runtime version changes.

---

## Quick version check (all tools)

```bash
echo "Python: $(python3 --version)" && echo "pip: $(pip --version)" && echo "Java: $(java -version 2>&1 | head -1)" && echo "Maven: $(mvn -v 2>&1 | head -1)"
```

Success: you can switch Python and Java versions and see the echoed versions change; the Spring Boot app runs with the active Java.
