# Git Documentation Tree

## Overview
- **What is Git?**
  - Distributed version control system
  - Track changes in source code
- **Key Features**
  - Branching and Merging
  - Distributed Development
- **Getting Started**
  - Installing Git
  - Initial Configuration
  - Sample Repository Setup
- **Basic Terminology**
  - Repository, Commit, Branch, Merge, etc.

## Repositories
- **Creating a Repository**
  - **Local Repositories**
    - Scenario: Start a new project
    - Sample Code:
      ```bash
      mkdir my-project
      cd my-project
      git init
      ```
  - **Remote Repositories**
    - Scenario: Push a local repository to GitHub
    - Sample Code:
      ```bash
      git remote add origin https://github.com/username/my-project.git
      git push -u origin master
      ```
- **Cloning Repositories**
  - **Cloning from a Remote**
    - Scenario: Clone an existing repository to start working on it
    - Sample Code:
      ```bash
      git clone https://github.com/username/repository.git
      ```
  - **Cloning via SSH**
    - Scenario: Use SSH for secure access
    - Sample Code:
      ```bash
      git clone git@github.com:username/repository.git
      ```
- **Repository Structure**
  - **.git Directory**
    - Stores metadata and object database
  - **Working Directory**
    - Files that are currently being edited
  - **Staging Area**
    - Intermediate area where changes are prepared for commit

## Files
- **Viewing Files**
  - **`git status`**
    - Scenario: Check the status of working directory and staging area
    - Sample Code:
      ```bash
      git status
      ```
  - **`git ls-files`**
    - Scenario: List all files tracked by Git
    - Sample Code:
      ```bash
      git ls-files
      ```
- **Editing Files**
  - **Modifying Files**
    - Scenario: Edit a file and prepare it for commit
    - Sample Code:
      ```bash
      echo "New content" >> file.txt
      git add file.txt
      ```
  - **Stage Changes**
    - Scenario: Stage files for the next commit
    - Sample Code:
      ```bash
      git add file1.txt file2.txt
      ```
- **Viewing File History**
  - **`git log`**
    - Scenario: View the commit history for a file
    - Sample Code:
      ```bash
      git log file.txt
      ```
  - **`git diff`**
    - Scenario: See the differences between working directory and last commit
    - Sample Code:
      ```bash
      git diff
      ```

## Commits
- **Making Commits**
  - **`git add`**
    - Scenario: Add files to the staging area
    - Sample Code:
      ```bash
      git add file.txt
      ```
  - **`git commit`**
    - Scenario: Commit staged changes with a message
    - Sample Code:
      ```bash
      git commit -m "Add new feature"
      ```
  - **Commit Messages**
    - Best practices for writing meaningful commit messages
- **Viewing Commit History**
  - **`git log`**
    - Scenario: View commit history in a concise format
    - Sample Code:
      ```bash
      git log --oneline
      ```
- **Amending Commits**
  - **`git commit --amend`**
    - Scenario: Modify the last commit (e.g., add missed changes)
    - Sample Code:
      ```bash
      git add additional-file.txt
      git commit --amend
      ```
- **Reverting Commits**
  - **`git revert`**
    - Scenario: Create a new commit that undoes changes from a previous commit
    - Sample Code:
      ```bash
      git revert <commit-hash>
      ```
  - **`git reset`**
    - Scenario: Undo commits (soft, mixed, hard resets)
    - Sample Code:
      ```bash
      git reset --hard <commit-hash>
      ```

## Pushes
- **Pushing Changes**
  - **`git push`**
    - Scenario: Push local commits to a remote repository
    - Sample Code:
      ```bash
      git push origin master
      ```
  - **`git push --force`**
    - Scenario: Force push changes (use with caution)
    - Sample Code:
      ```bash
      git push --force origin master
      ```
- **Push Policies**
  - **Branch Protection**
    - Scenario: Enforce rules on a branch (e.g., require pull requests)
  - **Rebase and Merge Policies**
    - Scenario: Use rebase or merge to integrate changes
- **Resolving Push Errors**
  - **Conflicts**
    - Scenario: Resolve conflicts that occur during push
    - Sample Code:
      ```bash
      git pull --rebase
      ```
  - **Authentication Issues**
    - Scenario: Address issues with credentials

