# Task: Error Handling in Shell Scripting

### Task 1: Checking Exit Status
- Write a script that attempts to create a directory and checks if the command was successful. If not, print an error message.

```
#!/bin/bash

# Attempt to create a directory
mkdir /path/to/new_directory

# Check if the command was successful
if [ $? -eq 0 ]; then
    echo "Directory created successfully."
else
    echo "Failed to create directory."
fi

```


### Task 2: Using `if` Statements for Error Checking
- Modify the script from Task 1 to include more commands (e.g., creating a file inside the directory) and use `if` statements to handle errors at each step.

```
#!/bin/bash

# Attempt to create a directory
if mkdir /path/to/new_directory; then
    echo "Directory created successfully."
    
    # Attempt to create a file inside the new directory
    if touch /path/to/new_directory/sample_file.txt; then
        echo "File created successfully inside the directory."
    else
        echo "Failed to create the file inside the directory."
    fi

else
    echo "Failed to create directory."
fi

```


### Task 3: Using `trap` for Cleanup
- Write a script that creates a temporary file and sets a `trap` to delete the file if the script exits unexpectedly.

```
#!/bin/bash

# Create a temporary file
temp_file=$(mktemp)

# Set up a trap to delete the temporary file on exit or interruption
trap "rm -f $temp_file; echo 'Temporary file deleted.'" EXIT

# Simulate some operations
echo "This is a temporary file." > $temp_file

# Simulate an unexpected exit
exit 1

```


### Task 4: Redirecting Errors
- Write a script that tries to read a non-existent file and redirects the error message to a file called `error.log`.

```
#!/bin/bash

# Try to read a non-existent file and redirect error to error.log
cat /path/to/non_existent_file.txt 2> error.log

echo "Attempted to read a non-existent file. Check error.log for details."

```

### Task 5: Creating Custom Error Messages
- Modify one of the previous scripts to include custom error messages that provide more context about what went wrong.

```
#!/bin/bash

# Attempt to create a directory
if mkdir /path/to/new_directory; then
    echo "Directory created successfully."
    
    # Attempt to create a file inside the new directory
    if touch /path/to/new_directory/sample_file.txt; then
        echo "File created successfully inside the directory."
    else
        echo "Error: Could not create the file inside /path/to/new_directory. Please check permissions."
    fi

else
    echo "Error: Could not create the directory /path/to/new_directory. Directory might already exist, or check permissions."
fi

```
