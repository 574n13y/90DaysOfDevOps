## Basic linux commands

### Listing commands
```ls option_flag arguments ```--> list the sub directories and files avaiable in the present directory

Examples:

- ``` ls -l ```--> list the files and directories in long list format with extra information
- ```ls -a ```--> list all including hidden files and directory
- ```ls *.sh``` --> list all the files having .sh extension.

- ```ls -i ``` --> list the files and directories with index numbers inodes
- ``` ls -d */``` --> list only directories.(we can also specify a pattern)
- ``` ls -lrth ``` ---> will list all files and directories: In long format (-l), Sorted by modification time (-t), but in reverse order (-r), so the oldest files are listed first, With file sizes displayed in a human-readable format (-h).


### Directoy commands
- ```pwd``` --> print work directory. Gives the present working directory.

- ```cd path_to_directory``` --> change directory to the provided path

- ```cd ~ ``` or just  ```cd ``` --> change directory to the home directory

- ``` cd - ``` --> Go to the last working directory.

- ``` cd ..``` --> change directory to one step back.

- ``` cd ../..``` --> Change directory to 2 levels back.

- ``` mkdir  directoryName``` --> to make a directory in a specific location

Examples:
```
mkdir newFolder              # make a new folder 'newFolder'

mkdir .NewFolder              # make a hidden directory (also . before a file to make it hidden)

mkdir A B C D                  #make multiple directories at the same time

mkdir /home/user/Mydirectory   # make a new folder in a specific location

mkdir -p  A/B/C/D              # make a nested directory
```

### Basic Commands

- `cd` - Change directory
- `pwd` - Show the current working directory
- `ls` - List directory contents
- `cp` - Copy files or directories
- `mv` - Move or rename files or directories
- `rm` - Remove files or directories
- `echo` - Print text to the terminal
- `cat` - Concatenate and display the contents of files
- `less` - View the contents of a file one page at a time
- `grep` - Search for a pattern within files
- `mkdir` - Create a new directory
- `touch` - Create a new file or update the timestamp of an existing file
- `chmod` - Change file permissions
- `man` - Display the manual for a command


### Understanding `chmod` Values

The `chmod` command uses numeric values to set file permissions:

- `0` - No permissions (---)
- `1` - Execute only (--x)
- `2` - Write only (-w-)
- `3` - Write and execute (-wx)
- `4` - Read only (r--)
- `5` - Read and execute (r-x)
- `6` - Read and write (rw-)
- `7` - Read, write, and execute (rwx)

**Example:** `chmod 777` gives read, write, and execute permissions to everyone.

- `r` - Read (4)
- `w` - Write (2)
- `x` - Execute (1)

