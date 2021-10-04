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

PATTERN | EXAMPLE | DESCRIPTION
------------ | ------------- | -------------
**/logs | logs/debug.log <br /> logs/monday/foo.bar <br /> build/logs/debug.log | You can prepend a pattern with a double asterisk to match directories anywhere in the repository.
**/logs/debug.log	| logs/debug.log <br /> build/logs/debug.log <br /> but not <br /> logs/build/debug.log	| You can also use a double asterisk to match files based on their name and the name of their parent directory.
*.log	| debug.log <br /> foo.log <br /> .log <br /> logs/debug.log | An asterisk is a wildcard that matches zero or more characters.
*.log <br /> !important.log	| debug.log <br /> trace.log <br /> but not <br /> important.log <br /> logs/important.log	| Prepending an exclamation mark to a pattern negates it. If a file matches a pattern, but also matches a negating pattern defined later in the file, it will not be ignored.
*.log <br /> !important/*.log	| trace.*	debug.log <br /> important/trace.log <br /> but not <br /> important/debug.log	| Patterns defined after a negating pattern will re-ignore any previously negated files.
/debug.log | debug.log <br /> but not <br /> logs/debug.log	| Prepending a slash matches files only in the repository root.
debug.log	 | debug.log <br /> logs/debug.log |	By default, patterns match files in any directory
debug?.log	| debug0.log <br /> debugg.log <br /> but not <br /> debug10.log |	A question mark matches exactly one character.
debug[0-9].log |	debug0.log <br /> debug1.log <br /> but not debug10.log |	Square brackets can also be used to match a single character from a specified range.
debug[01].log |	debug0.log <br /> debug1.log <br /> but not <br /> debug2.log <br /> debug01.log |	Square brackets match a single character form the specified set.
debug[!01].log	| debug2.log <br /> but not <br /> debug0.log <br /> debug1.log <br /> debug01.log |	An exclamation mark can be used to match any character except one from the specified set.
debug[a-z].log |	debuga.log <br /> debugb.log <br /> but not <br /> debug1.log |	Ranges can be numeric or alphabetic.
logs |	logs <br /> logs/debug.log <br /> logs/latest/foo.bar <br /> build/logs <br /> build/logs/debug.log |	If you don't append a slash, the pattern will match both files and the contents of directories with that name. In the example matches on the left, both directories and files named logs are ignored
logs/ |	logs/debug.log <br /> logs/latest/foo.bar <br /> build/logs/foo.bar <br /> build/logs/latest/debug.log |	Appending a slash indicates the pattern is a directory. The entire contents of any directory in the repository matching that name – including all of its files and subdirectories – will be ignored
logs/ <br /> !logs/important.log |	logs/debug.log <br /> logs/important.log |	Wait a minute! Shouldn't logs/important.log be negated in the example on the left <br /><br /> Nope! Due to a performance-related quirk in Git, you can not negate a file that is ignored due to a pattern matching a directory
logs/**/debug.log |	logs/debug.log <br /> logs/monday/debug.log <br /> logs/monday/pm/debug.log |	A double asterisk matches zero or more directories.
logs/*day/debug.log |	logs/monday/debug.log <br /> logs/tuesday/debug.log <br /> but not <br /> logs/latest/debug.log |	Wildcards can be used in directory names as well.
logs/debug.log |	logs/debug.log <br /> but not <br /> debug.log <br /> build/logs/debug.log |	Patterns specifying a file in a particular directory are relative to the repository root. (You can prepend a slash if you like, but it doesn't do anything special.)

In addition to these characters, you can use # to include comments in your .gitignore file:
```git
# ignore all logs
*.log
```

You can use \ to escape .gitignore pattern characters if you have files or directories containing them:
```git
# ignore the file literally named foo[01].txt
foo\[01\].txt
```

Git ignore rules are usually defined in a .gitignore file at the root of your repository. However, you can choose to define multiple .gitignore files in different directories in your repository. Each pattern in a particular .gitignore file is tested relative to the directory containing that file. However the convention, and simplest approach, is to define a single .gitignore file in the root. As your .gitignore file is checked in, it is versioned like any other file in your repository and shared with your teammates when you push. Typically you should only include patterns in .gitignore that will benefit other users of the repository.


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
```
Transform the current directory into a Git repository. This adds a .git subdirectory to the current directory and makes it possible to start recording revisions of the project.

OR

```git
git clone [repository name] [directory path]
```
Create a local copy of a remote repository (from an existing URL)
```git
git clone ssh://git@github.com/[username]/[repository-name].git
```
At a high level, they can both be used to "initialize a new git repository." However, git clone is dependent on git init. git clone is used to create a copy of an existing repository. Internally, git clone first calls git init to create a new repository. It then copies the data from the existing repository, and checks out a new set of working files.

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
<code>git config --global merge.tool [toolname like kdiff3] |

<code>git config --global core.editor \
"'C:/Program Files (x86)/Notepad++/notepad++.exe' -multiInst -notabbar -nosession -noPlugin"</code>

git config levels and files
Before we further discuss git config usage, let's take a moment to cover configuration levels. The git config command can accept arguments to specify which configuration level to operate on. The following configuration levels are available:

--local
By default, git config will write to a local level if no configuration option is passed. Local level configuration is applied to the context repository git config gets invoked in. Local configuration values are stored in a file that can be found in the repo's .git directory: .git/config
 

 --global
Global level configuration is user-specific, meaning it is applied to an operating system user. Global configuration values are stored in a file that is located in a user's home directory. ~ /.gitconfig on unix systems and C:\Users\\.gitconfig on windows
 

 --system
System-level configuration is applied across an entire machine. This covers all users on an operating system and all repos. The system level configuration file lives in a gitconfig file off the system root path. $(prefix)/etc/gitconfig on unix systems. On windows this file can be found at C:\Documents and Settings\All Users\Application Data\Git\config on Windows XP, and in C:\ProgramData\Git\config on Windows Vista and newer.

Thus the order of priority for configuration levels is: local, global, system. This means when looking for a configuration value, Git will start at the local level and bubble up to the system level.

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
<code>git clean -n git clean -f</code> | Forcefully remove untracked files
<code>git clean -n git clean -f -d</code> | Forcefully remove untracked directory


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
<code>git log --pretty=format:"%h%x09%an%x09%ad%x09%s"</code> | log result with date
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
  

## SQUASH YOUR COMMITS
To "squash" in Git means to combine multiple commits into one.
COMMAND | DESCRIPTION
------------ | -------------
<code>git rebase -i HEAD~[n]</code> | merge n commits into 1
At this point your editor of choice will pop up, showing the list of commits you want to merge.
Note that it might be confusing at first, since they are displayed in a reverse order, where the older commit is on top.
You mark a commit as squashable by changing the word pick into squash next to it (or s for brevity, as stated in the comments).
<code>pick d94e78 Prepare the workbench for feature Z     --- older commit</code>
<code>s 4e9baa Cool implementation </code>
<code>s afb581 Fix this and that  </code>
<code>s 643d0e Code cleanup</code>
<code>s 87871a I'm ready! </code>
<code>s 0c3317 Whoops, not yet... </code>
<code>s 871adf OK, feature Z is fully implemented      --- newer commit</code>
Save the file and close the editor.
  
## GIT REVERT
https://www.atlassian.com/git/tutorials/undoing-changes/git-revert
 
 
## Setup GIT GUI 
Install On Centos <code>sudo yum install git-gui</code>

Install On Ubuntu <code>sudo apt-get install git-gui</code>
  
RUN <code>git gui</code>
  
RUN <code>gitk --all</code>
