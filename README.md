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
git diff "file path" // Shows file differences not yet staged.
git diff "commit id" "commit id" // show two commit differences.
git diff --staged  //Shows file differences between staging and the last file version.
```

Unstages the file, but preserve its contents. more [info](https://www.atlassian.com/git/tutorials/undoing-changes/git-reset/). 


```bash
git reset HEAD [file]
git reset --soft [commit id] //The Staging Index and the Working Directory are left untouched.
git reset --mixed [commit id] //The Staging Index is reset to the state of the specified commit.
git reset --hard [commit id] //DANGEROUS, pending work that was hanging out in the Staging Index and Working Directory will be lost.
git reset --hard HEAD~2 //moves the current branch backward by two commits NOTE: used on unpublished commits.
```

Snapshots the file in preparation for versioning.

```bash
git add [file]
git add . //This command adds one or more to the staging area.
git add -A // file rename using linux command "mv"
git add -u // file rename using UI
```
