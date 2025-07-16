# Command References

- git initial commands.
```
# git user config
git config --global user.name "abhilash"
git config --global user.email "abhilash@xyz.com

# git local working directory initialization
git init

# to push local repo into github, create a new repo.
git remote add origin <repo https url>

# requires pat token with repo acccess. It has to be generated in github's settings--> developer settings --> PATs.
git remote set-url origin <user+repo https url>

# ssh-keygen
ssh-keygen -t rsa -b 4096 -C newkey

# start the ssh agent
eval $(ssh-agent -s)

# add the private key to the ssh agent. store the public key in github setting's ssh and gpg keys.
ssh-add newkey

# clone the repo.
git clone <https/ssh git repo url>

# display remote repositories associated with git repo.
git remote -v
```

- Branching
```
# List all branches including ones in remote.
git branch -a

# Check local branch existence
git rev-parse --verify <branch-name>

# Check remote branch existence
git ls-remote --quiet --heads <branch-name>

# Check default branch
git remote show origin | grep 'HEAD branch' | cut -d' ' -f5

# Create and also switch to a new branch.
git checkout -b new-branch

# or
git branch new-branch
git checkout new-branch

# Switch to a existing branch - checkout/switch.
git checkout old-branch

git switch old-branch

# Branch rename.
git branch -m old-name new-name

git switch old-name
git branch -m new-name

# Delete branch - local, remote
git branch -d new-name

git push origin -d new-name # use -D for force deletion
```

- Checking out to commit (code snapshot).
```
# Older commit id. HEAD detaches from branch.
git checkout <commit-id>

# to go back to branch.
git checkout <branch-name>
```

- Retrieve the commit id.
```
# for HEAD, 40 characters commit id.
git rev-parse HEAD

# short commit id - 8 characters.
git rev-parse --short HEAD

# local 
git rev-parse dev

# remote branch.
git rev-parse origin/master
```

- Check whether the curent branch is merged into master branch or not.
```
git log --graph --oneline master dev
```

- Fetch the changes from remote repository, but doesnt apply it into local branch. Used for reviewing fetched changes before deciding to merge/rebase.
```
git fetch origin master

git log origin/master
```

- Commit with additional options.
```
# Commit with amend - update commit message or stage left over files with same older commit id.
git commit --amend -m "updated commit message"

# Commit with no-edit - stage left over files with same older commit id, message.
git commit --amend --no-edit

# Note - requires force push after the above operation.
git push origin new-feat -f
```

- Revert & Reset commit ID.
```
# Reverts commit id, creates a new commit.
git revert <commit-id>

# Reset commit, moves the HEAD to specified commit, discards the changes in working directory. other commits are deleted.
git reset --hard <commit-id>

# Reset commit, moves the HEAD to specified commit, preserves the changes made after the commit as staged changes.
git reset --soft <commit-id>
```

- Open Source Code Contribution
```
# Fork the target/original repository.

# Clone the forked repository.
git clone forked-repo-url

# Set up the upstream remote repository.
git remote add upstream target/origin-repo-url

# Checkout to new branch, add/commit changes.
git checkout -b new-feat

# After file addition/update/delete.
git add file(s)

git commit -m "added new feat"

# Push the changes
git push origin new-feat

# Create a PR through GitHub console.

# Review, merge and close the PR.
```

- Rebase branch.
```
# if stale and no new changes.
git pull origin new-feat

# add/commit changes in current branch.
git commit -am "new commit"

# Checkout to master branch.
git checkout master

# Pull the latest changes (fetch & merge).
git pull origin master

# Once pulled, checkout back to new-feat branch.
git checkout new-feat

# Rebase the changes.
git rebase -i master

# To avoid rebase operation.
git rebase --abort

# while rebasing, if there are many conflicts - resolve one, stage, continue.
git add resolved-file.txt

git rebase --continue
...
# once rebase completes,
git commit -m "rebased, resolved conflicts"

git push origin new-feat -f
```

- Squash multiple commits into one before pushing into remote.
```
# squash commit - last two commit ids.
git rebase -i HEAD~2

# editor mode - pick --> squash for older commits --> save changes.

# once rebased, push the branch with force option.
git push origin new-feat -f
```

- Merge branch.
```
# Checkout to main branch.
git checkout main/master

# Pulls the lates changes. 
git pull origin master

# Merge main/master branch into feat-branch.
git checkout feat-branch

# Merge master and creates a merge commit.
git merge master

# Push feat-branch changes to remote repo.
git push origin feat-branch -f
```

- Tag.
```
# Annotated Tag - includes extra information.
git tag -a v1.0 -m "Version 1.0 release"

# Lightweight Tag:
git tag v1.0

# List Tags:
git tag

# Show Tag Details:
git show v1.0

# Push Tags to Remote:
git push origin --tags

# Delete a Tag:
git tag -d v1.0

# Delete a Remote Tag:
git push origin --delete v1.0
```
