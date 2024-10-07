### Tasks

  1. Explain in your own words and with examples what Shell Scripting means for DevOps.
   -  Shell scripting in DevOps refers to using shell commands in a script to automate repetitive tasks that would otherwise require manual intervention. It helps streamline operations, improve consistency, and save time by automating essential system administration tasks.

  2. What is #!/bin/bash? Can we write #!/bin/sh as well?
   - The #!/bin/bash at the top of a script is called a shebang. It tells the system which interpreter to use to execute the script. In this case, it specifies that the script should be run using the Bash shell (/bin/bash).
   - Yes, we can write #!/bin/sh as well, depending on the system and which shell is available. sh refers to the Bourne shell or a compatible shell, while bash is an extended version with more features (Bourne Again Shell).
   - There are different types of shells, such as Bash, KornShell (ksh), and Bourne shell (sh). We choose #!/bin/sh or #!/bin/bash based on the location and availability of the shell on the system.
  3. Write a Shell Script that prints I will complete #90DaysOfDevOps challenge.
   - We need to create a `s.sh` file to write the script and grant execution permission before running it.
   ```
   574n13y@574n13y:~/workspace/test$ ./s.sh
    I Will Complete #90DaysofDevops Challenge.
   574n13y@574n13y:~/workspace/test$ cat s.sh
     #!/bin/bash

     echo "I Will Complete #90DaysofDevops Challenge."

   574n13y@574n13y:~/workspace/test$
   ``` 
  4. Write a Shell Script that takes user input, input from arguments, and prints the variables.
   - A simple shell script that demonstrates taking user input, reading arguments passed to the script, and printing the variables.
   ```
    574n13y@574n13y:~/workspace/test$ ./print_var.sh
     Enter your first name: vivesh
     Enter your last name: tyagi
     First argument:
     Second argument:
     First Name: vivesh
     Last Name: tyagi
    574n13y@574n13y:~/workspace/test$ cat print_var.sh
     #!/bin/bash

     # Taking input from arguments
     arg1=$1
     arg2=$2

     # Taking input from the user
     read -p "Enter your first name: " first_name
     read -p "Enter your last name: " last_name

     # Printing the values
     echo "First argument: $arg1"
     echo "Second argument: $arg2"
     echo "First Name: $first_name"
     echo "Last Name: $last_name"

    574n13y@574n13y:~/workspace/test$
   ```
  5. Provide an example of an If-Else statement in Shell Scripting by comparing two numbers.
   - Example of an IF-else statement is as follow - 
   ```
    574n13y@574n13y:~/workspace/test$ vi if_else.sh
    574n13y@574n13y:~/workspace/test$ sudo chmod 700 if_else.sh
    574n13y@574n13y:~/workspace/test$ ./if_else.sh
     10 is less than 20
    574n13y@574n13y:~/workspace/test$ cat if_else.sh
     #!/bin/bash

      # Define two numbers
      num1=10
      num2=20

      # Compare the numbers
       if [ $num1 -gt $num2 ]; then
         echo "$num1 is greater than $num2"
       elif [ $num1 -lt $num2 ]; then
         echo "$num1 is less than $num2"
       else
         echo "$num1 is equal to $num2"
       fi

    574n13y@574n13y:~/workspace/test$
   ```
 
