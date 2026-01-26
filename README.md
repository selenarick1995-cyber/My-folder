# Configure u (once)
git config --global user.name "Your Name"
git config --global user.email "you@example.c

# Initialize a new locl repo
git init

# Clone an existing repo
git clone git@github.com:username/repo.git
# or using HTTPS:
# git clone https://github.com/username/repo.git

# Check status and history
git status
git log --oneline --graph --all

# Basic staging and committing
git add file.txt              # stage a single file
git add .                     # stage all changes
git commit -m "Short clear message"

# Amend last commit (only if not pushed)
git commit --amend --no-edit

# Create and switch branches
git branch                      # list branches
git branch feature/my-feature   # create branch
git checkout feature/my-feature # switch (old)
git switch feature/my-feature   # switch (new)

# Create and push a new branch to remote
git push -u origin feature/my-feature

# Fetch, pull, and merge
git fetch origin
git pull origin main            # fetch + merge from remote main into current
git merge origin/main           # merge fetched main into current branch

# Rebase (use carefully)
git checkout feature/my-feature
git rebase main                 # replay commits on top of latest main
# To abort a rebase:
git rebase --abort

# Stash changes
git stash push -m "WIP: notes"
git stash list
git stash pop                   # apply and remove latest stash

# Undo changes
git restore file.txt            # discard working-dir changes (Git 2.23+)
git checkout -- file.txt        # older style to discard changes
git reset --soft HEAD~1         # undo last commit, keep changes staged
git reset --hard HEAD~1         # undo last commit and discard changes (dangerous)

# Remove a file from repo but keep locally
git rm --cached secret.txt
echo "secret.txt" >> .gitignore
git add .gitignore
git commit -m "Ignore secret.txt"

# Tags
git tag -a v1.0 -m "Release v1.0"
git push origin v1.0

# Cherry-pick a commit from another branch
git cherry-pick <commit-hash>

# Show differences and blame
git diff                       # unstaged changes
git diff --staged              # staged vs HEAD
git blame file
