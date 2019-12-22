# GIT COMMANDS

Useful git commands for everyday use!

## INSTALLATION
Use this command [line](https://www.linode.com/docs/development/version-control/how-to-install-git-on-linux-mac-and-windows/) to install **git**.

## Configuring GIT

This command sets the author name and email address respectively to be used with your all local repositories.

```bash
git config –global user.name "johir-rayhan"
git config –global user.email "johir.rayhan01@gmail.com"

git config user.name "johir-rayhan" # only one local repository
git config user.email "johir.rayhan01@gmail.com" # See the result cat .git/config find [user] key
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
git diff --name-only # The list of changed files.
git diff --name-only --diff-filter=U #the simplest way to list conflicted files
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
git log --reverse # To go the first commit of the repo


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
## Rewriting history

Git uses a few different methods to record changes. 

```bash
git commit -m "commit-message" --author="Johir Rayhan <johir.rayhan01@gmail.com>"
git commit --amend #command is a convenient way to modify the most recent commit.
git commit --amend --author="Johir Rayhan <johir.rayhan01@gmail.com>" # Changed the commited author.
# Reset All commit author
  git filter-branch --commit-filter '
      if [ "$GIT_AUTHOR_NAME" = "OLD-NAME" ];
         then
                GIT_AUTHOR_NAME="Johir Rayhan";
                GIT_AUTHOR_EMAIL="johir.rayhan01@gmail.com";
                git commit-tree "$@";
     else
                git commit-tree "$@";
    fi' HEAD

```
Rebase is one of two Git utilities that specializes in integrating changes from one branch onto another. The other change integration utility is git merge. Merge is always a forward moving change record. Alternatively, rebase has powerful history rewriting features. [Merging vs Rebasing](https://www.atlassian.com/git/tutorials/merging-vs-rebasing)

```bash
git rebase [branch-name] # First, rewinding head to replay your work on top of it...
git rebase --interactive [BASE] # It's like Git commit --amend on steroids.
#(BASE an ID, a branch name, a tag, or a relative reference to HEAD).

git rebase --continue/--abort 
#The --continue and --abort command line arguments can be passed to git rebase 
#to advance or reset the the rebase when dealing with conflicts.
```
## SAVE FRAGMENTS

git [stash](https://www.atlassian.com/git/tutorials/saving-changes/git-stash) temporarily shelves. 

This command temporarily stores all the modified tracked files.

```bash
git stash save "message" #it's good practice to annotate your stashes with a description.
git stash -u # stash your untracked files
git stash list # 
```
This is useful if you want to apply the same stashed changes to multiple branches.

```bash
git stash apply #
git stash apply stash@{2} # a particular stash.
```

Cleaning up your stash

```bash
git stash drop # first stash
git stash drop stash@{1} # a particular stash
git stash clear #delete all of your stashes
```

Apply and drop a stash in one command.

```bash
git stash pop #the most recently created stash.
git stash pop stash@{2} # A particular stash.
```

### Viewing stash diffs

You can view a summary of a stash with:

```bash
git stash show
git stash show -p #To view the full diff on first stash
git stash show -p stash@{1} #To view the full diff of a stash 1
```

Creating a branch from your stash

```bash
git stash branch [branch-name] stash@{1}
```
## Git Tagging

Tagging is generally used to capture a point in history that is used for a marked version release (i.e. v1.0.1).

```bash
git tag <tagname> #Light weight Tags
git tag -a <tagname> #Annotated tags are stored as full objects 
# {the tagger name, email, and date. Similar to commits and commit messages}
git tag --list 
git tag --delete <tagname>
git tag <tagname> -m [message]
git tag -a <tagname> <commit id>
git tag -a <tagname> -f <commit id>

git diff <tagname> <tagname>

git push origin <tagname>
git push origin master --tags
git push origin :v-0.8-alpha # delete remote tag

git checkout <tagname> #command will checkout the ... tag
```
## GIT syncing
git remote/ git fetch/ git push/ git pull

###TODO
Apply PUSH.

```bash
git push origin branch-name #the .
git push --all # .
```
Apply PULL.

```bash
git pull origin branch-name #the .
git pull origin branch-name --allow-unrelated-histories # refusing to merge unrelated histories(--allow-unrelated-histories).
```
