# Using Git

## Version Control
Version Control is a system that records changes and allows programmers to revisit various versions of a file or set of files. Through version control, one can revert a file or project to a previous version, track modifications and modifying individuals, and compare changes. By utilizing a Version Control System (VCS), mistakes with files can easily be rectified.

## Local Version Control
Local Version control procedures were done using hard disk centralizing updates with only one person reviewing all changes before the push.

## Centralized Version Control
The need for collaboration within a developer team on a single file or set of files led to the advent of the Centralized Version Control System (CVCS). This allowed teams of developers to work with one another in tandem on a project. This way one central operations manager would review all the changes before pushing code out. This is a common way how businesses operate at the moment at one centralized server.

## Distributed Version Control
A Distributed Version Control systems (DVCS) addresses the major vulnerability of the CVS: the server as a single point of failure. Just like how mesh networks found in offices and homes to address and improve overall connectivity is implemented. Such is done in a distriuted network of version control is done. One example of that is how bitcoin mining used on a decentralized network for any real signicant change to be made on the network protocols 51% of all miners need to be update to the newer version creating a fork in the mining program with a different set of rules.

To prevent this type of catastrophic loss, a DVCS allows clients to create mirrored repositories. These data backups can be easily be placed on the server to replace any lost information. Such as keeping the blockchain records up to date.


## Local Operations

Git mostly relies on local operations because most necessary information can be found in local resources. This allows for process expediency because a project’s history resides on the local disk, eliminating the need to fetch history information from the server, and allowing one to continue work on a project even when not online or on a VPN.

## Tracking Changes
Every single change applied to any file or directory is tracked by Git. And, as the gatekeeper, Git will always detect file corruption or loss of information in transit.

## Loss of Data
Git is set up to greatly minimize the possibility of irreversible damage to files, such as accidentally lost data. Git makes it extremely difficult for a snapshot of your file that is committed to be lost.


Definition | Syntax
---------- | --------------------------------------------------------------------------
States     | Files in Git can reside in three main states: committed, modified and staged.
Committed  | Data is securely stored in a local database
Modified   | File has been changed but not committed to the database


## Seeing Your Remotes
By running the git remote command, you can view the short names, such as “origin,” of all specified remote handles.

By using git remote -v, you can view all the remote URLs next to their corresponding short names.

### Inputs
$ cd example

$ git remote -v

### Outputs
remote1 https://github.com/remote1/example (fetch)

remote1 https://github.com/remote1/example (push)

remote2 https://github.com/remote2/example (fetch)

remote2 https://github.com/remote2/example (push)

remote3 https://github.com/remote3/example (fetch)

remote3 https://github.com/remote3/example (push)

# Adding Remotes
To create a new remote Git repository with a short name, use the following format:

git remote add shortname url
Example:

### Inputs
$ git remote

origin

$ git remote add js https://github.com/janesmith/project1

$ git remote -v

origin https://github.com/johndoe/project1 (fetch)

origin https://github.com/johndoe/project1 (push)

js     https://github.com/janesmith/project1 (fetch)

js     https://github.com/janesmith/project1 (push)
This addition of these remote and short names allows you to use shortnames for Git collaboration.

### Fetching
Fetching entails pulling data that you don’t have from a remote project.

Here is the command format:

git fetch [remote-name]
*Now, you should also possess the references to all branches for that remote (more on branching later).

### Cloned Repositories

For cloned repositories, use the command git fetch origin to pull down any new changes that were pushed to the server since you cloned or last fetched from it.

Note: git fetch solely pulls new data to a local repository; it does not merge changes with or modify your local work. We will discuss merging in a later section. Later, we will also discuss git pull , which allows for fetching and automatic merging.

### Pushing
To push your changes “upstream” for sharing, you would use the following git push command format:

git push [remote-name][branch-name]
Example:

$ git push origin master
*This command pushes committed changes from your local “master” branch upstream to the “origin” server.

Note: You can only successfully push changes upstream if you have write access for the server from which you cloned, and if someone else has not pushed changes upstream that you haven’t pulled yet. If a collaborator pushed changes upstream after you had cloned, your push will not be successful. You will have to pull new changes and merge them with your branch before you can successfully push your changes upstream.

### Renaming/Removing Remotes
Rename

To rename a remote’s short name, use the git remote rename command.

Example:

$ git remote rename js jane

$ git remote

origin

jane
*In the example above, we can see that the remote’s short name has been changed from js to Jane. The command git remote lists our existing remotes, which jane is now one of. The rename action also alters names of remote branches: js/master would change to jane/master.

### Remove

To remove a remote for whatever reason (e.g., a contributor has left the team, the server has moved), simply use the git remote rm command:

Example:

$ git remote rm jane

$ git remote

origin
NOTE: Reminder: “origin” is simply the default remote name when you use the git clone command.
 
### Undoing Actions
Git has mechanisms for undoing certain actions.

### Commit Mistakes
You can use the –amend command when you need to alter a commit message or forgot to add some files.

$ git commit --amend
In the example above, you can use this command to easily change your commit message, if no changes were made since the newest commit.

$ git commit -m “my first commit”

$ git add example_file

$ git commit --amend
In the above example, a forgotten file is added to a commit.

### Unstaging a File
$ git reset HEAD index.html

Unstaged changes after reset:

M index.html
Above, we see that the git reset HEAD command unstaged the index.html file.

NOTE: When git reset --hard is used, Git overwrites all changes in the working directory, permanently destroying any uncommitted changes.

### Undo a Committed Snapshot
To undo changes resulting from a particular commit, use the git revert command. This command appends a new commit that undoes changes introduced by a specific commit. This prevents Git from losing history.

$ git commit -m "Example Commit"

$ git revert HEAD
*In the example above, a new commit gets appended and rolls back changes from a specific commit.

### Unmodifying a File
To have a file return to its state when you last committed, utilize the git checkout command.

Example:

$ git checkout -- index.html
NOTE: git checkout -- file erases any changes made to the file because you are copying another file over it. Almost all committed information in Git can be recovered; however, any uncommitted information can be lost forever.

### Branching
Almost every type of Version Control System incorporates branching. By creating branches of a central repository, collaborators are able to work on a project simultaneously via multiple branches, without affecting this main repository.

A collaborator can create a branch, work on it and save commit snapshots within it, switch between various branches, and merge changes. A Git branch is basically a movable pointer that always points to the most recent commit, or snapshot. Git uses the default local branch name “master,” which can be changed. Just because the default name is “master” does not imply that it is higher in importance or has more functionality than other branches. The head is a special pointer which indicates which branch you are currently working within.

![Branching](https://blog.udemy.com/wp-content/uploads/2015/08/image016.png)


[🔙 GO BACK](README.md)

