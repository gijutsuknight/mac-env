# Deployment Server Exercises

Prove Jenkins runs and that version switching (e.g. Java) is reflected in the pipeline.

---

## 1. Start Jenkins and note version

1. Start Jenkins (choose one):
   - **Docker:** `docker run -d -p 8080:8080 -p 50000:50000 --name jenkins jenkins/jenkins:lts`
   - **Native:** `brew services start jenkins-lts`
2. Open http://localhost:8080 and complete the initial setup (unlock with the printed or logged password, install suggested plugins, create admin user).
3. In the UI, check the Jenkins version (footer or **Manage Jenkins → About**). Note it as “success” for this step.

---

## 2. Minimal pipeline (echo versions)

Create a pipeline that runs on the built-in agent and echoes tool versions so you can confirm Node, Java, and optionally Python are available to Jenkins.

1. In Jenkins: **New Item** → name (e.g. `version-check`) → **Pipeline** → OK.
2. Under **Pipeline**, choose **Pipeline script** and paste:

```groovy
pipeline {
    agent any
    stages {
        stage('Echo versions') {
            steps {
                sh 'echo "Hello from Jenkins"'
                sh 'java -version 2>&1 || true'
                sh 'node -v 2>&1 || true'
                sh 'npm -v 2>&1 || true'
                sh 'python3 --version 2>&1 || true'
            }
        }
    }
}
```

3. **Save** and **Build Now**.
4. Open the build and check **Console Output**. Confirm you see “Hello from Jenkins” and the output of `java -version`, `node -v`, etc. If a tool is not installed on the agent, that line may show an error; install it per [frontend-developer](../frontend-developer/README.md) or [backend-developer](../backend-developer/README.md) and ensure the Jenkins process has it on PATH.

Success: the pipeline runs and the console shows the versions (or clear errors for missing tools).

---

## 3. (Optional) Switch Java and re-run pipeline

1. Change the Java version used when starting Jenkins (see [deployment-server README — Version switching](../README.md#version-switching)): set `JAVA_HOME`/PATH to a different JDK, then restart Jenkins.
2. Run the same pipeline again and check **Console Output** for `java -version`. The reported version should match the JDK you switched to.

Success: after switching Java and restarting Jenkins, the pipeline’s `java -version` output reflects the new version.
