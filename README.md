# GIT COMMANDS

Useful git commands for everyday use!

## INSTALLATION
Use this command [line](https://www.linode.com/docs/development/version-control/how-to-install-git-on-linux-mac-and-windows/) to install **git**.

## Configuring GIT

This command sets the author name and email address respectively to be used with your all local repositories.

```bash
git config –global user.name "johir-rayhan"
git config –global user.email "johir.rayhan01@gmail.com"
```
To turn on code highlighting.

```bash
git config --global color.ui true
```
By default, Git uses whatever you’ve set as your default text editor via one of the shell environment variables.

```bash
git config --global core.editor code
```
Now, no matter what is set as your default shell editor, Git will fire up VScode to edit messages. To see the result==>
```bash
git config --global -e
```
Let you view your Git configurations.

```bash
git config --list
```
## CREATE REPOSITORIES

Creates a new local repository with the specified name

```bash
 git init [project-name]
```

Downloads a project and its entire version history.

```bash
 git clone [url]
```


## MAKE CHANGES
Review edits and craf a commit transaction.

Lists all new or modified files to be commited.


```bash
git status
```

Shows files differences not yet staged.


```bash
git diff 
git diff "file path" #Shows file differences not yet staged.
git diff "commit id" "commit id" #show two commit differences.
git diff [first-branch]...[second-branch] #Shows content differences between two branches
git diff --staged  #Shows file differences between staging and the last file version.
```

Unstages the file, but preserve its contents. more [info](https://www.atlassian.com/git/tutorials/undoing-changes/git-reset/). 


```bash
git reset HEAD [file]
git reset --soft [commit id] #The Staging Index and the Working Directory are left untouched.
git reset --mixed [commit id] #The Staging Index is reset to the state of the specified commit.
git reset --hard [commit id] #DANGEROUS, pending work that was hanging out in the Staging Index and Working Directory will be lost.
git reset --hard HEAD~2 #moves the current branch backward by two commits NOTE: used on unpublished commits.
```

Snapshots the file in preparation for versioning.

```bash
git add [file]
git add . # This command adds one or more to the staging area.
git add -A # file rename using linux command "mv"
git add -u # file rename using UI
```
## REFACTOR FILENAMES

Relocate and remove versioned files.


```bash
git mv [file-original] [file-renamed] #Changes the file name and prepares it for commit.

git rm [file] #Deletes the file from the working directory and stages the deletion.
git rm --cached [file] #Removes the file from version control but preserves the file locally.

NOTE: bash command [mv] then use [git add -A] 
OR UI rename a file -> use [git add [file]] and [git add -u] 

NOTE: git rm [file]; 
git reset HEAD [file], git checkout -- [file] #reverse the file from your working directory.
```
## REVIEW HISTORY

Browse and inspect the evolution of project files.


```bash
git log #Lists version history for the current branch.
git log --follow [file] #Lists version history for a file, including renames
git log --abbrev-commit # commit id has been short.
git log [commit id]...[commit id] # show details between those commit.
git log --since="3 days ago" #same as **git log [commit id]...[commit id]**

git log --oneline --graph --decorate

git diff [first-branch]...[second-branch] #Shows content differences between two branches.

git show [commit id] #Outputs metadata and content changes of the specified commit

NOTE: git help log for details.
```
## GIT [ALIAS](https://www.atlassian.com/git/tutorials/git-alias)

Aliases are created through the use of the git config command and the Git configuration files.


```bash
git hist # Should be [git: 'hist' is not a git command.]
git config --global alias.hist ["log --all --graph --decorate --oneline"]
```

## SUPPRESS TRACKING

Exclude temporary files and paths.

A text file named **.gitignore** suppresses accidental versioning of
files and paths matching the specified paterns

```bash
*.log
build/
temp-*
*.DS_Store
git ls-files --other --ignored --exclude-standard #Lists all ignored files in this project
```
## GROUP CHANGES

Name a series of commits and combine completed efforts

```bash
git branch #Lists all local branches in the current repository
git branch -a # Active branch.And all remote branches.
git branch [branch_name] #Creates a new branch
git checkout [branch-name] #Switches to the specified branch and updates the working directory.
git checkout -b [branch-name] # creates and switches to the branch.

git branch -m [old-name] [new-name] # rename the branch name.
git branch -d [branch-name] # Deletes the specified branch.
```
Combines the specified branch’s history into the current branch.

```bash
git merge [branch] 
git merge [branch] --no--ff #Create a merge commit even when the merge resolves as a fast-forward.
git merge [branch] -m [commit message]. #Set the commit message (in case one is created).
```
