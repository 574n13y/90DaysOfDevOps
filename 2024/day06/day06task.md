1. **Understanding File Permissions:**
   - Create a simple file and run `ls -ltr`.
   ```
    s74n13y@574n13y:~/workspace/test$touch day06task.txt
    s74n13y@574n13y:~/workspace/test$ls -ltr
    -rw-r--r-- 1 s74n13y s74n13y    0 Oct  9 16:41 day06task.txt
    
   ```
   - Each of the three permissions are assigned to three defined categories of users. The categories are:
     - **Owner:** The owner of the file or application.
       - Use `chown` to change the ownership permission of a file or directory.
      ```
       s74n13y@574n13y:~/workspace/test$sudo chown vivs day06task.txt
       chown: invalid user: ‘vivs’
       s74n13y@574n13y:~/workspace/test$sudo useradd vivs
       s74n13y@574n13y:~/workspace/test$ sudo chown vivs day06task.txt
       s74n13y@574n13y:~/workspace/test$ ls -ltr day06task.txt
       -rw-r--r-- 1 vivs s74n13y 0 Oct  9 16:41 day06task.txt
       s74n13y@574n13y:~/workspace/test$
       
      ```
     - **Group:** The group that owns the file or application.
       - Use `chgrp` to change the group permission of a file or directory.
      ```
       s74n13y@574n13y:~/workspace/test$ sudo chgrp esh day06task.txt
       chgrp: invalid group: ‘esh’
       s74n13y@574n13y:~/workspace/test$ sudo groupadd esh
       s74n13y@574n13y:~/workspace/test$ sudo chgrp esh day06task.txt
       s74n13y@574n13y:~/workspace/test$ ls -lrt day06task.txt
       -rw-r--r-- 1 vivs esh 0 Oct  9 16:41 day06task.txt
       s74n13y@574n13y:~/workspace/test$
      ```
     - **Others:** All users with access to the system (outside the users in a group).
       - Use `chmod` to change the other users' permissions of a file or directory.
   - Task: Change the user permissions of the file and note the changes after running `ls -ltr`.
    ```
     s74n13y@574n13y:~/workspace/test$ sudo chmod o+w day06task.txt
     s74n13y@574n13y:~/workspace/test$ ls -lrth day06task.txt
     -rw-r--rw- 1 vivs esh 0 Oct  9 16:41 day06task.txt
     s74n13y@574n13y:~/workspace/test$
    ```

2. **Writing an Article:**
   - Write an article about file permissions based on your understanding from the notes.

# Understanding File Permissions in Linux
  File permissions in Linux are essential for controlling who can access, modify, or execute files and directories. These permissions ensure security and proper management of resources. Each file or directory has permissions assigned to three categories of users:

  - **Owner**: The creator or designated owner of the file.
  - **Group**: A group of users with shared permissions.
  - **Others**: All other users outside the file's group.

