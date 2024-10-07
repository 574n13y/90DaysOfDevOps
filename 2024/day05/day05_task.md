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
-rw-r--r-- 1 s74n13y s74n13y    6 Oct  3 19:20 README.md
-rwx------ 1 s74n13y s74n13y 2.8K Oct  5 16:00 virtualization.txt
-rw-r--r-- 1 s74n13y s74n13y   55 Oct  5 17:48 devops.txt
-rw-r--r-- 1 s74n13y s74n13y   52 Oct  5 18:14 Colors.txt
-rw-r--r-- 1 s74n13y s74n13y   58 Oct  5 18:14 fruits.txt
-rwx------ 1 s74n13y s74n13y   64 Oct  6 19:57 s.sh
-rwx------ 1 s74n13y s74n13y  320 Oct  6 20:17 print_var.sh
-rwx------ 1 s74n13y s74n13y  252 Oct  6 20:27 if_else.sh
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

3. Read About Cron and Crontab to Automate the Backup Script:

Cron is the system's main scheduler for running jobs or tasks unattended. A command called crontab allows the user to submit, edit, or delete entries to cron. A crontab file is a user file that holds the scheduling information.

4. Read About User Management:

A user is an entity in a Linux operating system that can manipulate files and perform several other operations. Each user is assigned an ID that is unique within the system. IDs 0 to 999 are assigned to system users, and local user IDs start from 1000 onwards.


