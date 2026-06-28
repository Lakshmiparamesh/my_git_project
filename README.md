

## Phase 1 — Create Directory and Script Files

Create a new project directory and populate it with shell script files.

```bash
# Create and enter the project directory
mkdir my-git-project && cd my-git-project

# Create shell script files
touch app.sh utils.sh config.sh

# Add content to each script
echo '#!/bin/bash' > app.sh
echo 'echo "App script running"' >> app.sh

echo '#!/bin/bash' > utils.sh
echo 'echo "Utility functions loaded"' >> utils.sh

echo '#!/bin/bash' > config.sh
echo 'echo "Configuration loaded"' >> config.sh

# Make scripts executable
chmod +x app.sh utils.sh config.sh

# Verify files are created
ls -la
```

---

## Phase 2 — Initialise Git Repository

Convert the local directory into a Git repository.

```bash
# Initialise an empty Git repository
git init

# Stage all files
git add .

# Verify what is staged
git status

# Create the initial commit
git commit -m "Initial commit: add shell scripts"

# View commit history
git log --oneline
```

---

## Phase 3 — Connect to GitHub and Push

Create an empty repository on GitHub and link it to the local repository.


## Phase 4 — Merge

Merge changes from a feature branch into main.

```bash
# Create and switch to a new feature branch
git checkout -b feature/new-script

# Create a new script on this branch
echo '#!/bin/bash' > feature.sh
echo 'echo "New feature script"' >> feature.sh
chmod +x feature.sh

# Stage and commit
git add feature.sh
git commit -m "feat: add feature script"

# Switch back to main
git checkout main

# Merge the feature branch into main
git merge feature/new-script

# View the merge result
git log --oneline --graph

# Push merged result to GitHub
git push origin main
```

---

## Phase 5 — Rebase

Rebase a branch on top of the latest main for a clean, linear history.

```bash
# Create a new branch from main
git checkout -b feature/refactor

# Make changes on this branch
echo "# refactored section" >> utils.sh
git add utils.sh
git commit -m "refactor: update utils script"

# Rebase this branch on top of main
git rebase main

# Switch to main and fast-forward merge
git checkout main
git merge feature/refactor

# Push to GitHub
git push origin main

# View clean linear history
git log --oneline --graph --all
```

> **Tip:** Never rebase branches that have already been pushed and shared with others.
> Rebase rewrites commit history, which can cause conflicts for other collaborators.

---

## Phase 6 — Stash

Temporarily save uncommitted changes without making a commit.

```bash
# Make some in-progress changes (not ready to commit)
echo "# work in progress — do not commit" >> config.sh

# Check current status
git status

# Stash the uncommitted changes
git stash

# Verify working directory is now clean
git status

# List all stash entries
git stash list

# (Do other work or switch branches here if needed)

# Restore the stashed changes
git stash pop

# Verify changes are back
cat config.sh
```

### Useful stash commands

```bash
git stash save "WIP: config changes"  
```

