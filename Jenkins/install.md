## Installing Jenkins on Ubuntu

## ✅ Prerequisites

1. **Java**: Jenkins requires Java to run.
2. A server or machine with internet access.
3. `sudo` privileges.

## 🚀 Step-by-Step Jenkins Installation (on Ubuntu)

### 🔹 Step 1: Update System Packages
```bash
sudo apt update
```

### 🔹 Step 2: Install Java (if not already installed)
```bash
sudo apt install fontconfig openjdk-21-jre
```
Check Java version:
```bash
java -version
```

### 🔹 Step 3: Add Jenkins Repository

Add the Jenkins repository key:
```bash
sudo wget -O /etc/apt/keyrings/jenkins-keyring.asc \
  https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key
```

Add the Jenkins repository entry:
```bash
echo "deb [signed-by=/etc/apt/keyrings/jenkins-keyring.asc]" \
  https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null
```

### 🔹 Step 4: Update Package List Again
```bash
sudo apt-get update
```

### 🔹 Step 5: Install Jenkins
```bash
sudo apt-get install jenkins
```

### 🔹 Step 6: Start and Enable Jenkins Service
```bash
sudo systemctl start jenkins
sudo systemctl enable jenkins
```

Check status:
```bash
sudo systemctl status jenkins
```
### 🔹 Step 7: Access Jenkins via Web Browser

Open your browser and go to:
```
http://your-server-ip:8080
```

### 🔹 Step 8: Unlock Jenkins

You’ll be prompted to enter the initial admin password. Get it using:
```bash
sudo cat /var/jenkins_home/secrets/initialAdminPassword
```

Copy and paste that password into the browser prompt.

### 🔹 Step 9: Customize Jenkins

You'll be guided through:

- Installing suggested plugins or selecting custom ones.
- Creating an admin user.
- Setting up the instance URL (usually defaults are fine).

Finally, click **"Start using Jenkins"**!