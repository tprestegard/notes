# Some useful git commands

## Misc
* Stop tracking an upstream branch: `git branch --unset-upstream`
* Push a local branch to remote: `git push -u origin [branch_name]`
* Delete a remote branch: `git push --delete origin [branch_name]`
* Check out a remote branch locally and track the remote:
  * `git checkout -b [local_name] origin/[branch_name]`
  * `git checkout --track origin/[branch_name]`
* Add an upstream remote branch to an already existing local branch: `git branch -u origin/[remote_name]`
* Search git diffs for any commits which remove/add a string: `git log -Sstring`
* Search git log:
  * Open log with 'git log'
  * Search by entering '/string'
* Clean up untracked files: `git clean -dxf`
* List different commits between two branches: `git log --left-right --graph --cherry-pick --oneline feature...branch`
* Set a local repository as a remote: `git remote add repo_name /path/to/repo/.git`
* Override local branch with git pull: `git fetch --all; git reset --hard origin/branch_name`
* Pull a remote into another local branch without switching branches: `git fetch origin master:master`

## Commits
* Remove a specific commit: `git rebase -p --onto SHA1^ SHA1`
* Set commit author: `git commit -m "message" --author="Name <email>"`
* Set author date: `git commit -m "message" --date="Tue Dec 12 2017 09:01:14 -0600"`
* Set commit date: `GIT_COMMITTER_DATE="Tue Dec 12 2017 09:01:14 -0600" git commit -m "message"`
* View author and commit dates: `git log --format=fuller`
* Find commit where a file was first added: `git log --diff-filter=A -- file.py`
* See all commits for a specific file: `git log --follow file.py`
* View file at a specific commit: `git show REVISION:/path/to/file`
* See cached changes: `git diff --cached`
* Edit chunks of cached changes: `git reset -p`
* Edit/amend a past commit:
  1. Do an interactive rebase and set the commit to be edited.
  2. When the rebase stops on that commit, do: `git commit --amend [other stuff]`
* Change author of old commit:
  1. Do interactive rebase, set the commit in question to 'edit'
  2. When stopped, do: `git commit --amend --author="name <email>"`

## Tags
* Create a tag: `git tag -a "version" -m "message"`
* List tags with messages and sorted by version: `git tag -l --sort=v:refname -n`
* Push tags to remote: `git push --tags`
* Delete a tag (locally): `git tag -d gracedb-1.26-1`
* Push a local tag deletion to remote: `git push --delete origin gracedb-1.26-1`
