# mac-env

Role-based development and deployment environment setup for macOS. Each role has its own setup guide with **Installation**, **Version checking**, and **Version switching**, plus exercises to verify your environment.

## Prerequisites

- **macOS**
- [Homebrew](https://brew.sh) (recommended for installing many tools)

## Roles overview

| Role | Main tools | Guide |
|------|------------|--------|
| **Frontend Developer** | nvm, Node, npm, yarn, bun, Java, Android Studio, Xcode; APK/AAB, IPA builds; React, React Native, Android/iOS native | [frontend-developer/README.md](frontend-developer/README.md) |
| **Backend Developer** | Python (pyenv), Java, Maven/Gradle, Spring Boot | [backend-developer/README.md](backend-developer/README.md) |
| **Full-Stack Developer** | All frontend + backend tools | [full-stack-developer/README.md](full-stack-developer/README.md) |
| **Deployment Server** | Jenkins, Docker, Java; mobile/web/backend deployment | [deployment-server/README.md](deployment-server/README.md) |

## Common pattern

Every role’s README includes three sections:

- **Installation** — How to install each tool (macOS-focused).
- **Version checking** — Commands to print installed versions.
- **Version switching** — How to switch between versions (e.g. nvm, pyenv, SDKMAN).

After setup, run the **Exercise** in that role’s `Exercise/` folder to switch versions, echo versions, and confirm everything works.

## Quick start

1. Choose a role above and open its README.
2. Follow **Installation**, then **Version checking** and **Version switching**.
3. Complete the tasks in that role’s **Exercise** folder (e.g. [frontend-developer/Exercise/](frontend-developer/Exercise/)).
