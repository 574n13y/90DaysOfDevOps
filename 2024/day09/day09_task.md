## Challenge Description

Your task is to create a bash script that takes a directory path as a command-line argument and performs a backup of the directory. The script should create timestamped backup folders and copy all the files from the specified directory into the backup folder.

Additionally, the script should implement a rotation mechanism to keep only the last 3 backups. This means that if there are more than 3 backup folders, the oldest backup folders should be removed to ensure only the most recent backups are retained.

> The script will create a timestamped backup folder inside the specified directory and copy all the files into it. It will also check for existing backup folders and remove the oldest backups to keep only the last 3 backups.

## Example Usage

Assume the script is named `backup_with_rotation.sh`. Here's an example of how it will look,
also assuming the script is executed with the following commands on different dates:

1. First Execution (2023-07-30):

```
$ ./backup_with_rotation.sh /home/user/documents
```

Output:

```
Backup created: /home/user/documents/backup_2023-07-30_12-30-45
Backup created: /home/user/documents/backup_2023-07-30_15-20-10
Backup created: /home/user/documents/backup_2023-07-30_18-40-55
```

After this execution, the /home/user/documents directory will contain the following items:

```
backup_2023-07-30_12-30-45
backup_2023-07-30_15-20-10
backup_2023-07-30_18-40-55
file1.txt
file2.txt
...
```

2. Second Execution (2023-08-01):

```
$ ./backup_with_rotation.sh /home/user/documents
```

Output:

```
Backup created: /home/user/documents/backup_2023-08-01_09-15-30
```

After this execution, the /home/user/documents directory will contain the following items:

```
backup_2023-07-30_15-20-10
backup_2023-07-30_18-40-55
backup_2023-08-01_09-15-30
file1.txt
file2.txt
...
```

In this example, the script creates backup folders with timestamped names and retains only the last 3 backups while removing the older backups.

## Submission Instructions

Create a bash script named backup_with_rotation.sh that implements the Directory Backup with Rotation as described in the challenge.
```
#!/bin/bash

# Check if directory path is provided as argument
if [ -z "$1" ]; then
  echo "Usage: $0 <directory_path>"
  exit 1
fi

# Get the directory path from the argument
DIR_PATH=$1

# Check if the directory exists
if [ ! -d "$DIR_PATH" ]; then
  echo "Error: Directory $DIR_PATH does not exist."
  exit 1
fi

# Generate timestamp for the backup folder
TIMESTAMP=$(date +"%Y-%m-%d_%H-%M-%S")

# Create a backup folder inside the specified directory with the current timestamp
BACKUP_DIR="$DIR_PATH/backup_$TIMESTAMP"
mkdir "$BACKUP_DIR"

# Copy all files and directories from the specified directory to the backup folder
cp -r "$DIR_PATH"/* "$BACKUP_DIR"

# Confirm backup creation
echo "Backup created: $BACKUP_DIR"

# Rotate backups: Keep only the last 3 backup folders
BACKUP_COUNT=$(ls -d "$DIR_PATH"/backup_* 2> /dev/null | wc -l)

if [ "$BACKUP_COUNT" -gt 3 ]; then
  # Find and remove the oldest backup(s) if there are more than 3
  OLDEST_BACKUP=$(ls -dt "$DIR_PATH"/backup_* | tail -n +4)
  echo "Removing oldest backup(s):"
  echo "$OLDEST_BACKUP"
  rm -rf $OLDEST_BACKUP
fi
```
