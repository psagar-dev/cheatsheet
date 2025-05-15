# 🔐 Jenkins: Add "Username with Password" Credentials (Step-by-Step)

This guide explains how to create **Username with Password** credentials in Jenkins for use in pipelines and jobs.

## ✅ Use Case

These credentials are commonly used for:

- 🐳 Docker Hub authentication  
- 🧾 Git repositories using HTTPS authentication  
- 🔗 External services requiring basic authentication  

## 🪜 Step-by-Step Instructions

### 🏠 Step 1: Go to Jenkins Dashboard
- Open your Jenkins instance in the browser.
- Example: `http://localhost:8080`

### 🔐 Step 2: Navigate to Credentials
- Click on: `Manage Jenkins` (left sidebar)
- Then click: `Credentials`

### 🌍 Step 3: Open the "Global" Domain
- Click: `System`
- Then click: `Global credentials (unrestricted)`

### ➕ Step 4: Click "Add Credentials"
- In the left sidebar, click `Add Credentials`

### 📝 Step 5: Fill in the Credential Form

#### 👤 ➤ Kind:
- Select: `Username with password`

#### 🌐 ➤ Scope:
- Select: `Global (Jenkins, nodes, items, all child items, etc)`

#### 🧑‍💻 ➤ Username:
- Enter your username for the service  
  _Example_: `docker_user`

#### 🔒 ➤ Password:
- Enter the corresponding password

#### 🆔 ➤ ID (Optional):
- Provide a custom ID to reference this credential in scripts  
  _Example_: `docker-hub-creds`

#### 📄 ➤ Description:
- Provide a useful description  
  _Example_: `Credentials for pushing to Docker Hub`

### ✅ Step 6: Click "Create"
- Click the **blue "Create"** button at the bottom of the form.

## 💡Tip: Using in Jenkinsfile

Here’s an example of how to use these credentials in a `Jenkinsfile`:

```groovy
pipeline {
    agent any
    stages {
        stage('Docker Login') {
            steps {
                script {
                    docker.withRegistry('https://index.docker.io/v1/', 'docker-hub-creds') {
                        docker.image('my-image').push()
                    }
                }
            }
        }
    }
}
```