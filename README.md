# Git Commands

A list of my commonly used Git commands.

## Installation

1. Create an account on GitHub
2. Create a new repository for your project
3. Start a project and give it a name
4. Grab the HTTPS link to this new repository	
```git
https://github.com/YourUsername/some-small-app.git
```
5. Bind this remote repository to your local repository 
via HTTPS 
```git
git remote add origin https://github.com/YourUsername/some-small-app.git
```
push tells Git to push your files to a remote repository
```git
git push -u origin master
```	
"-u", we can run only "git push" next time!".

"git push" is that you have to enter your credentials each time you push code to GitHub.
6. Bind this remote repository to your local repository via SSH
```git
git remote add origin git@github.com:YourUsername/your-app.git
```
work with SSH, then you won't have to enter GitHub credentials every time you push code to GitHub [help connecting to github with ssh](https://help.github.com/articles/connecting-to-github-with-ssh/)

7. View the list of repositories
```git
git remote -v
```
8. Ignore files with [.gitignore](https://help.github.com/articles/ignoring-files/)
```git
.gitignore
```


## CONFIG (Location of config file ~/.gitconfig)
Configure the author name to be used with your commits.
```git
git config –global user.name "[name]"
```
Configure the email address to be used with your commits.
```git
git config –global user.email "[email address]"
```

## GIT STARTING A REPO
Initialize a local Git repository
```git
git init [repository name]
git clone [repository name] [directory path]
```
Create a local copy of a remote repository (from an existing URL)
```git
git clone ssh://git@github.com/[username]/[repository-name].git
```
```git
git pull
```

## CONFIG
COMMAND | DESCRIPTION
------------ | -------------
<code>git config –global user.name "[name]"</code> | Configure the author name to be used with your commits.
<code>git config –global user.email "[email address]"</code> | Configure the email address to be used with your commits.
<code>git config --system core.editor "[editor]"</code> | 
<code>git config --global alias. [alias-name] [git-command]</code> |
<code>git config --global color.ui auto</code> |

<code>git config --global core.editor \
"'C:/Program Files (x86)/Notepad++/notepad++.exe' -multiInst -notabbar -nosession -noPlugin"</code>


## GIT STARTING A REPO/ CLONING
COMMAND | DESCRIPTION
------------ | -------------
<code>git init  [repository name]</code> | Initialize a local Git repository
<code>git clone ssh://git@github.com/[username]/[repository-name].git </code> | Create a local copy of a remote repository (from an existing URL via SSH)
<code>git clone https://github.com/[username]/[repository-name].git</code> | Create a local copy of a remote repository (from an existing URL via HTTPS)
<code>git clone https://github.com/[username]/[repository-name].git ~/dir/folder</code> | Create a local copy of a remote repository to a folder (from an existing URL via HTTPS)
<code>git clone -b branchname https://github.com/[username]/[repository-name].git</code> | Clone specific branch to localhost
<code>git pull</code> | Update local repository to the newest commit
<code>git status</code> | Check status


## ADDING/ DELETING
COMMAND | DESCRIPTION
------------ | -------------
<code>git add filename(s)</code> | Add a file to the staging area
<code>git add .</code> | Add several files to the staging area in one go (only add files located in the root directory)
<code>git add --all</code> | Add several files to the staging area in one go (add files located in the root directory and other directories)
<code>git add -A</code> | Add all new and changed files to the staging area (Same as Above)
<code>git add -f .<code> | Add all new, changed and ignored files to the staging area
<code>git add *</code> | Adds one or more to the staging area.
<code>git add Folder/\*.txt</code> | Adds content from all *.txt files under given directory and its subdirectories
<code>git rm --cached my-file.ts</code> | deletes the file from your working directory and stages the deletion
<code>git reset another-file.js</code> | unstages the file but it preserves the file contents.
<code>git push origin :branchname</code> | Delete remote branch (push nothing)
<code>git push origin --delete branchname</code> | Delete remote branch (push nothing)
<code>git clean -n git clean -f</code | Forcefully remove untracked files
<code>git clean -n git clean -f -d</code | Forcefully remove untracked directory


## COMMITTING
COMMAND | DESCRIPTION
------------ | -------------
<code>git commit -m "message"</code> | commit changes
<code>git commit -a -m "Do something once more"</code> | add modified files to the staging area and commit them at the same time
<code>git reset --soft HEAD^</code>	|		undo the commit (resetting the HEAD)
<code>git commit --amend -m "Add the remaining file"</code> | rectify commit with new message. Just add the remaining file to the staging area and then commit


## BRANCHING (Create branches/ Switch branches or Restore working tree files)

COMMAND | DESCRIPTION
------------ | -------------
<code>git branch</code> | see our current branches
<code>git branch -a</code> | list all branches (remote and local)
<code>git branch -r</code> | list all remote branches 
<code>git branch new_branch</code> | create a new branch
<code>git branch -f new_branch</code> | create a new branch (if it already exists, then reset it)
<code>git branch -m new_branch_name</code> | rename a branch
<code>git branch -m [old-branch-name] [new-branch-name]</code> | rename a branch
<code>git branch -d new_branch</code> | delete a local branch 
<code>git push origin --delete [branch name]</code> | delete a remote branch
<code>git push origin :[branch name]</code> | delete a remote branch
<code>git checkout new_branch</code> | switch branch
<code>git checkout -b new_branch</code> | create a new branch and switch to it
<code>git checkout -B new_branch</code> | create a new branch (if it already exists, then reset it) and switch to it
<code>git checkout -b [branch name] origin/[branch name]</code> | clone a remote branch and switch to it
<code>git checkout -f new_branch</code> | switching branches, proceed even if the index or the working tree differs from HEAD. This is used to throw away local changes.
<code>git checkout -</code>  | switch to the branch last checked out
<code>git checkout -- [file-name.txt]</code> | discard changes to a file
<code>git checkout e3b43d63</code> | get back to a previously committed state
<code>git reset --hard HEAD^ path/filename</code> | abort your changes to a file

```git
-m, --merge
```
When switching branches, if you have local modifications to one or
more files that are different between the current branch and the
branch to which you are switching, the command refuses to switch
branches in order to preserve your modifications in context.
However, with this option, a three-way merge between the current
branch, your working tree contents, and the new branch is done, and
you will be on the new branch.

When a merge conflict happens, the index entries for conflicting
paths are left unmerged, and you need to resolve the conflicts and
mark the resolved paths with git add (or git rm if the merge should
result in deletion of the path).

When checking out paths from the index, this option lets you
recreate the conflicted merge in the specified paths.

```git
--conflict=<style>
```
The same as --merge option above, but changes the way the
conflicting hunks are presented, overriding the merge.conflictStyle
configuration variable. Possible values are "merge" (default) and
"diff3" (in addition to what is shown by "merge" style, shows the
original contents).

## MERGING
first switch back to the main branch by git checkout master_branch

COMMAND | DESCRIPTION
------------ | -------------
<code>git merge new_branch</code> | merge a branch into the active branch
<code>git merge [source branch] [target branch]</code> | merge a branch into a target branch

## STASHING

COMMAND | DESCRIPTION
------------ | -------------
<code>git stash</code> | command temporarily stores all the modified tracked files.
<code>git stash -u</code> | command temporarily stores all the modified tracked and untracked files.
<code>git stash -a</code> | command temporarily stores all the modified tracked, untracked and ignored files.
<code>git stash save "message"</code> | command temporarily stores all the modified tracked files with custom message.
<code>git stash list</code> | lists all stashed changesets
<code>git stash pop</code> | restores the most recently stashed files and delete stash from list
<code>git stash pop "stash@{1}"</code> | restores the stashed files for the given stash id and delete stash from list
<code>git stash drop</code> | discards the most recently stashed changeset.
<code>git stash drop "stash@{1}"</code> | discards the stashed files for the given stash id
<code>git stash apply</code> | restore the most recently stashed files
<code>git stash clear</code> | remove all stashed entries

## SHARING AND UPDATING

COMMAND | DESCRIPTION
------------ | -------------
<code>git push origin [branch name]</code> | Push a branch to your remote repository
<code>git push -u origin [branch name]</code> | Push changes to remote repository (and remember the branch)
<code>git push</code> | Push changes to remote repository (remembered branch)
<code>git pull</code> | Update local repository to the newest commit
<code>git pull origin [branch name]</code> | Pull changes from remote repository
<code>git remote add origin ssh://git@github.com/[username]/[repository-name].git </code> | Add a remote repository
<code>git remote set-url origin ssh://git@github.com/[username]/[repository-name].git </code> | Set a repository's origin branch to SSH

## DIFFRENCE IN FILES

COMMAND | DESCRIPTION
------------ | -------------
<code>git diff</code> | shows the file differences which are not yet staged
<code>git diff --color-words index.html</code> | Compare modified files and highlight changes only
<code>git diff –staged</code> | shows the differences between the files in the staging area and the latest version present
<code>git diff [branch1] [branch2]</code> | shows the differences between the two branches mentioned
<code>git diff 6eb715d</code> | compare commits
<code>git diff 6eb715d index.html</code> | compare commits of a file
<code>git diff 6eb715d 7eds15d index.html</code> | compare commits of a file

## LOGGING

COMMAND | DESCRIPTION
------------ | -------------
<code>git log</code> | list the version history for the current branch
<code>git log --oneline</code> | show oneline-summary of commits
<code>git log --format=oneline</code> | show oneline-summary of commits with full SHA-1
<code>git log --oneline -3</code> | show oneline-summary of the last three commits
<code>git log --author="Sven"</code> | show only custom commits
<code>git log --grep="Message"</code> | show only custom commits
<code>git log --until=2013-01-01</code> | show only custom commits
<code>git log --since=2013-01-01</code> | show only custom commits
<code>git log -p</code> | show changes
<code>git log 6eb715d.. index.html</code> | show every commit since special commit for custom file only
<code>git log -p 6eb715d.. index.html</code> | Show changes of every commit since special commit for custom file only
<code>git log --stat --summary</code> | Show stats and summary of commits
<code>git log –follow[file]</code> | lists version history for a file, including the renaming of files also.
<code>git log --graph</code> | Show history of commits as graph
<code>git log --oneline --graph --all --decorate</code> | Show history of commits as graph-summary
<code>git show [commit]</code> | shows the metadata and content changes of the specified commit.
<code>git reflog</code>

## MISC

COMMAND | DESCRIPTION
------------ | -------------
<code>git --version</code> | Prints the Git suite version that the git program came from.
<code>git --help</code> | Prints the synopsis and a list of the most commonly used commands.
<code>git --help -a</code> | Prints all git commands
<code>git --help -all</code> | Prints all git commands
<code>git check-ignore *</code> | List ignored files
<code>git status --ignored</code> | Status of ignored files


## GIT GOOD MORNING COMMANDS
COMMAND | DESCRIPTION
------------ | -------------
<code>git checkout [master_branch]</code> |
<code>git remote prune origin</code> | The git remote prune command only deletes the remote tracking branches in the remotes/origin namespace. Not the local branches.
<code>git fetch origin</code> | Downloads all history from the remote tracking branches
<code>git pull</code> | Updates your current local working branch with all new commits from the corresponding remote branch on GitHub
<code>git checkout [child_branch]</code> |
<code>git pull</code> |
<code>git rebase [master_branch]</code> | To place feature branch of top of [Master Branch]
<code>gitk --all</code> |
<code>git rebase --abort</code> |
<code>git rebase --continue</code> |

## DELETE ALL LOCAL BRANCHES
<code>git branch | grep -v "[MASTER_BRANCH]" | xargs git branch -D</code>

## Setup GIT GUI 
Install On Centos <code>sudo yum install git-gui</code>

Install On Ubuntu <code>sudo apt-get install git-gui</code>
  
RUN <code>git gui</code>
  
RUN <code>gitk --all</code>
