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
8. Ignore files with 
```git
.gitignore
```


## CONFIG
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
git config –global user.name "[name]" | Configure the author name to be used with your commits.
git config –global user.email "[email address]" | Configure the email address to be used with your commits.

## GIT STARTING A REPO
COMMAND | DESCRIPTION
------------ | -------------
git init  [repository name] | Initialize a local Git repository
git clone ssh://git@github.com/[username]/[repository-name].git | Create a local copy of a remote repository (from an existing URL)
git pull | Update local repository to the newest commit
git status | Check status


## ADDING/ DELETING
COMMAND | DESCRIPTION
------------ | -------------
git add filename(s) | Add a file to the staging area
git add . | Add several files to the staging area in one go (only add files located in the root directory)
git add --all | Add several files to the staging area in one go (add files located in the root directory and other directories)
git add -A | Add all new and changed files to the staging area (Same as Above)
git add * | Adds one or more to the staging area.
git add Folder/\*.txt | Adds content from all *.txt files under given directory and its subdirectories
git rm --cached my-file.ts | deletes the file from your working directory and stages the deletion
git reset another-file.js | unstages the file but it preserves the file contents.


## COMMITTING
COMMAND | DESCRIPTION
------------ | -------------
git commit -m "message" | commit changes
git commit -a -m "Do something once more" | add modified files to the staging area and commit them at the same time
git reset --soft HEAD^	|		undo the commit (resetting the HEAD)
git commit --amend -m "Add the remaining file" | rectify commit with new message. Just add the remaining file to the staging area and then commit


## BRANCHING (Create branches/ Switch branches or Restore working tree files)

COMMAND | DESCRIPTION
------------ | -------------
git branch | see our current branches
git branch -a | list all branches (remote and local)
git branch new_branch | create a new branch
git branch -f new_branch | create a new branch (if it already exists, then reset it)
git branch -d new_branch | delete branch
git checkout new_branch | switch branch
git checkout -b new_branch | create a new branch and switch to it
git checkout -B new_branch | create a new branch (if it already exists, then reset it) and switch to it
git checkout -b [branch name] origin/[branch name] | clone a remote branch and switch to it
git checkout -f new_branch | switching branches, proceed even if the index or the working tree differs from HEAD. This is used to throw away local changes.
git checkout -  | switch to the branch last checked out
git checkout -- [file-name.txt] | discard changes to a file
git checkout e3b43d63 | get back to a previously committed state
git reset --hard HEAD^ path/filename | abort your changes to a file

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
git merge new_branch | merge a branch into the active branch
git merge [source branch] [target branch] | merge a branch into a target branch

## STASHING
COMMAND | DESCRIPTION
------------ | -------------
git stash | command temporarily stores all the modified tracked files.
git stash save "message" | command temporarily stores all the modified tracked files with custom message.
git stash list | lists all stashed changesets
git stash pop | restores the most recently stashed files.
git stash pop "stash@{1}" | restores the stashed files for the given stash id
git stash drop | discards the most recently stashed changeset.
git stash drop "stash@{1}" | discards the stashed files for the given stash id
git stash apply | restore the most recently stashed files and delete stash from list
git stash clear | remove all stashed entries

## SHARING AND UPDATING
COMMAND | DESCRIPTION
------------ | -------------
git push origin [branch name] | Push a branch to your remote repository
git push -u origin [branch name] | Push changes to remote repository (and remember the branch)
git push | Push changes to remote repository (remembered branch)
git push origin --delete [branch name] | Delete a remote branch
git pull | Update local repository to the newest commit
git pull origin [branch name] | Pull changes from remote repository
git remote add origin ssh://git@github.com/[username]/[repository-name].git | Add a remote repository
git remote set-url origin ssh://git@github.com/[username]/[repository-name].git | Set a repository's origin branch to SSH

## DIFFRENCE IN FILES
COMMAND | DESCRIPTION
------------ | -------------
git diff | shows the file differences which are not yet staged
git diff –staged | shows the differences between the files in the staging area and the latest version present
git diff [branch1] [branch2] | shows the differences between the two branches mentioned

## LOGGING
COMMAND | DESCRIPTION
------------ | -------------
git log | list the version history for the current branch
git log –follow[file] | lists version history for a file, including the renaming of files also.
git show [commit] | shows the metadata and content changes of the specified commit.

## MISC
COMMAND | DESCRIPTION
------------ | -------------
git --version | Prints the Git suite version that the git program came from.
git --help | Prints the synopsis and a list of the most commonly used commands.
git --help -a | Prints all git commands
git --help -all | Prints all git commands
