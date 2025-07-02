### Fast-Forward Merge
1. Create a new branch and make some commits.

git init
echo "Initial content" > file.txt
git add file.txt
git commit -m "Initial commit"
 
git checkout -b feature-branch
echo "Feature content" >> file.txt
git add file.txt
git commit -m "Add feature content"


2. Switch back to the main branch and merge.

Since main has no new commits, Git will perform a fast-forward merge, moving the main pointer to the feature-branch commit.

git checkout main
git merge feature-branch


### Recursive Merge (3-Way Merge)
A recursive merge is used when both branches have diverged (have unique commits). Git creates a new merge commit.

1. Create a new branch and make commits.

git checkout -b feature-branch
echo "Feature content" >> file.txt
git add file.txt
git commit -m "Add feature content"
2. Switch back to main and make a commit.

git checkout main
echo "Main content" >> file.txt
git add file.txt
git commit -m "Add main content"
3. Merge feature-branch into main.

Git will perform a recursive merge, combining changes from both branches and creating a new merge commit.

git merge feature-branch

### Ours/Theirs Merge
These strategies allow you to resolve conflicts by favoring one branch over the other.

#### Ours Strategy
Keeps changes from the current branch and discards changes from the other branch.

1. Create a conflict.

git checkout -b feature-branch
echo "Feature content" > file.txt
git add file.txt
git commit -m "Add feature content"
 
git checkout main
echo "Main content" > file.txt
git add file.txt
git commit -m "Add main content"
2. Merge using ours strategy.

The main branch's content will be preserved, and changes from feature-branch will be ignored.

git merge -s ours feature-branch

#### Theirs Strategy
Keeps changes from the other branch and discards changes from the current branch.

1. Merge using theirs strategy.

The feature-branch's content will be preserved, and changes from main will be ignored.

git merge -s theirs feature-branch

### Octopus Merge
An octopus merge is used to merge multiple branches simultaneously. It’s typically used for integrating multiple feature branches into main.

1. Create multiple branches.

git checkout -b feature-1
echo "Feature 1 content" >> file.txt
git add file.txt
git commit -m "Add feature 1 content"
 
git checkout main
git checkout -b feature-2
echo "Feature 2 content" >> file.txt
git add file.txt
git commit -m "Add feature 2 content"
 
git checkout main
git checkout -b feature-3
echo "Feature 3 content" >> file.txt
git add file.txt
git commit -m "Add feature 3 content"
2. Merge all branches into main.

Git will perform an octopus merge, combining all branches into main.

git checkout main
git merge feature-1 feature-2 feature-3

### Resolving Merge Conflicts
When merging branches with conflicting changes, Git will prompt you to resolve conflicts.

1. Create a conflict.

git checkout -b feature-branch
echo "Feature content" > file.txt
git add file.txt
git commit -m "Add feature content"
 
git checkout main
echo "Main content" > file.txt
git add file.txt
git commit -m "Add main content"
2. Attempt to merge.

Git will notify you of a conflict in file.txt.

git merge feature-branch
3. Resolve the conflict:

Open file.txt and manually resolve the conflict (look for <<<<<<<, =======, and >>>>>>> markers).
Stage the resolved file.
git add file.txt
4. Complete the merge.

git commit

### Squash Merge
A squash merge combines all commits from a branch into a single commit on the target branch.

1. Create a branch and make multiple commits.

git checkout -b feature-branch
echo "Feature content 1" >> file.txt
git add file.txt
git commit -m "Add feature content 1"
 
echo "Feature content 2" >> file.txt
git add file.txt
git commit -m "Add feature content 2"
2. Squash merge into main.

git checkout main
git merge --squash feature-branch
git commit -m "Squash merge feature-branch"

### Rebase and Merge
Rebasing rewrites the commit history by moving commits from one branch to another.

1. Create a branch and make commits.

git checkout -b feature-branch
echo "Feature content" >> file.txt
git add file.txt
git commit -m "Add feature content"
2. Rebase onto main.

git checkout main
git pull
git checkout feature-branch
git rebase main
3. Merge into main.

git checkout main
git merge feature-branch


### Summary of Merge Strategies


Fast-Forward

Moves the branch pointer forward when no divergent commits exist.

Recursive

Combines changes from divergent branches and creates a merge commit.

Ours/Theirs

Resolves conflicts by favouring one branch's changes over the other.

Octopus

Merges multiple branches simultaneously.

Squash

Combines all commits from a branch into a single commit.

Rebase

Rewrites commit history by moving commits to the tip of the target branch.


