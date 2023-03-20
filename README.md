
# Git Notes

## ------------------------------Lesson 01------------------------------
1. compare two files using the following command on command prompt:  
```bash
  FC file1.extension file2.extension
```

### The following commands are supposed to be run on "git CMD".
2. To create a new version of a code use "Git" version control system, and create a commitment.
3. Compare two versions of a file using `git diff` command followed with the two version IDs of the file.
4. The best checkpoint to commit is after finishing a task in one location of the file (eg. modifying a function).
5. If you changed multiple files in one task (add parameter to a function used in different file), you can commit multiple files at once.
6. Get commits logs with statistics about which file have changes in each commit:  
```bash
git log --stat
```
7. Stop viewing the logs: press `q`, which stands for quit.
8. Download a cloned repository from Github:  
```bash
git clone the_link_to_the_repository_in_github
```
9. Show colored outputs from git results:  
```bash
git config --global color.ui auto
```
10. change the version of the project to a different previous versions:  
```bash
git checkout id_of_the_version
```
(HEAD is the commit that you're currently working on)

### Configuring Git Bash to look much better
11. Copy "git-completion.bash" file to home directory ("windows_user_name" folder).
12. Copy "git-prompt.sh" file to home directory ("windows_user_name" folder).
13. Copy ".bash_profile" file to home directory ("windows_user_name" folder).
14. Set the default text editor for Git:  
```bash
git config --global core.editor "'directory_of_the_editor_with.exe' -n -w"
```
(-n means open in a new window, -w means git will wait for the editor until the window is closed to continue).  
example of the command:  
```bash
git config --global core.editor "'C:/Users/windows_user_name/AppData/Local/Programs/Microsoft\ VS\ Code/Code.exe' -n -w"
```
(This editor will be used for writing your commit messages)  

15. Create a shortcut of the editor to run from "Git Bash":  
add the following line in the file ".bash_profile":  
`alias shortcut_name="directory_of_the_editor"`.  
example:  
`alias vscode="C:/Users/windows_user_name/AppData/Local/Programs/Microsoft\ VS\ Code/Code.exe"`  

16. Run these two commands in "Git Bash" command line:  
```bash
git config --global push.default upstream
config --global merge.conflictstyle diff3
```
## ------------------------------Lesson 02------------------------------
1. Git stores its metadata about the logs of a repository in a directory named as `".git"`, which is a hidden folder.
2. Set the Author's identity:
```bash
git config --global user.email "you@example.com"
git config --global user.name "Your Name"
```
3. Create a Git repository in a directory:  
```bash
git init
```
4. Get the status of the repository reflections:  
```bash
git status
```
(reflections are the files or directories that are tracked by Git)  

5. Add a file or folder to the staging area so that it could be tracked in the repository:  
```bash
git add name_of_the_file_or_folder
```
6. Add everything in the working directory to the staging area:  
```bash
git add .
```
7. Remove a file or directory from the staging area:  
```bash
git reset name_of_the_file_or_folder
```
8. Commit changes to the files in staging area:  
```bash
git commit
```
(This will open your selected default editor to allow you write your message
for this commit. If no default editor is set to git configuration, it will give an error.)

9. Commit changes directly with message:  
```bash
git commit -m "your message"
```
10. The staging area is a copy of the last commit.
11. Compare files changed in the working directory that are not updated to the staging area:  
```bash
git diff
```
12. Compare files updated in the staging area and the last commit:  
```bash
git diff --staged
```
13. Discard any changes in the working directory and the staging area:  
```bash
git reset --hard
```
14. Get all branches created in the repository:  
```bash
git branch
```
15. Create a branch starting from the selected commit:  
```bash
git branch name_of_the_branch
```
16. select the branch where to attach new commits:  
```bash
git checkout name_of_the_branch
```
(This will set HEAD to the last commit in the branch)

17. Visualize branches connections in the repository in a graph:  
```bash
git log --graph name_of_the_branch name_of_other_branch
```
You can aslo remove unwanted details:  
```bash
git log --graph --oneline name_of_the_branch name_of_other_branch".
```
18. Log command will only show the track of commits starting from the `Initial commit` through branches that leads to the commit where `HEAD` is attached to (each commit has its parents till the Initial commit).  
19. If a commit is created in `detached HEAD` status without creating a branch for it, then this new commit will be lost.
20. Create a new branch for the new detached HEAD commit:  
```bash
git switch -c name_of_the_new_branch
```
21. Merge two branches and the selected branch as a new commit in the selected branch:  
```bash
git merge name_of_the_first_branch name_of_the_second_branch
```
Or just merge the selected branch with another branch:  
```bash
git merge name_of_the_other_branch
```
(You can either set your commit message by adding `-m "your_message"`, or wait for the editor to open and type your commit message)  

22. Merging branches will move all commits of the branches to the checked branche where the merge will happen.  
23. When merging branches, some commits will get separated from each other and that will make comparing changes between commits hard.  
To compare a commit with its parent commit automatically:  
```bash
git show commit_id
```
24. Remove the commit where HEAD is attached to:  
```bash
git reset --hard HEAD~1
```
25. Remove a branch from the repository:  
```bash
git branch -d name_of_the_branch
```
26. If a branche is deleted then all commits within that branch will be discarded. Git garbage collector will get rid of them automatically (Git garbage collector run from time to time automatically).  

27. Collect garbage manually:  
```bash
git cg
```
28. Get log with a declared max of commits:  
```bash
git log -n max_commits_number
```
29. When merging two commits that contains changes to the same lines of code, then you'll have to decide which chages to keep in this conflict.
## ------------------------------Lesson 03------------------------------
1. Create a remote repository in Github in your account.
2. Copy the URL link to that remote repository.
3. Connect the remote repository to your local PC repository:  
```bash
git remote add any_name_for_the_remote the_URL_link_of_the_remote
```
example:  
```bash
git remote add tri_repo https://github.com/GaijinOtohp/trial.git
```
4. Get all remotes created with more detail:  
```bash
git remote -v
```
(`-v` stands for verbose)

5. Push data from local PC repository to the remote repository in Github:  
```bash
git push name_for_the_remote name_for_the_branch_to_push
```
example:  
```bash
git push tri_repo master
```
6. If asked for username and password, insert your Github username and password.  
   If annoyed of setting password each push then follow instruction in following link:
https://docs.github.com/en/get-started/getting-started-with-git/caching-your-github-credentials-in-git  

7. You can create and modify on files on Github directly. Other developers that are allowed to modify on your remote repository can also push and modify on files on your remote repository.  
(To do so just modify on the file and commit changes with a commit message)  

8. Pull data from the remote repository to the local reflections repository:  
```bash
git pull name_of_the_remote name_of_the_branch_to_pull
```
example:  
```bash
git pull tri_repo master
```
The branch that you want to pull must be the chekced one in your local repository (selected one). Otherwise, you will merge the selected branch with the pulled branch.  

9. Cloning a repository from a different developer will create a remote to that different developer named as `origin`.
10. The name of the branch that is cloned will be named as `name_of_the_remote/name_of_the_branch_pulled`.  
example: `origin/master`  

11. Get all branches, even cloned ones:  
```bash
git branch -a
```
12. Forking is the same as cloning but just on your Github account with more features (You can copy the repository directly into your account without downloading it into your own machine, Github keeps track of the number of people who've made forks on a repository, all forks refers back to the original, it makes it easier to suggest changes to the original repository).  

13. Give permission to other developers to edit on your Github repository: insert their Github names in collaborators list.  
14. Update cloned local branches alone `origin/master`:  
```bash
git fetch name_of_the_remote
```
example:  
```bash
git fetch origin
```
15. Ask the original repository owner to merge a branch of your creation to his repository: create a pull request from the new branch.  
The base repository by default is the original repository (the merge pull request is for the original repository)  

16. You can also merge the branches in your own fork: click edit on the page where the pull request is opened, and change the base fork to your own repository.  

17. Editing and pushing the branch of the pull request will also change the file in the pull request.  

18. Merging a commit that is ancestor to the other commit will make a `Fast-Forward Merge` (takes the label of the ancestor commit and moves it to the newer commit without creating a new commit of the merge).

19. Fast-Forward Merge doesn't work when merging in Github.

20. If a merge of a pull request has a conflict with changes of other pull requests, then you'll have to fix that conflict in your own machine by pulling the remote master into local master (which will also update `origin/master`), fixing the conflict, merging local master into the branch of the pull request, then pushing that branch of the pull request.
## --------------------------Additional notes---------------------------
1. Get remote repositories commits:  
```bash
git remote update
```
2. Show commits of all branches (local and remote repositories) each in one line:  
```bash
git log --all --oneline --graph --decorate
```
3. Copy a commit from a branch to the current branch:  
```bash
git cherry-pick commit_id
```