# Task

A well-documented Linux and Git-GitHub cheat sheet!

---

# 🐧 **Linux & 🐙 Git-GitHub Cheat Sheet** 🌟

## 🐧 **Linux Commands**

### 🔍 **Basic Navigation**
| Command               | Description                                                |
|-----------------------|------------------------------------------------------------|
| `pwd`                 | Print the current working directory                        |
| `ls`                  | List files and directories                                 |
| `ls -l`               | List with detailed information (long format)               |
| `ls -a`               | List all files, including hidden files                     |
| `cd [directory]`      | Change to the specified directory                          |
| `cd ..`               | Move up one directory level                                |
| `mkdir [directory]`   | Create a new directory                                     |
| `rmdir [directory]`   | Remove an empty directory                                  |

### 🛠️ **File Operations**
| Command                      | Description                                                |
|------------------------------|------------------------------------------------------------|
| `touch [filename]`           | Create a new empty file                                    |
| `cat [filename]`             | Display the contents of a file                             |
| `cp [source] [destination]`  | Copy file(s) from source to destination                    |
| `mv [source] [destination]`  | Move or rename file(s)                                     |
| `rm [filename]`              | Delete a file                                              |
| `rm -r [directory]`          | Delete a directory and its contents                        |
| `nano [filename]`            | Open a file in the Nano text editor                        |
| `chmod [permissions] [file]` | Change file permissions (e.g., `chmod 755 script.sh`)      |

### 🔧 **System Monitoring**
| Command         | Description                                                    |
|-----------------|----------------------------------------------------------------|
| `top`           | Display active processes and system usage                      |
| `ps aux`        | List all running processes with detailed information           |
| `df -h`         | Show disk space usage                                          |
| `du -sh [dir]`  | Display the total disk usage of a directory                    |
| `free -h`       | Show memory usage (RAM)                                        |
| `uptime`        | Show how long the system has been running                      |

### 🌐 **Networking**
| Command                 | Description                                                        |
|-------------------------|--------------------------------------------------------------------|
| `ifconfig` / `ip a`     | Display network interfaces and IP addresses                        |
| `ping [address]`        | Test connectivity to a host (e.g., `ping google.com`)              |
| `curl [url]`            | Transfer data from or to a server (fetch web content)              |
| `scp [file] [user@host]`| Securely copy files to/from a remote host                          |
| `ssh [user@host]`       | Securely connect to a remote host via SSH                          |

---

## 🐙 **Git & GitHub Commands**

### 📂 **Repository Management**
| Command                        | Description                                                     |
|--------------------------------|-----------------------------------------------------------------|
| `git init`                     | Initialize a new Git repository                                 |
| `git clone [url]`              | Clone a repository from a URL                                   |
| `git status`                   | Check the status of your working directory                      |
| `git add [file]`               | Stage a file for the next commit                                |
| `git add .`                    | Stage all changes for the next commit                           |
| `git commit -m "[message]"`    | Commit staged changes with a message                            |
| `git push`                     | Push commits to a remote repository                             |
| `git pull`                     | Fetch and merge changes from the remote repository              |
| `git fetch`                    | Download changes from the remote without merging                |
| `git log`                      | View the commit history                                         |

### 🌳 **Branching & Merging**
| Command                         | Description                                                    |
|---------------------------------|----------------------------------------------------------------|
| `git branch`                    | List all branches                                              |
| `git branch [branch-name]`      | Create a new branch                                            |
| `git checkout [branch-name]`    | Switch to the specified branch                                 |
| `git checkout -b [branch-name]` | Create and switch to a new branch                              |
| `git merge [branch-name]`       | Merge the specified branch into the current branch             |
| `git branch -d [branch-name]`   | Delete a branch                                                |

### 🌟 **Advanced Git**
| Command                                      | Description                                                     |
|----------------------------------------------|-----------------------------------------------------------------|
| `git reset --hard [commit-hash]`             | Reset to a specific commit and discard all changes              |
| `git stash`                                 | Save uncommitted changes for later                              |
| `git stash pop`                             | Restore the most recent stashed changes                         |
| `git rebase [branch-name]`                  | Reapply commits on top of another base tip                      |
| `git remote add origin [url]`               | Link the local repository to a remote repository                |
| `git diff`                                  | Show changes between commits, branches, or working directory    |

---

## 💡 **Cheat Sheet Tips** 📌

- **Combine Commands:** Use `&&` to chain commands (e.g., `mkdir new-dir && cd new-dir`).
- **Use Wildcards:** `*` to match multiple files (e.g., `rm *.txt` deletes all `.txt` files).
- **Shortcut Branch Switching:** `git checkout -` switches back to the previous branch.
- **Use Aliases:** Set up aliases for frequently used commands (e.g., `alias gs='git status'`).

---

