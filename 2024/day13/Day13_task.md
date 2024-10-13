
### **Task 1: Feature Development with Branches**

1. **Create a Branch and Add a Feature**
   - Start by creating a new branch named `dev` from `master`:
     ```bash
     git checkout -b dev
     ```
   - Create a new file `version01.txt` inside the `Devops/Git/` directory with the following content:
     ```bash
     echo "This is the first feature of our application" > Devops/Git/version01.txt
     ```
   - Add and commit your changes:
     ```bash
     git add Devops/Git/version01.txt
     git commit -m "Added new feature"
     ```

2. **Push Changes to GitHub**
   - Push your local `dev` branch to the remote repository:
     ```bash
     git push origin dev
     ```

3. **Add More Features with Separate Commits**
   - Update `version01.txt` with new lines, and commit after each change:
     - **1st line:**
       ```bash
       echo "This is the bug fix in development branch" >> Devops/Git/version01.txt
       git commit -am "Added feature2 in development branch"
       ```
     - **2nd line:**
       ```bash
       echo "This is gadbad code" >> Devops/Git/version01.txt
       git commit -am "Added feature3 in development branch"
       ```
     - **3rd line:**
       ```bash
       echo "This feature will gadbad everything from now" >> Devops/Git/version01.txt
       git commit -am "Added feature4 in development branch"
       ```

4. **Restore the File to a Previous Version**
   - Revert the file back to when it contained only “This is the bug fix in development branch”:
     ```bash
     git revert HEAD~2
     ```

### **Task 2: Working with Branches**

1. **Demonstrate Branches**
   - Create two or more branches:
     ```bash
     git checkout -b feature1
     git checkout -b feature2
     ```
   - To show the branch structure, you can take a screenshot of the output of:
     ```bash
     git branch -a
     ```
   - (Use `git log --graph --oneline --all` to get a more visual representation.)

2. **Merge Changes into Master**
   - Switch to the `master` branch:
     ```bash
     git checkout master
     ```
   - Merge the `dev` branch into `master`:
     ```bash
     git merge dev
     ```
   - Push the merged changes to the remote `master` branch:
     ```bash
     git push origin master
     ```

3. **Practice Rebase**
   - To rebase, switch to the `dev` branch:
     ```bash
     git checkout dev
     ```
   - Perform a rebase on `master`:
     ```bash
     git rebase master
     ```
   - If there are conflicts, resolve them, add the resolved files, and continue the rebase:
     ```bash
     git add <resolved_file>
     git rebase --continue
     ```

