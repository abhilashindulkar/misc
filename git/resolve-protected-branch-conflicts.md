# Resolve Protected branch conflicts. DEV-UAT

### Step 1: Create a new temporary branch from dev

git checkout dev
git pull origin dev
git checkout -b temp-merge-dev-uat

### Step 2: Merge uat into the temporary branch

git pull origin uat
git merge uat

### Step 3: Resolve conflicts manually, then

git add <conflicted-files>
git commit -m "Merged uat into temp-merge-dev-uat and resolved conflicts"

### Step 5: Push the temporary branch to the remote repository

git push origin temp-merge-dev-uat

### Step 6: Create a PR from temp-merge-dev-uat to dev using the interface


### Step 7: Delete the temporary branch locally and remotely after merging the PR

git branch -d temp-merge-dev-uat
git push origin --delete temp-merge-dev-uat
