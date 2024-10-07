### Task Day05 

1. Create Directories Using Shell Script: 
 (a).Write a bash script createDirectories.sh that, when executed with three arguments (directory name, start number of directories, and end number of directories), creates a specified number of directories with a dynamic directory name.
 (b). Example 1: When executed as ./createDirectories.sh day 1 90, it creates 90 directories as day1 day2 day3 ... day90.
 (c). Example 2: When executed as ./createDirectories.sh Movie 20 50, it creates 31 directories as Movie20 Movie21 Movie22 ... Movie50.
  - Let's create a shell script with marking three agr mandatory. 
  ```
   s74n13y@574n13y:~/workspace/test$ cat directories.sh
#!/bin/bash

# Check if exactly three arguments are provided
if [ $# -ne 3 ]; then
  echo "Usage: $0 <directory_name> <start_number> <end_number>"
  exit 1
fi

# Assign arguments to variables
dir_name=$1
start=$2
end=$3

# Check if start and end are numbers and if end is greater than or equal to start
if ! [[ "$start" =~ ^[0-9]+$ ]] || ! [[ "$end" =~ ^[0-9]+$ ]]; then
  echo "Start and end must be positive integers."
  exit 1
fi

if [ $start -gt $end ]; then
  echo "End number must be greater than or equal to start number."
  exit 1
fi

# Create directories in the range
for (( i=$start; i<=$end; i++ ))
do
  mkdir "${dir_name}${i}"
done

echo "Directories created successfully from ${dir_name}${start} to ${dir_name}${end}."

s74n13y@574n13y:~/workspace/test$ ./directories.sh devops 1 90
Directories created successfully from devops1 to devops90.
s74n13y@574n13y:~/workspace/test$ ls -lrth
total 400K
drwxr-xr-x 2 s74n13y s74n13y 4.0K Oct  7 20:07 0
-rwx------ 1 s74n13y s74n13y  733 Oct  7 20:14 directories.sh
drwxr-xr-x 2 s74n13y s74n13y 4.0K Oct  7 20:15 devops1
drwxr-xr-x 2 s74n13y s74n13y 4.0K Oct  7 20:15 devops6
drwxr-xr-x 2 s74n13y s74n13y 4.0K Oct  7 20:15 devops5
drwxr-xr-x 2 s74n13y s74n13y 4.0K Oct  7 20:15 devops4
drwxr-xr-x 2 s74n13y s74n13y 4.0K Oct  7 20:15 devops3
drwxr-xr-x 2 s74n13y s74n13y 4.0K Oct  7 20:15 devops2
drwxr-xr-x 2 s74n13y s74n13y 4.0K Oct  7 20:15 devops9
drwxr-xr-x 2 s74n13y s74n13y 4.0K Oct  7 20:15 devops8
drwxr-xr-x 2 s74n13y s74n13y 4.0K Oct  7 20:15 devops7
drwxr-xr-x 2 s74n13y s74n13y 4.0K Oct  7 20:15 devops12
drwxr-xr-x 2 s74n13y s74n13y 4.0K Oct  7 20:15 devops11
drwxr-xr-x 2 s74n13y s74n13y 4.0K Oct  7 20:15 devops10
drwxr-xr-x 2 s74n13y s74n13y 4.0K Oct  7 20:15 devops15
drwxr-xr-x 2 s74n13y s74n13y 4.0K Oct  7 20:15 devops14
drwxr-xr-x 2 s74n13y s74n13y 4.0K Oct  7 20:15 devops13
drwxr-xr-x 2 s74n13y s74n13y 4.0K Oct  7 20:15 devops18
drwxr-xr-x 2 s74n13y s74n13y 4.0K Oct  7 20:15 devops17
drwxr-xr-x 2 s74n13y s74n13y 4.0K Oct  7 20:15 devops16
drwxr-xr-x 2 s74n13y s74n13y 4.0K Oct  7 20:15 devops21
drwxr-xr-x 2 s74n13y s74n13y 4.0K Oct  7 20:15 devops20
drwxr-xr-x 2 s74n13y s74n13y 4.0K Oct  7 20:15 devops19
drwxr-xr-x 2 s74n13y s74n13y 4.0K Oct  7 20:15 devops23
drwxr-xr-x 2 s74n13y s74n13y 4.0K Oct  7 20:15 devops22
drwxr-xr-x 2 s74n13y s74n13y 4.0K Oct  7 20:15 devops26
drwxr-xr-x 2 s74n13y s74n13y 4.0K Oct  7 20:15 devops25
drwxr-xr-x 2 s74n13y s74n13y 4.0K Oct  7 20:15 devops24
drwxr-xr-x 2 s74n13y s74n13y 4.0K Oct  7 20:15 devops30
drwxr-xr-x 2 s74n13y s74n13y 4.0K Oct  7 20:15 devops29
drwxr-xr-x 2 s74n13y s74n13y 4.0K Oct  7 20:15 devops28
drwxr-xr-x 2 s74n13y s74n13y 4.0K Oct  7 20:15 devops27
drwxr-xr-x 2 s74n13y s74n13y 4.0K Oct  7 20:15 devops34
drwxr-xr-x 2 s74n13y s74n13y 4.0K Oct  7 20:15 devops33
drwxr-xr-x 2 s74n13y s74n13y 4.0K Oct  7 20:15 devops32
drwxr-xr-x 2 s74n13y s74n13y 4.0K Oct  7 20:15 devops31
drwxr-xr-x 2 s74n13y s74n13y 4.0K Oct  7 20:15 devops37
drwxr-xr-x 2 s74n13y s74n13y 4.0K Oct  7 20:15 devops36
drwxr-xr-x 2 s74n13y s74n13y 4.0K Oct  7 20:15 devops35
drwxr-xr-x 2 s74n13y s74n13y 4.0K Oct  7 20:15 devops42
drwxr-xr-x 2 s74n13y s74n13y 4.0K Oct  7 20:15 devops41
drwxr-xr-x 2 s74n13y s74n13y 4.0K Oct  7 20:15 devops40
drwxr-xr-x 2 s74n13y s74n13y 4.0K Oct  7 20:15 devops39
drwxr-xr-x 2 s74n13y s74n13y 4.0K Oct  7 20:15 devops38
drwxr-xr-x 2 s74n13y s74n13y 4.0K Oct  7 20:15 devops46
drwxr-xr-x 2 s74n13y s74n13y 4.0K Oct  7 20:15 devops45
drwxr-xr-x 2 s74n13y s74n13y 4.0K Oct  7 20:15 devops44
drwxr-xr-x 2 s74n13y s74n13y 4.0K Oct  7 20:15 devops43
drwxr-xr-x 2 s74n13y s74n13y 4.0K Oct  7 20:15 devops54
drwxr-xr-x 2 s74n13y s74n13y 4.0K Oct  7 20:15 devops53
drwxr-xr-x 2 s74n13y s74n13y 4.0K Oct  7 20:15 devops52
drwxr-xr-x 2 s74n13y s74n13y 4.0K Oct  7 20:15 devops51
drwxr-xr-x 2 s74n13y s74n13y 4.0K Oct  7 20:15 devops50
drwxr-xr-x 2 s74n13y s74n13y 4.0K Oct  7 20:15 devops49
drwxr-xr-x 2 s74n13y s74n13y 4.0K Oct  7 20:15 devops48
drwxr-xr-x 2 s74n13y s74n13y 4.0K Oct  7 20:15 devops47
drwxr-xr-x 2 s74n13y s74n13y 4.0K Oct  7 20:15 devops59
drwxr-xr-x 2 s74n13y s74n13y 4.0K Oct  7 20:15 devops58
drwxr-xr-x 2 s74n13y s74n13y 4.0K Oct  7 20:15 devops57
drwxr-xr-x 2 s74n13y s74n13y 4.0K Oct  7 20:15 devops56
drwxr-xr-x 2 s74n13y s74n13y 4.0K Oct  7 20:15 devops55
drwxr-xr-x 2 s74n13y s74n13y 4.0K Oct  7 20:15 devops65
drwxr-xr-x 2 s74n13y s74n13y 4.0K Oct  7 20:15 devops64
drwxr-xr-x 2 s74n13y s74n13y 4.0K Oct  7 20:15 devops63
drwxr-xr-x 2 s74n13y s74n13y 4.0K Oct  7 20:15 devops62
drwxr-xr-x 2 s74n13y s74n13y 4.0K Oct  7 20:15 devops61
drwxr-xr-x 2 s74n13y s74n13y 4.0K Oct  7 20:15 devops60
drwxr-xr-x 2 s74n13y s74n13y 4.0K Oct  7 20:15 devops70
drwxr-xr-x 2 s74n13y s74n13y 4.0K Oct  7 20:15 devops69
drwxr-xr-x 2 s74n13y s74n13y 4.0K Oct  7 20:15 devops68
drwxr-xr-x 2 s74n13y s74n13y 4.0K Oct  7 20:15 devops67
drwxr-xr-x 2 s74n13y s74n13y 4.0K Oct  7 20:15 devops66
drwxr-xr-x 2 s74n13y s74n13y 4.0K Oct  7 20:15 devops74
drwxr-xr-x 2 s74n13y s74n13y 4.0K Oct  7 20:15 devops73
drwxr-xr-x 2 s74n13y s74n13y 4.0K Oct  7 20:15 devops72
drwxr-xr-x 2 s74n13y s74n13y 4.0K Oct  7 20:15 devops71
drwxr-xr-x 2 s74n13y s74n13y 4.0K Oct  7 20:15 devops78
drwxr-xr-x 2 s74n13y s74n13y 4.0K Oct  7 20:15 devops77
drwxr-xr-x 2 s74n13y s74n13y 4.0K Oct  7 20:15 devops76
drwxr-xr-x 2 s74n13y s74n13y 4.0K Oct  7 20:15 devops75
drwxr-xr-x 2 s74n13y s74n13y 4.0K Oct  7 20:15 devops83
drwxr-xr-x 2 s74n13y s74n13y 4.0K Oct  7 20:15 devops82
drwxr-xr-x 2 s74n13y s74n13y 4.0K Oct  7 20:15 devops81
drwxr-xr-x 2 s74n13y s74n13y 4.0K Oct  7 20:15 devops80
drwxr-xr-x 2 s74n13y s74n13y 4.0K Oct  7 20:15 devops79
drwxr-xr-x 2 s74n13y s74n13y 4.0K Oct  7 20:15 devops88
drwxr-xr-x 2 s74n13y s74n13y 4.0K Oct  7 20:15 devops87
drwxr-xr-x 2 s74n13y s74n13y 4.0K Oct  7 20:15 devops86
drwxr-xr-x 2 s74n13y s74n13y 4.0K Oct  7 20:15 devops85
drwxr-xr-x 2 s74n13y s74n13y 4.0K Oct  7 20:15 devops84
drwxr-xr-x 2 s74n13y s74n13y 4.0K Oct  7 20:15 devops90
drwxr-xr-x 2 s74n13y s74n13y 4.0K Oct  7 20:15 devops89
s74n13y@574n13y:~/workspace/test$
  ```