## Permission Structure

  When you list files with `ls -ltr`, you’ll see a structure like:[refer this for more detail](https://github.com/574n13y/90DaysOfDevOps/tree/stanley/2024/2024/day02)

```bash
   -rw-r--r-- 1 owner group size date filename
```
3. **Access Control Lists (ACL):**
   - Read about ACL and try out the commands `getfacl` and `setfacl`.

## Understanding Access Control Lists (ACL) in Linux
Access Control Lists (ACL) provide a more granular permission mechanism than the traditional file permission system in Linux. While the standard permission model allows setting permissions for the owner, group, and others, ACLs enable defining permissions for specific users and groups on a per-file or per-directory basis.
   - Task: Create a directory and set specific ACL permissions for different users and groups. Verify the permissions using `getfacl`.
```
s74n13y@574n13y:~/workspace/test$ mkdir acl_dir
s74n13y@574n13y:~/workspace/test$ sudo setfacl -m u:vivs:rw acl_dir
s74n13y@574n13y:~/workspace/test$ sudo setfacl -m g:esh:x acl_dir
s74n13y@574n13y:~/workspace/test$ ls -lrth | grep acl_dir
drwxrwxr-x+ 2 s74n13y s74n13y 4.0K Oct  9 17:05 acl_dir
s74n13y@574n13y:~/workspace/test$ getfacl acl_dir
# file: acl_dir
# owner: s74n13y
# group: s74n13y
user::rwx
user:vivs:rw-
group::r-x
group:esh:--x
mask::rwx
other::r-x

s74n13y@574n13y:~/workspace/test$sudo setfacl -x u:vivs acl_dir
s74n13y@574n13y:~/workspace/test$ getfacl acl_dir
# file: acl_dir
# owner: s74n13y
# group: s74n13y
user::rwx
group::r-x
group:esh:--x
mask::r-x
other::r-x

s74n13y@574n13y:~/workspace/test$
```
ACLs offer an advanced way to manage permissions by allowing you to assign custom access rights to specific users or groups. By using setfacl and getfacl, you can effectively control access to files and directories beyond the default permission system.


4. **Additional Tasks:**
   - **Task:** Create a script that changes the permissions of multiple files in a directory based on user input.
```
#!/bin/bash

# Script to change permissions for multiple files in a directory based on user input

# Ask the user for the directory path
read -p "Enter the directory path: " directory

# Check if the directory exists
if [ ! -d "$directory" ]; then
    echo "Directory does not exist!"
    exit 1
fi

# Ask the user for the permission to set (e.g., 755)
read -p "Enter the permissions you want to set (e.g., 755): " permissions

# Ask the user to enter file names (space-separated)
read -p "Enter the file names (space-separated): " files

# Change the permissions for each specified file
for file in $files; do
    if [ -f "$directory/$file" ]; then
        chmod "$permissions" "$directory/$file"
        echo "Permissions for $file have been changed to $permissions."
    else
        echo "File $file does not exist in the directory."
    fi
done

```
```
chmod +x change_permissions.sh
./change_permissions.sh
```
   - **Task:** Write a script that sets ACL permissions for a user on a given file, based on user input.
```
#!/bin/bash

# Script to set ACL permissions for a user on a specific file

# Ask the user for the file path
read -p "Enter the file path: " filepath

# Check if the file exists
if [ ! -f "$filepath" ]; then
    echo "File does not exist!"
    exit 1
fi

# Ask the user for the username
read -p "Enter the username to set ACL permissions: " username

# Ask the user for the permissions (e.g., rwx, r--, etc.)
read -p "Enter the ACL permissions for the user (e.g., rwx, r--, etc.): " permissions

# Set the ACL permissions for the specified user
setfacl -m u:$username:$permissions "$filepath"

# Verify that the ACL has been set
echo "ACL permissions for $username on $filepath have been set to $permissions."
getfacl "$filepath"

```
```
chmod +x set_acl.sh
./set_acl.sh
```
5. **Understanding Sticky Bit, SUID, and SGID:**
   - Read about sticky bit, SUID, and SGID.
   - Task: Create examples demonstrating the use of sticky bit, SUID, and SGID, and explain their significance.
# Sticky Bit, SUID, and SGID in Linux

Linux provides advanced permission mechanisms: **Sticky Bit**, **SUID (Set User ID)**, and **SGID (Set Group ID)**, enhancing security and access control.

## 1. Sticky Bit
- **Purpose**: Restricts file deletion in directories. Only the file owner, directory owner, or root can delete or rename files.
- **Example**:
  1. Create a directory:
     ```bash
     mkdir /tmp/shared_dir
     ```
  2. Set permissions:
     ```bash
     chmod 777 /tmp/shared_dir
     ```
  3. Enable sticky bit:
     ```bash
     chmod +t /tmp/shared_dir
     ```
  4. Verify:
     ```bash
     ls -ld /tmp/shared_dir
     ```
     Output: `drwxrwxrwt`

### Significance
Prevents users from deleting files they do not own in shared directories.

---

## 2. SUID (Set User ID)
- **Purpose**: Executes a file with the owner’s permissions, typically `root`.
- **Example**:
  1. Create a script:
     ```bash
     echo -e "#!/bin/bash\necho \"Effective UID: \$(id -u)\"" > suid_example.sh
     ```
  2. Set SUID:
     ```bash
     chmod u+s suid_example.sh
     chmod +x suid_example.sh
     sudo chown root suid_example.sh
     ```
  3. Run the script:
     ```bash
     ./suid_example.sh
     ```
     Output: `Effective UID: 0`

### Significance
Allows programs to be executed with elevated privileges when necessary.

---

## 3. SGID (Set Group ID)
- **Purpose**: Executes a file with the group’s permissions or ensures new files inherit the directory’s group ownership.
- **Example**:
  1. Create a directory:
     ```bash
     mkdir sgid_dir
     ```
  2. Set SGID:
     ```bash
     chmod g+s sgid_dir
     ```
  3. Verify:
     ```bash
     ls -ld sgid_dir
     ```
     Output: `drwxrwsr-x`
  4. Create a file in the directory as a different user.

### Significance
Ensures consistent group ownership for files created in shared project directories.

---

### Summary
- **Sticky Bit**: Protects files from deletion by unauthorized users.
- **SUID**: Allows execution with owner privileges, enhancing functionality.
- **SGID**: Maintains group ownership consistency for collaborative environments.


6. **Backup and Restore Permissions:**
   - Task: Create a script that backs up the current permissions of files in a directory to a file.
```
#!/bin/bash

# Script to back up file permissions of a specified directory

# Ask the user for the directory path
read -p "Enter the directory path to back up permissions: " directory

# Check if the directory exists
if [ ! -d "$directory" ]; then
    echo "Directory does not exist!"
    exit 1
fi

# Specify the backup file
backup_file="permissions_backup.txt"

# Clear or create the backup file
> "$backup_file"

# Iterate through files in the directory and save their permissions
for file in "$directory"/*; do
    if [ -e "$file" ]; then
        # Get the file permissions in numeric format
        permissions=$(stat -c "%a" "$file")
        # Write to the backup file
        echo "$(basename "$file") $permissions" >> "$backup_file"
    fi
done

echo "Permissions backed up to $backup_file."

```
```
chmod +x backup_permissions.sh
./backup_permissions.sh
```
   - Task: Create another script that restores the permissions from the backup file.
```
#!/bin/bash

# Script to restore file permissions from a backup file

# Specify the backup file
backup_file="permissions_backup.txt"

# Check if the backup file exists
if [ ! -f "$backup_file" ]; then
    echo "Backup file does not exist!"
    exit 1
fi

# Read the backup file and restore permissions
while read -r line; do
    # Extract filename and permissions
    filename=$(echo "$line" | awk '{print $1}')
    permissions=$(echo "$line" | awk '{print $2}')

    # Restore the permissions if the file exists
    if [ -e "$filename" ]; then
        chmod "$permissions" "$filename"
        echo "Restored permissions for $filename to $permissions."
    else
        echo "File $filename does not exist; skipping."
    fi
done < "$backup_file"

echo "Permissions restoration complete."

```
```
chmod +x restore_permissions.sh
./restore_permissions.sh
```

