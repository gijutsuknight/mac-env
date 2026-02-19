# Full-Stack Developer Environment

This role uses the same tools as **frontend-developer** and **backend-developer**. Follow their guides for installation, version checking, and version switching.

---

## Tools overview

| Area | Tools | Guide |
|------|--------|--------|
| **Frontend** | nvm, Node, npm, yarn, bun, Java, Android Studio, Xcode; React, React Native | [frontend-developer/README.md](../frontend-developer/README.md) |
| **Backend** | Python (pyenv), Java, Maven/Gradle, Spring Boot | [backend-developer/README.md](../backend-developer/README.md) |

- **Installation:** See [frontend-developer README — Installation](../frontend-developer/README.md#installation) and [backend-developer README — Installation](../backend-developer/README.md#installation).
- **Version checking:** See [frontend-developer README — Version checking](../frontend-developer/README.md#version-checking) and [backend-developer README — Version checking](../backend-developer/README.md#version-checking).
- **Version switching:** See [frontend-developer README — Version switching](../frontend-developer/README.md#version-switching) and [backend-developer README — Version switching](../backend-developer/README.md#version-switching).

---

## Recommended order

1. **Backend stack first:** Python (pyenv) and Java (SDKMAN or Homebrew), then Maven or Gradle.
2. **Frontend stack next:** nvm, Node, npm/yarn/bun, then Android Studio and Xcode if you need mobile.

This order avoids dependency issues (e.g. Java needed for Android and Jenkins).