2. Create a Script to Backup All Your Work:

Backups are an important part of a DevOps Engineer's day-to-day activities. The video in the references will help you understand how a DevOps Engineer takes backups (it can feel a bit difficult but keep trying, nothing is impossible).
  ```
  s74n13y@574n13y:~/workspace/test$ ./backup.sh /home/s74n13y/workspace/test/ test
Creating backup directory: test
Compressing /home/s74n13y/workspace/test/ to test/backup_20241007_202531.tar.gz
Backup completed: test/backup_20241007_202531.tar.gz
s74n13y@574n13y:~/workspace/test$ ls -lrth
total 40K
-rwx------ 1 s74n13y s74n13y 1.4K Oct  7 20:24 backup.sh
drwxr-xr-x 2 s74n13y s74n13y 4.0K Oct  7 20:25 test
s74n13y@574n13y:~/workspace/test$ ls -lrth test/
total 16K
-rw-r--r-- 1 s74n13y s74n13y 15K Oct  7 20:25 backup_20241007_202531.tar.gz
s74n13y@574n13y:~/workspace/test$ cat backup.sh
#!/bin/bash

# Backup script to compress and optionally upload work

# Variables
SOURCE_DIR=$1    # Directory to backup
BACKUP_DIR=${2:-"$HOME/backups"}  # Backup directory, defaults to $HOME/backups if not provided
DATE=$(date +"%Y%m%d_%H%M%S")
BACKUP_FILE="${BACKUP_DIR}/backup_${DATE}.tar.gz"
UPLOAD_TO_S3=false   # Set this to true if you want to upload to AWS S3 (optional)
BUCKET_NAME="your-s3-bucket-name"

# Function to check if directory exists
check_directory() {
  if [ ! -d "$1" ]; then
    echo "Directory $1 does not exist!"
    exit 1
  fi
}

# Function to create backup directory if it doesn't exist
create_backup_dir() {
  if [ ! -d "$BACKUP_DIR" ]; then
    echo "Creating backup directory: $BACKUP_DIR"
    mkdir -p "$BACKUP_DIR"
  fi
}

# Function to compress the source directory
compress_files() {
  echo "Compressing $SOURCE_DIR to $BACKUP_FILE"
  tar -czf "$BACKUP_FILE" -C "$SOURCE_DIR" .
}

# Function to upload backup to AWS S3 (optional)
upload_to_s3() {
  if [ "$UPLOAD_TO_S3" = true ]; then
    echo "Uploading backup to S3 bucket $BUCKET_NAME..."
    aws s3 cp "$BACKUP_FILE" "s3://$BUCKET_NAME/"
  fi
}

# Main script
if [ -z "$SOURCE_DIR" ]; then
  echo "Usage: $0 <source_directory> [backup_directory]"
  exit 1
fi

check_directory "$SOURCE_DIR"
create_backup_dir
compress_files
upload_to_s3

echo "Backup completed: $BACKUP_FILE"

s74n13y@574n13y:~/workspace/test$

  ```