## Branches
- **Creating Branches**
  - **`git branch`**
    - Scenario: Create a new branch for a feature
    - Sample Code:
      ```bash
      git branch feature-branch
      ```
  - **`git checkout -b`**
    - Scenario: Create and switch to a new branch
    - Sample Code:
      ```bash
      git checkout -b feature-branch
      ```
- **Managing Branches**
  - **Merging Branches**
    - Scenario: Merge a feature branch into master
    - Sample Code:
      ```bash
      git checkout master
      git merge feature-branch
      ```
  - **Deleting Branches**
    - Scenario: Remove a branch that is no longer needed
    - Sample Code:
      ```bash
      git branch -d feature-branch
      ```
- **Branch Policies**
  - **Naming Conventions**
    - Scenario: Follow consistent naming for branches
  - **Access Control**
    - Scenario: Restrict branch access to specific users
- **Viewing Branch History**
  - **`git log --graph`**
    - Scenario: Visualize branch history and merges
    - Sample Code:
      ```bash
      git log --graph --oneline --all
      ```
  - **`git branch -a`**
    - Scenario: List all branches
    - Sample Code:
      ```bash
      git branch -a
      ```

## Tags
- **Creating Tags**
  - **Lightweight Tags**
    - Scenario: Create a simple tag for a commit
    - Sample Code:
      ```bash
      git tag v1.0
      ```
  - **Annotated Tags**
    - Scenario: Create a tag with additional metadata
    - Sample Code:
      ```bash
      git tag -a v1.0 -m "Release version 1.0"
      ```
- **Viewing Tags**
  - **`git tag -l`**
    - Scenario: List all tags
    - Sample Code:
      ```bash
      git tag -l
      ```
  - **`git show <tag>`**
    - Scenario: View details of a specific tag
    - Sample Code:
      ```bash
      git show v1.0
      ```
- **Managing Tags**
  - **Deleting Tags**
    - Scenario: Remove a tag that was created by mistake
    - Sample Code:
      ```bash
      git tag -d v1.0
      ```
  - **Pushing Tags to Remote**
    - Scenario: Share tags with a remote repository
    - Sample Code:
      ```bash
      git push origin v1.0
      ```

## Pull Requests
- **Creating Pull Requests**
  - **Opening a Pull Request**
    - Scenario: Start a pull request to merge changes into a main branch
    - Sample Code: (Typically done via a platform UI like GitHub or GitLab)
- **Reviewing Pull Requests**
  - **Commenting**
    - Scenario: Add comments or suggestions on changes
    - Sample Code: (Typically done via a platform UI)
  - **Approving Changes**
    - Scenario: Review and approve changes for merging
    - Sample Code: (Typically done via a platform UI)
- **Merging Pull Requests**
  - **Merge Strategies**
    - Scenario: Choose a merge strategy (merge commit, squash, rebase)
    - Sample Code:
      ```bash
      git merge feature-branch
      ```
  - **Resolving Conflicts**
    - Scenario: Handle merge conflicts during pull request merge
    - Sample Code:
      ```bash
      git merge feature-branch
      # Resolve conflicts in files
      git add resolved-file.txt
      git commit
      ```

## Advanced Topics
- **Advanced Git Commands**
  - **`git cherry-pick`**
    - Scenario: Apply a specific commit from another branch
    - Sample Code:
      ```bash
      git cherry-pick <commit-hash>
      ```
  - **`git rebase`**
    - Scenario: Reapply commits on top of another base tip
    - Sample Code:
      ```bash
      git rebase master
      ```
- **Git Hooks**
  - **Pre-commit Hooks**
    - Scenario: Automatically run scripts before committing
    - Sample Code: (Scripts placed in `.git/hooks/pre-commit`)
  - **Post-commit Hooks**
    - Scenario: Perform actions after a commit
    - Sample Code: (Scripts placed in `.git/hooks/post-commit`)
- **Configuration**
  - **`.gitconfig`**
    - Scenario: Set global Git configuration
    - Sample Code:
      ```bash
      git config --global user.name "Your Name"
      git config --global user.email "you@example.com"
      ```
  - **Setting Global and Local Configurations**
    - Scenario: Different settings for different repositories
    - Sample Code:
      ```bash
      git config --local user.name "Local Name"
      ```
- **Git Internals**
  - **Object Storage**
    - Scenario: Understand how Git stores data
  - **Refs and Branches**
    - Scenario: Explore how branches and tags are implemented internally
