### 🖥️ `ls` Command in DevOps

##### 📌 1. Basic `ls` Command
```sh
ls
```
##### 📤 Output:
Lists the files and directories in the **current** working directory.

📂 **Example:**
```sh
app  log  scripts  config.yaml
```

##### 📌 2. `ls` Command with a Specific Directory
```sh
ls /var/www/html/
```
- 🗂️ `ls` (list) - This command lists the files & directories inside a specified path
- 🌍 `/var/www/html` - This is the directory where web applications are typically stored on Linux servers running Apache (or sometimes Nginx)

##### 📤 Example Output:
```sh
index.html  style.css  script.js
```

##### 📌 3. List Files with Details (`-l` option)
```sh
ls -l
```

📂 **Example Output:**
- This will display detailed information about files and directories in the current directory.

```sh
drwxr-xr-x 2 user user 4096 Feb 12 10:30 app
-rw-r--r-- 1 user user 120 Feb 12 10:30 config.yaml
```
##### 📖 Understanding the Output

Each line in the output represents a file or directory and consists of the following details:

| Field                  | Example         | Description                                     |
|------------------------|----------------|-------------------------------------------------|
| **File Type & Permissions** | `drwxr-xr-x`  | File type and permissions                      |
| **Link Count**         | `2`            | Number of hard links to the file/directory     |
| **Owner**             | `user`         | User who owns the file                         |
| **Group**             | `user`         | Group associated with the file                 |
| **Size**              | `4096`         | File size in bytes                             |
| **Modification Date**  | `Feb 12 10:30` | Last modification date and time                |
| **File Name**         | `app`          | Name of the file or directory                 |