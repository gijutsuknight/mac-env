# Deployment Server Environment

Setup for Jenkins-based auto deployment: mobile app deployment, web deployment, and backend application deployment. Uses Jenkins (with Java and optionally Docker) and assumes pipeline agents have access to Git, Node, Java, and optionally Python (see other role guides).

---

## Installation

### Java (required for Jenkins)

Jenkins needs Java 11 or 17. Install per [backend-developer/README.md](../backend-developer/README.md) (Homebrew or SDKMAN).

### Jenkins

- **Docker (recommended for isolation):**
  ```bash
  docker run -d -p 8080:8080 -p 50000:50000 --name jenkins jenkins/jenkins:lts
  ```
  Get initial admin password: `docker exec jenkins cat /var/jenkins_home/secrets/initialAdminPassword`
- **Native (Homebrew):**
  ```bash
  brew install jenkins-lts
  brew services start jenkins-lts
  ```
  Open http://localhost:8080 and complete setup.

### Docker (optional)

For containerized builds or deployment targets:

- **Docker Desktop:** [docker.com/products/docker-desktop](https://www.docker.com/products/docker-desktop/)
- **CLI only:** `brew install docker` (daemon not included; use Docker Desktop for full stack).

### CLI tools used in pipelines

Pipelines typically need Git, Node (web/frontend builds), Java (backend/Android), and optionally Python. Install and configure these per:

- [frontend-developer/README.md](../frontend-developer/README.md) (Node, Java, Android SDK)
- [backend-developer/README.md](../backend-developer/README.md) (Python, Java)

Ensure the user that runs Jenkins (e.g. `jenkins` or your user) has these tools on PATH.

---

## Version checking

```bash
java -version
docker -v
```

Jenkins version: open the Jenkins UI (e.g. http://localhost:8080) and check the footer or **Manage Jenkins → About**. If you use Jenkins CLI: `java -jar jenkins-cli.jar -s http://localhost:8080 version` (after downloading the CLI from the server).

---

## Version switching

- **Java used by Jenkins:** Jenkins uses the Java that is first on the process `PATH` when it starts. To use a specific JDK:
  - **Native (Homebrew):** Set `JAVA_HOME` and `PATH` before starting Jenkins (e.g. in launchd env or `~/.zshrc` if you start Jenkins manually). Example: `export JAVA_HOME=/opt/homebrew/opt/openjdk@17` and `export PATH=$JAVA_HOME/bin:$PATH`.
  - **Docker:** Use an image that ships the desired JDK, or mount a volume with the correct `JAVA_HOME`/PATH for the container.
- **Docker:** Switch Docker daemon version by upgrading Docker Desktop or the `docker` package; no per-project “version switch” for Docker itself.

After changing Java, restart Jenkins and run a pipeline that echoes `java -version` to confirm.

---

## Pipeline scope (high level)

- **Mobile:** Build APK/AAB or IPA using Node, Java, Android SDK, and/or Xcode (often on an agent with frontend-developer tools).
- **Web:** Build frontend assets (e.g. `npm ci && npm run build`) and deploy to a server or static host.
- **Backend:** Build and run Java/Python services (e.g. `./mvnw package` or `pip install` + run) and deploy to a server or container.

Detailed pipeline code (Jenkinsfiles) can live in your application repos or a separate deployment repo.
