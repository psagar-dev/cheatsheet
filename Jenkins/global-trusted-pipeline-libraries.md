## 🛠️ Shared Library Setup

To configure the global library in Jenkins:

1. Navigate to your Jenkins **Dashboard**.
2. Click on **Manage Jenkins**.
3. Select **System**.
4. Scroll down to the section labeled **Global Trusted Pipeline Libraries**.
5. Click **Add** and fill out the fields as follows:

### Library Configuration

| Field                        | Value                                                                 |
|-----------------------------|-----------------------------------------------------------------------|
| **Name**                    | `Shared`                                                              |
| **Default Version**         | `main` **(Branch name)**                                              |
| **Retrieval Method**        | `Modern SCM`                                                          |
| **Source Code Management**  | `Git`                                                                 |
| **Project Repository**      | `https://github.com/psagar-dev/jenkins-shared-libraries.git`          |
| **Credentials**             | `psagar-dev/******` (Select your GitHub credentials if the repo is private) |

Once the library is configured, you can load it in your `Jenkinsfile` using the following syntax:

```groovy
@Library('Shared') _
```

This will enable you to use the shared functions and utilities defined in the library across your Jenkins pipelines.