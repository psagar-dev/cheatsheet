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


##### 📌 4. Show Hidden Files & Directories (`-a` option)
```sh
ls -a
```

📂 **Example Output:**
```sh
.  ..  .git  .env  app  logs  scripts  config.yaml
```

##### 📖 Explanation:
- `.` (dot) represents the current directory.
- `..` (double dot) represents the parent directory.
- Files and directories that start with a `.` (like `.git` and `.env`) are normally hidden but will be display with `ls -a`.

##### 📌 5. Human-Readable File Sizes (`-lh` option)
```sh
ls -lh
```
📂 **Example Output:**
Display file sizes in a readable format(KB, MB, GB).

```sh
-rw-r--r-- 1 user user  1.2K Feb 12 10:30 config.yaml
```
In this output, `1.2K` is easier to understand then 1200 bytes.

##### 📌 6. Human-Readable File Sizes (`-lt` option)
```sh
ls -lt
```
📂 **Example Output:**
Lists files sorted by the most recently modified.
```sh
-rw-r--r-- 1 user user  120 Feb 12 11:00 latest.log
drwxr-xr-x 2 user user  4096 Feb 12 10:30 scripts
```
In this case, `latest.log` was modified most recently.

##### 📌 7. Sorting Files by Size Using the `-lS` Option
```sh
ls -lS
```
📂 **Example Output:**

To list files in a directory sorted by size(Largest first), use the `ls` command  with the `-lS` option.

```sh
-rw-r--r-- 1 user user  15M Feb 12 10:30 backup.tar.gz
-rw-r--r-- 1 user user  5K  Feb 12 10:30 report.txt
```
In this example, `backup.tar.gz` is the largest file, appearing at the top of the list.

##### 📌 8. Recursive Listing (-R option)
```sh
ls -R
```
📂 **Example Output:**
The `ls -R` command lists files and directories recursively, displaying the structure of all subdirectories.
```sh
.:
app  logs  scripts

./app:
main.py  utils.py

./logs:
error.log  access.log
```
This command helps visualize the hierarchical structure of directories and their contents.