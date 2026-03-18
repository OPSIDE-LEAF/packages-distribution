# Leaf

---

## 🌍 Project Description

Leaf is a modular Kotlin Multiplatform (KMP) framework designed to enable scalable, reusable, and decoupled mobile application development.

The system is built around a **core architecture** and **independent feature modules**, allowing developers to compose applications dynamically by integrating only the required components.

### Key Characteristics
- Modular architecture (Core + Feature Modules)
- Kotlin Multiplatform (Android + iOS)
- Distributed via GitHub Packages (Maven)
- Scalable and reusable components

---

## 🚀 Installation

### Requirements
- GitHub account with access to packages
- Personal Access Token (PAT) with `read:packages` permission

---

### 1. Configure Credentials

Add credentials to your `local.properties`:

```properties
gpr.user=[YOUR_GITHUB_USERNAME]
gpr.key=[YOUR_GITHUB_TOKEN]
```

2. Configure Repository

Add GitHub Packages repository in settings.gradle.kts:

```Kotlin
val localProperties = java.util.Properties()
val localPropertiesFile = File(rootDir, "local.properties")
if (localPropertiesFile.exists()) {
    localProperties.load(FileInputStream(localPropertiesFile))
}

dependencyResolutionManagement {
    repositories {
        mavenCentral()

        maven {
            url = uri("https://maven.pkg.github.com/OPSIDE-LEAF/packages-distribution")
            credentials {
                username = localProperties.getProperty("gpr.user")
                password = localProperties.getProperty("gpr.key")
            }
        }
    }
}
```

3. Add Dependencies
```Kotlin
kotlin {
    sourceSets {
        commonMain.dependencies {
            implementation("com.opside-leaf:core:[VERSION]")
            implementation("com.opside-leaf:auth:[VERSION]")
        }
    }
}
```

📦 Example Usage
```Kotlin
import com.opside.core.Core
import com.opside.auth.AuthService

val core = Core()
val auth = AuthService()
```
