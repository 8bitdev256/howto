Explaining the git pull command:
The git pull command is nothing more than a git fetch command with a git merge command after

See the differences between a local branch and a remote branch:
git diff local_branch_name remote_branch_name
Example: git diff main origin/main <- main is local and origin/main is remote

Clone a specific branch from remote repository:
git clone repository_link --branch branch_name --single-branch

Archive (undo) some change made to repository:
git stash

List all archived changes on current branch:
git stash list

Bring back archived changes:
git stash pop <- bring back archived changes and remove changes from archived changes list
git stash apply <- bring back archived changes and keep changes from archived changes list