3. Read About Cron and Crontab to Automate the Backup Script:

Cron is the system's main scheduler for running jobs or tasks unattended. A command called crontab allows the user to submit, edit, or delete entries to cron. A crontab file is a user file that holds the scheduling information.
  ```
  #!/bin/bash

# Variables
BACKUP_DIR="$HOME/backup"  # Define where the backups will be stored
SOURCE_DIR="$HOME/work"    # Define the directory to backup
TIMESTAMP=$(date +'%Y%m%d%H%M%S')  # Get a timestamp for the backup name
BACKUP_FILE="$BACKUP_DIR/backup-$TIMESTAMP.tar.gz"

# Create backup directory if it doesn't exist
mkdir -p "$BACKUP_DIR"

# Create the backup
tar -czvf "$BACKUP_FILE" "$SOURCE_DIR"

# Print message on successful backup
echo "Backup created at $BACKUP_FILE"

  ```

4. Read About User Management:

A user is an entity in a Linux operating system that can manipulate files and perform several other operations. Each user is assigned an ID that is unique within the system. IDs 0 to 999 are assigned to system users, and local user IDs start from 1000 onwards.
 ```
  In Linux, a user represents an individual account used to log into and operate the system. Every user is associated with a User ID (UID), and there are various ways to manage users, including adding, modifying, and deleting accounts.

1. Types of Users:
System Users: These are users required by the system for running services like root, daemon, etc. Their UID ranges from 0 to 999.
Regular Users: These are non-system users who log into the system to perform tasks. Their UID starts from 1000 upwards.
2. User Components:
Username: The name associated with the user.
UID (User ID): A unique numerical identifier for each user. The superuser (root) has a UID of 0.
GID (Group ID): Each user belongs to a group, identified by a GID.
Home Directory: The default directory for a user, usually /home/username.
Shell: The default command interpreter (e.g., /bin/bash).
3. User Management Commands:
Adding a User: You can create a new user with the useradd command.

bash
Copy code
sudo useradd username
Common options:

-m: Create a home directory for the user.
-s: Set the default shell for the user.
-d: Define the home directory.
Example:

bash
Copy code
sudo useradd -m -s /bin/bash -d /home/newuser newuser
Setting a Password: After creating a user, set a password using the passwd command.

bash
Copy code
sudo passwd username
Modifying a User: To modify an existing user, use the usermod command.

bash
Copy code
sudo usermod -l newname oldname  # Change the username
sudo usermod -d /new/home/dir username  # Change home directory
Deleting a User: To remove a user, you can use the userdel command.

bash
Copy code
sudo userdel username  # Deletes the user but not their home directory
sudo userdel -r username  # Deletes the user and their home directory
4. Groups:
Users can be assigned to groups, which control permissions for files and directories.

Primary Group: The default group assigned to a user when they are created.

Supplementary Groups: Additional groups a user can belong to.

Managing Groups:

Add a new group:
bash
Copy code
sudo groupadd groupname
Add a user to a group:
bash
Copy code
sudo usermod -aG groupname username
View group membership:
bash
Copy code
groups username
5. Important Files Related to User Management:
/etc/passwd: Contains details about the users, including usernames, UID, GID, home directory, and shell. Example line:

ruby
Copy code
username:x:1001:1001:User Name,,,:/home/username:/bin/bash
/etc/shadow: Stores hashed passwords for users and password-related details (requires superuser privileges to view).

/etc/group: Contains group information, including group names and GIDs.

6. Special User: root:
The root user has UID 0 and has full administrative privileges to perform any operation on the system. It is the superuser account used for administrative tasks like installing software, changing system configurations, and managing users.

7. Switching Users:
To switch to another user, use the su (substitute user) command:

bash
Copy code
su - username
Or use sudo to run commands as another user, especially root:

bash
Copy code
sudo command
Summary:
Users in Linux are entities associated with unique UIDs.
Linux uses files like /etc/passwd, /etc/shadow, and /etc/group to manage user information.
Key commands include useradd, usermod, userdel, and passwd.
Groups control access to resources, and users can belong to multiple groups for permissions.
 ```

