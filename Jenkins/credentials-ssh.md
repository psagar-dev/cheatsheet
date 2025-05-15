# Jenkins - Add SSH Credentials

This document explains the fields for adding **SSH Username with private key** credentials in Jenkins under **Global credentials (unrestricted)**.

---

## 📋 Credential Details

| Field         | Description                                                                 |
|---------------|-----------------------------------------------------------------------------|
| **Kind**      | `SSH Username with private key`                                             |
| **Scope**     | `Global (Jenkins, nodes, items, all child items, etc)`                     |
| **ID**        | *(Optional)* Unique identifier to refer to this credential programmatically |
| **Description** | *(Optional)* Human-readable description for the credential                |
| **Username**  | Username associated with the SSH private key                                |
| **Private Key** | You can either:                                                           |
|               | - **Enter directly**: Paste private key (e.g. from `~/.ssh/id_rsa`)         |
| **Passphrase**| *(Optional)* If the private key is encrypted, enter the passphrase          |

---

## ✅ Example Setup

```text
Kind:              SSH Username with private key  
Scope:             Global  
ID:                ssh-ec2  
Description:       EC2 SSH Access Key  
Username:          ubuntu  
Private Key:       -----BEGIN RSA PRIVATE KEY-----
                   ...
                   -----END RSA PRIVATE KEY-----
Passphrase:        [Optional - if your key is passphrase-protected]
````

After filling out all required fields, click the **Create** button to save the credentials.
