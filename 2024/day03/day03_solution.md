### Tasks 
  1. View the content of a file and display line numbers.
   - Let's start by creating a file and adding some values to display line numbers. We've created the `virtualization.txt` file, so let's move on to task 1. 
   
    ```
      input - 
      574n13y@574n13y/workspace/test$ cat -n virtualization.txt
   ```
   
   ```
      output - 
       1  'Virtualization'
       2  Virtualization is the process of creating a virtual version of something, typically hardware, an operating system, storage, or network resources. Instead of running directly on physical hardware, virtual instances run on a host machine that emulates the underlying hardware resources.
       3
       4  Types of Virtualization:
       5
       6  Hardware Virtualization: Emulates physical hardware using hypervisors. Examples include VMware, Hyper-V, and KVM.
       7  OS Virtualization (Containerization): Runs multiple isolated instances (containers) on a single OS kernel. Examples include Docker and Kubernetes.
       8  Network Virtualization: Combines hardware and software resources to create a virtual network, often used in SDN (Software-Defined Networking).
       9  Storage Virtualization: Abstracts multiple physical storage devices into a unified storage resource.
       10  Hypervisors:
       11
       12  Type 1 (Bare Metal): Runs directly on hardware (e.g., VMware ESXi, Microsoft Hyper-V).
       13  Type 2 (Hosted): Runs on top of an existing OS (e.g., VirtualBox, VMware Workstation).
   ```

  2. Change the access permissions of files to make them readable, writable, and executable by the owner only.
    - Let's modify the permissions for the `virtualization.txt` file so that only the owner has read, write, and execute permissions. The command to do this will be `chmod 700 virtualization.txt`.
     ```
      574n13y@574n13y:~/workspace/test$ ls -lrth
      total 8.0K
      -rw-r--r-- 1 574n13y 574n13y    6 Oct  3 19:20 README.md
      -rw-r--r-- 1 574n13y 574n13y 2.8K Oct  5 16:00 virtualization.txt
      574n13y@574n13y:~/workspace/test$ chmod 700 virtualization.txt
      574n13y@574n13y:~/workspace/test$ ls -lrth
      total 8.0K
      -rw-r--r-- 1 574n13y 574n13y    6 Oct  3 19:20 README.md
      -rwx------ 1 574n13y 574n13y 2.8K Oct  5 16:00 virtualization.txt
      574n13y@574n13y:~/workspace/test$
     ``` 

  3. Check the last 10 commands you have run.
   - To check the last 10 commands you have run in a Linux/Unix terminal, you can use the history command with the tail command to display just the last 10 entries.
    ```
    574n13y@574n13y:~/workspace/test$ history | tail -n 10
      704  cd test/
      705  ls
      706  cat README.md
      707  vi virtualization.txt
      708  cat -n virtualization.txt
      709  ls -lrth
      710  chmod 700 virtualization.txt
      711  ls -lrth
      712  cd aws\ keys/
      713  history | tail -n 10
     574n13y@574n13y:~/workspace/test$
    ```
  4. Remove a directory and all its contents.
   - To remove a directory and all its contents (including files and subdirectories) in Linux/Unix, you can use the rm command with the -r (recursive) -f(forcefully) option.
   ```
     574n13y@574n13y:~/workspace$ ls -lrth
     total 28K
     drwxr-xr-x  3 574n13y 574n13y 4.0K Sep  2 04:46 shell
     drwxr-xr-x  3 574n13y 574n13y 20.0K Oct  5 16:00 test
     drwxr-xr-x  2 574n13y 574n13y 4.0K Oct  5 16:24 list
     574n13y@574n13y:~/workspace$ ls -lrth list/
     total 4.0K
     -rwx------ 1 574n13y 574n13y 2.8K Oct  5 16:23 virtualization.txt
     -rw-r--r-- 1 574n13y 574n13y    0 Oct  5 16:24 9
     -rw-r--r-- 1 574n13y 574n13y    0 Oct  5 16:24 8
     -rw-r--r-- 1 574n13y 574n13y    0 Oct  5 16:24 7
     -rw-r--r-- 1 574n13y 574n13y    0 Oct  5 16:24 6
     -rw-r--r-- 1 574n13y 574n13y    0 Oct  5 16:24 5
     -rw-r--r-- 1 574n13y 574n13y    0 Oct  5 16:24 4
     -rw-r--r-- 1 574n13y 574n13y    0 Oct  5 16:24 3
     -rw-r--r-- 1 574n13y 574n13y    0 Oct  5 16:24 2
     -rw-r--r-- 1 574n13y 574n13y    0 Oct  5 16:24 1
     574n13y@574n13y:~/workspace$ rm -rf list/
     574n13y@574n13y:~/workspace$ ls -lrth
      total 24K
     drwxr-xr-x  3 574n13y 574n13y 4.0K Sep  2 04:46 shell
     drwxr-xr-x  3 574n13y 574n13y 20.0K Oct  5 16:00 test
     574n13y@574n13y:~/workspace$
   ```

  5. Create a fruits.txt file, add content (one fruit per line), and display the content. 
   - Lets create a `fruits.txt` file  via a touch and add content through vi. Lets begin 
   ```
    574n13y@574n13y:~/workspace/test$ touch fruits.txt
    574n13y@574n13y:~/workspace/test$ vi fruits.txt
    574n13y@574n13y:~/workspace/test$ cat fruits.txt
     Apple
     Orange
     Kiwi
     Banana
     Dragon friut
     chiku
     Sweet patato
   ```
  6. Add content in devops.txt (one in each line) - Apple, Mango, Banana, Cherry, Kiwi, Orange, Guava. Then, append "Pineapple" to the end of the file.
   - Let's create a file named `devops.txt` and add the specified content using the `echo` command. 
   ```

    574n13y@574n13y:~/workspace/test$ vi devops.txt
    574n13y@574n13y:~/workspace/test$ cat devops.txt
     Apple
     Mango
     Banana
     Cherry
     Kiwi
     Orange
     Guava.
    574n13y@574n13y:~/workspace/test$ echo "Pineapple" >> devops.txt
    574n13y@574n13y:~/workspace/test$ cat devops.txt
     Apple
     Mango
     Banana
     Cherry
     Kiwi
     Orange
     Guava.
     Pineapple
    s74n13y@574n13y:~/workspace/test$

   ```
  7. Show the first three fruits from the file in reverse order.
   - To show the first three fruits from the devops.txt file in reverse order,`tac`
   ```
     574n13y@574n13y:~/workspace/test$ head -n 3 devops.txt | tac
      Banana
      Mango
      Apple
     574n13y@574n13y:~/workspace/test$

   ```
  8. Show the bottom three fruits from the file, and then sort them alphabetically.
   - To display the last three fruits from the devops.txt file and sort them alphabetically, `sort`
  ```
   574n13y@574n13y:~/workspace/test$ tail -n 3 devops.txt | sort
    Guava.
    Orange
    Pineapple
   574n13y@574n13y:~/workspace/test$
  ```
  9. Create another file Colors.txt, add content (one color per line), and display the content.
   - To create a file named Colors.txt, add colors to it (one color per line), and then display the content,`echo`
   ```
    574n13y@574n13y:~/workspace/test$ echo -e "Red\nGreen\nBlue\nYellow\nOrange" > Colors.txt
    574n13y@574n13y:~/workspace/test$ cat Colors.txt
     Red
     Green
     Blue
     Yellow
     Orange
    574n13y@574n13y:~/workspace/test$
   ```
  10. Add content in Colors.txt (one in each line) - Red, Pink, White, Black, Blue, Orange, Purple, Grey. Then, prepend "Yellow" to the beginning of the file. 
   - To add the specified colors to Colors.txt and then prepend "Yellow" to the beginning of the file, `echo -e`
    ```
     574n13y@574n13y:~/workspace/test$ echo -e "Red\nPink\nWhite\nBlack\nBlue\nOrange\nPurple\nGrey" > Colors.txt
     574n13y@574n13y:~/workspace/test$ echo "Yellow" | cat - Colors.txt > temp && mv temp Colors.txt
     574n13y@574n13y:~/workspace/test$ cat Colors.txt
      Yellow
      Red
      Pink
      White
      Black
      Blue
      Orange
      Purple
      Grey
     574n13y@574n13y:~/workspace/test$
    ```
  11. Find and display the lines that are common between fruits.txt and Colors.txt.
   - To find and display the lines that are common between fruits.txt and Colors.txt, you can use the comm or grep command. First sort both files 
   ```
    574n13y@574n13y:~/workspace/test$ sort Colors.txt -o Colors.txt
    574n13y@574n13y:~/workspace/test$ sort fruits.txt -o fruits.txt
    574n13y@574n13y:~/workspace/test$ comm -12 fruits.txt Colors.txt
     Orange
    574n13y@574n13y:~/workspace/test$ grep -Fxf fruits.txt Colors.txt
     Orange
    574n13y@574n13y:~/workspace/test$
   ```
  12. Count the number of lines, words, and characters in both fruits.txt and Colors.txt.
   - To count the number we can use `wc` 
   ```
    574n13y@574n13y:~/workspace/test$ wc fruits.txt Colors.txt
     8   9  58 fruits.txt
     9   9  52 Colors.txt
     17  18 110 total
    574n13y@574n13y:~/workspace/test$
   ```  
