# Tasks

### Task 1:
- Set your user name and email address, which will be associated with your commits.

  ```
  git config --global user.name "Your Name"
  git config --global user.email "your_email@example.com"

  ```

### Task 2:
- Create a repository named "DevOps" on GitHub.

 1. Go to GitHub and log in to your account.
 2. Click on the "New" button (usually located on the top right) to create a new repository.
 3. Enter "DevOps" as the repository name.
 4. Optionally, add a description, and choose whether to make it public or private.
 5. Click "Create repository.
             "OR "
 1. Open Visual Studio Code (VS Code): Create a directory named "DevOps."
 2. Log in to GitHub via VS Code: Use the GitHub extension or the built-in Git features to log in to your GitHub account.
 3. Open the Integrated Terminal in VS Code: In the newly created "DevOps" directory, open the integrated terminal.
 4. Initialize a Git Repository: Run the command git init in the terminal to initialize a new Git repository.
  
  
- Connect your local repository to the repository on GitHub.
 1. Open your terminal and navigate to the directory where you want to create your local repository.
 2. Initialize a new Git repository:
  ```
  mkdir DevOps
  cd DevOps
  git init
  ```
 3. Add the remote repository you just created:
  ```
  git remote add origin https://github.com/574n13y/DevOps.git
  ```
  
- Create a new file in Devops/Git/Day-02.txt & add some content to it.
 1. Create the necessary directories and file:
  ```
  mkdir -p Git
  echo "This is some content for Day 02." > Git/Day-02.txt
  ```
 2. Stage the new file for commit:
  `git add Git/Day-02.txt`
 3. Commit the Changes:
  ```
  git commit -m "Day-02.txt added with initial content"
  ```
- Push your local commits to the repository on GitHub.
  ```
  git push -u origin master
  ```
### Summary
  ```
   # Task 1: Set user name and email
   git config --global user.name "Your Name"
   git config --global user.email "your_email@example.com"
   
   # Task 2: Create and push repository
   mkdir DevOps
   cd DevOps
   git init
   git remote add origin https://github.com/your_username/DevOps.git
   mkdir -p Git
   echo "This is some content for Day 02." > Git/Day-02.txt
   git add Git/Day-02.txt
   git commit -m "Add Day-02.txt with initial content"
   git push -u origin master

  ```
