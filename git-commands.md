# git for teams

## basic commands

	git clone _URL_

download a copy of a remote repository

	git init

convert a current directory into a new git repository

	git status

get a status report for your repository

	git commit -m "_message_"

commit all staged files to your repository

	git log

review a repository's history

	git log --oneline

lists history of commits and each commit message is listed on one line

	git log -- <filename>

lists the history of one file

	git branch --list

list all local branches

	git branch --all

list local and remote branches

	git branch --remotes

list all remote _branches_

	git checkout --track _remote_name/branch_

create a copy of a remote branch for local use

	git checkout _branch_

switch to a different local branch

	git checkout -b _branch_ _branch_parent_

create a new branch from a specified branch

	git add --update

stages all files, that are known to git, and that have been edited (or updated)

	git status
	git add --all

stages all files including all unstaged files
add all changed and new files to the staging area of your repository

	git add _filename(s)_

stage only the specified file so that it is ready to be committed

	git add --patch _filename_

stage only portions of a file so that they are ready to be committed
stages just a part of the changes of the changed file with filename

	git reset HEAD _filename_

removes the file with filename from the staging area

	git commit --amend

update the previous commit with changes currently staged and supply a new commit message

	git config --global core.excludefiles ~/.gitignore

adds a global .gitignore file to your home directory

	git log --oneline
	git log _fa04c30_ --max-depth=1

shows the detailed commit message for the commit fa04c30

	git show _fa04c30_

shows the detailed commit message including changes for the commit fa04c30

	git tag _import_ _fa04c30_

adds the tag 'import' to the commit fa04c30

	git tag

lists all tags

	git show _import_

shows the detailed commit message including changes for the commit with the tag 'import'

	git remote add _remote_name_ _url_

create a new reference to a new remote repository

	git push

upload changes for the current branch to a remote repository

	git remote --verbose

list the fetch and push urls for all available remotes

	git push --set-upstream _remote_name_ _branch_local_ _branch_remote_
push a copy of your local branch to the remote server

	git merge _branch_

incorporate the commits currently stored in another branch into the current one

	git push --delete _remote_name_ _branch_remote_

remove named branch from the remote server

## removing

	git rm _filename_

remove file from working copy and git repository

	git rm --cached _filename_

remove file from git repository, but not from the file system

## rollbacks, reverts, resets and rebasing

	git checkout -- _filename_

discard changes you've made to a file in your working directory; changed file is not staged or committed;

	git reset -- hard

discard all unsaved changes in the working directory;
file is staged, but not committed;

	git reset commit

combine several commits up to, but not including, a specific commit

	git clean -fd

remove all unsaved changes, including untracked; changed files are not committed;

	git revert _commit_

remove previous work, but keep the commit history intact (roll forward); branch has been published; working directory is clean;

	git rebase -- interactive _commit_

remove a single commit from a branch's history; changed files are committed; working directory is clean; branch has not been published;

	git rebase -- interactive _commit_

keep previous work, but combine it with another commit;


### rebasing with conflict

	git reset HEAD _file_
	git add _file_

while rebasing this puts the file to the state of the last commit

	git rebase --continue

proceed with rebasing

	git mergetool _file_

opens the conflict in the mergetool -> save file;

	git add _file_

to mark the conflict as resolved


### locating lost work

	git reflog

lists a history of everything that has happened in your local copy of the repository

	git checkout _commit_
	git checkout -b _new_branch_name_

to go back to a certain commit and use that commit for a basis for a new branch

	git checkout _working_branch_
	git merge _new_branch_name_
	git branch --delete _new_branch_name_
	git push --delete _new_branch_name_

to merge the new branch to the head of the old branch

## cherry picking

	git checkout <branch_name> -- <paths>

to checkout file(s) from an other branch to the actual branch

## big

if you want the default branch to be something other than master, you need to do this:

	git symbolic-ref HEAD refs/heads/mybranch

# Fugitive Git in Vim

	:Git add %		:Gwrite

Stage the current file to the index

	:Git checkout %	:Gread

Revert current file to last checked in version

	:Git rm %		:Gremove

Delete the current file and the corresponding Vim buffer

	:Git mv %		:Gmove

Rename the current file and the corresponding Vim buffer

	:Git commit %	:Gcommit

Commits the current file with aoutocompletiion in the commit message

	:Git blame %	:Gblame

	:Gstatus
	:Gdiff

# finding in Repo

	git log --name-status --grep _query-string_

finds affected files with the query-string in commit messages

# Alias

	[alias]
		co = checkout
		br = branch
		lo = log --oneline
		au = add --update
		cv = commit
		pr = pull --rebase
		af = diff-tree --name-only -r
		find = log --pretty=\"format:%Cgreen%H %Cblue%s\" --name-status --grep
