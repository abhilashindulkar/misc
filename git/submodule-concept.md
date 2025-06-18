# Git Submodule

Git submodules are a feature in Git that allow you to include one Git repository as a subdirectory of another Git repository. This is useful when you want to include an external dependency (repository) within your own project while keeping it tracked by Git.

Why are submodules useful?

1. You can track specific versions of the submodule in your project.
2. The submodule remains independent; you can fetch updates or switch versions without merging its content directly into your repository.
3. Reuse code across multiple projects (if multiple projects use the same library, all can point to the same submodule).

### Commands

1. Initialize a new project through git init or clone the remote repository.

2. Add submodule into the cloned repo

git submodule add <submodule-library-link> <submodule-name>

Example - 

git submodule add git@github.com:abc-technologies-ecommerce/submodule-test.git submodule-test

3. Git will clone the submodule into the specified directory (submodule-test) add a configuration entry to the .gitmodules file in your main project.

[submodule "submodule-test"]
        path = submodule-test
        url = git@github.com:abc-technologies-ecommerce/submodule-test.git

4. Commit & Push the changes

git add .gitmodules my-library
git commit -m "Added my-library as a submodule"
git push

---

### Working with submodule

1. When you clone a repository that has submodules, the submodules won’t automatically be cloned. You need to initialize and update them.

git clone https://github.com/your-project.git

2. Initialize and update submodules

git submodule init
git submodule update

#### Pull Updates for Submodules

git pull origin main

git submodule update --remote

git push origin main

