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
