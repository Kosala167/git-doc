# Git Workflow Documentation

This document outlines common Git commands and workflows for various roles within a development team, focusing on clarity and best practices.

---

## 1. Initial Setup & Configuration

* **Set Global User Identity:**
    ```bash
    git config --global user.name "Your Name" [cite: 1]
    git config --global user.email "your.email@example.com" [cite: 1]
    ```
    * **Note:** Omit `--global` if you need project-specific configurations (e.g., for personal projects vs. work projects). [cite: 1]
* **Initialize a New Local Repository:**
    ```bash
    git init [cite: 1]
    ```
    * This creates a `.git` folder, making the current directory a Git repository.

---

## 2. Basic Local Workflow (All Developers)

These are the fundamental commands for daily work within your local repository.

* **Check Status:** See changes in your working directory and staging area. [cite: 10]
    ```bash
    git status [cite: 10]
    ```
* **Add Files to Staging (Index):** Prepare changes for the next commit. [cite: 1]
    ```bash
    git add file1.extension file2.extension ... # Add specific files [cite: 1]
    git add . # Add all changes in the current directory and subdirectories
    ```
* **Commit Changes:** Save staged changes to your repository's history with a descriptive message. [cite: 1]
    ```bash
    git commit -m "Some meaningful commit message" [cite: 1]
    ```
* **View Staged Changes:** Shows differences between the staging area and your last commit (HEAD). [cite: 5]
    ```bash
    git diff --cached <filename> [cite: 5]
    ```
* **View Unstaged Changes:** Shows differences between your working directory (what you're editing) and the staging area. [cite: 4]
    ```bash
    git diff <filename> [cite: 4]
    ```
* **View All Uncommitted Changes:** Shows differences between your working directory and your last commit (HEAD) (includes both staged and unstaged changes). [cite: 6]
    ```bash
    git diff HEAD [cite: 6]
    ```
* **View Commit History:**
    ```bash
    git log # Full history [cite: 12]
    git log --oneline # Concise one-line history [cite: 12]
    git log --oneline <branch_name> # History of a specific branch [cite: 12]
    ```
* **Check Which Files are Tracked:**
    ```bash
    git ls-files [cite: 1]
    ```
* **Discard Local Changes:**
    ```bash
    git restore <filename> # Discard changes in your working directory for a specific file [cite: 14]
    git restore . # Discard all changes in working directory
    ```
* **Unstage Files:**
    ```bash
    git reset HEAD <filename> # Removes file from staging area, keeps changes in working directory
    ```
* **Remove Files:** Remove from working directory and stage for deletion. [cite: 13]
    ```bash
    git rm <filename> [cite: 13]
    ```
* **Move/Rename Files:** Move or rename files and stage the change. [cite: 1]
    ```bash
    git mv old_name new_name [cite: 1]
    ```
* **Temporarily Save Uncommitted Work (Stashing):**
    * Save all uncommitted changes to a temporary location. [cite: 1]
        ```bash
        git stash [cite: 1]
        ```
    * Apply the latest stashed changes back to your working directory. [cite: 1]
        ```bash
        git stash apply [cite: 1]
        ```

---

## 3. Branching Workflow

Branching is fundamental for parallel development and organizing work.

* **List Local Branches:**
    ```bash
    git branch [cite: 2]
    ```
* **List All Branches (Local and Remote-tracking):**
    ```bash
    git branch -a [cite: 2]
    ```
* **List Remote Branches Only:**
    ```bash
    git branch -r [cite: 2]
    ```
* **Create a New Branch:**
    ```bash
    git branch <new_branch_name> [cite: 2]
    ```
* **Switch to an Existing Branch:**
    ```bash
    git checkout <branch_name> [cite: 2]
    ```
* **Create and Switch to a New Branch:**
    ```bash
    git checkout -b <new_branch_name> [cite: 2]
    ```
* **Rename a Local Branch:**
    * Rename a specific local branch:
        ```bash
        git branch -m <old_branch_name> <new_branch_name> [cite: 2]
        ```
    * Rename the currently checked-out branch:
        ```bash
        git branch -m <new_branch_name> [cite: 2]
        ```
* **Delete a Local Branch:**
    ```bash
    git branch -d <branch_name> # Deletes only if merged [cite: 2]
    git branch -D <branch_name> # Force delete (use with caution)
    ```

---

## 4. Working with Remotes

How to interact with remote repositories (like GitHub, GitLab, Bitbucket).

* **List Remotes and URLs:**
    ```bash
    git remote -v [cite: 8]
    ```
* **Add a Remote (e.g., your fork's origin):**
    ```bash
    git remote add origin [https://github.com/your_username/your_repo.git](https://github.com/your_username/your_repo.git) [cite: 1]
    ```
* **Rename a Remote:**
    ```bash
    git remote rename old_alias new_alias [cite: 1]
    ```
* **Remove a Remote:**
    ```bash
    git remote remove <remote_alias> [cite: 1]
    ```
    * Useful if a server moved, a mirror is no longer used, or a contributor leaves. All remote-tracking branches and config settings for that remote will be deleted. [cite: 1]
* **Fetch Changes from a Remote:** Download objects and refs from another repository. [cite: 1]
    ```bash
    git fetch <remote_alias> <branch_name> [cite: 1]
    git fetch origin master # Update local repo from origin/master [cite: 1]
    ```
* **Pull Changes from a Remote (Fetch + Merge):** Download changes and automatically merge them into your current branch. [cite: 1]
    ```bash
    git pull origin <branch_name> [cite: 1]
    git pull origin master # Pull from master branch of origin [cite: 1]
    ```
* **Pull Changes from a Remote (Fetch + Rebase):** Get latest commits and rebase your local commits on top. [cite: 1]
    ```bash
    git pull --rebase origin <branch_branch> # Use --rebase instead of merge
    git pull -r origin main # Get latest main commits before pushing [cite: 1]
    ```
* **Push Changes to a Remote:** Upload your local commits to a remote repository. [cite: 8]
    ```bash
    git push origin <branch_name> [cite: 2]
    git push origin new_branch # Push new_branch to origin [cite: 2]
    git push origin master # Push master branch to origin [cite: 8]
    ```
* **Force Push (Use with EXTREME Caution!):** Overrides remote history. [cite: 9]
    ```bash
    git push -f origin <branch_name> # Not recommended as it overrides people's changes. [cite: 9]
    ```
* **Delete Remote Branch:**
    ```bash
    git push origin --delete <branch_name> [cite: 2]
    git push origin -d <branch_name> # Shorthand [cite: 2]
    ```
* **Rename Remote Branch:**
    * This is a two-step process: rename local, push new, delete old remote. [cite: 2]
        ```bash
        git branch -m old_branch_name new_branch_name # Rename local [cite: 2]
        git push origin new_branch_name # Push the new branch [cite: 2]
        git push origin :old_branch_name # Delete the old branch on remote [cite: 2]
        ```

---

## 5. Branch Management & History Rewriting

* **Rebase:** Reapply your commits on top of another base tip. [cite: 2, 3]
    * Example: If `branch3` has commits on top of `master`, rebasing `branch3` onto `master` will move `branch3`'s unique commits to come after `master`'s latest commit, creating a linear history. [cite: 3]
        * Before: `master - 3 - 2 - 1` and `branch3 - 4 - 2 - 1` [cite: 3]
        * After `git rebase master` on `branch3`: `master - 3 - 2 - 1 - 4` [cite: 3]
    ```bash
    git rebase <base_branch_name> # While on your feature branch [cite: 2]
    ```
    * **Caution:** Never rebase a branch that has already been pushed and shared with others, as it rewrites history.

---

## 6. Project Distribution / Sharing

* **Archive Project as Zip:**
    ```bash
    git archive master --format=zip --output=../project_name.zip [cite: 1]
    ```
* **Create a Bundle (Portable Repository):**
    ```bash
    git bundle create ../repo.bundle master [cite: 1]
    ```

---

# Git Workflows by Role

This section outlines standard Git workflows for different roles within a team.

## Scenario 1: Developer Using a Fork Method (e.g., Open Source Contributions)

**Assumptions:** You have forked the `ORIGINAL_REPOSITORY` on GitHub/GitLab to `YOUR_FORK`. You have cloned `YOUR_FORK` locally.

**Workflow:**

1.  **Initial Setup (One-time):**
    * Fork the repository on the hosting platform (GitHub UI: click "Fork"). [cite: 1]
    * Clone your fork locally:
        ```bash
        git clone [https://github.com/YOUR_USERNAME/YOUR_FORK.git](https://github.com/YOUR_USERNAME/YOUR_FORK.git) [cite: 1]
        cd YOUR_FORK [cite: 1]
        ```
    * Add the original repository as an "upstream" remote: [cite: 1]
        ```bash
        git remote add upstream [https://github.com/ORIGINAL_OWNER/ORIGINAL_REPOSITORY.git](https://github.com/ORIGINAL_OWNER/ORIGINAL_REPOSITORY.git) [cite: 1]
        git remote -v # Verify remotes [cite: 1]
        ```

2.  **Start Working on a New Feature/Fix:**
    * **Sync your local `main` (or `master`) branch with the upstream:**
        ```bash
        git checkout main # or master [cite: 1]
        git fetch upstream [cite: 1]
        git merge upstream/main # or upstream/master [cite: 1]
        git push origin main # Optional: Push updated main to your fork
        ```
    * **Create a new feature branch from your updated `main` (or `master`):**
        ```bash
        git checkout -b feature/my-awesome-feature [cite: 2]
        ```

3.  **Develop & Commit:**
    * Make changes to your files.
    * Stage changes: `git add .` [cite: 1]
    * Commit changes: `git commit -m "feat: Add my awesome feature"` (use descriptive messages) [cite: 1]
    * Repeat `git add` and `git commit` as you make progress.

4.  **Push to Your Fork:**
    * Regularly push your feature branch to your fork on GitHub: [cite: 2]
        ```bash
        git push origin feature/my-awesome-feature [cite: 2]
        ```

5.  **Prepare for Pull Request (PR):**
    * **Before creating a PR, re-sync your feature branch (recommended for clean history):**
        ```bash
        git checkout feature/my-awesome-feature [cite: 2]
        git fetch upstream [cite: 1]
        git rebase upstream/main # or upstream/master [cite: 2]
        # Resolve any conflicts if they occur
        git push origin feature/my-awesome-feature --force # Force push after rebase (use with caution as it rewrites history, but necessary for a rebased branch if already pushed) [cite: 9]
        ```
    * Alternatively, you can `git merge upstream/main` into your feature branch, but `rebase` creates a cleaner, linear history.

6.  **Create Pull Request (PR):**
    * Go to your fork on GitHub. You should see a prompt to create a PR from your `feature/my-awesome-feature` branch to the `ORIGINAL_REPOSITORY`'s `main` (or `master`) branch.

7.  **Address PR Feedback:**
    * If changes are requested, make them in your local `feature/my-awesome-feature` branch.
    * Commit changes.
    * Push to your fork: `git push origin feature/my-awesome-feature`. The PR will automatically update.

8.  **Clean Up (After Merge):**
    * Once your PR is merged into the `ORIGINAL_REPOSITORY`, delete your local feature branch: [cite: 2]
        ```bash
        git checkout main # or master
        git branch -d feature/my-awesome-feature [cite: 2]
        ```
    * Delete the remote feature branch from your fork (optional, but good practice): [cite: 2]
        ```bash
        git push origin --delete feature/my-awesome-feature [cite: 2]
        ```

## Scenario 2: Developer in a Company Repo (Direct Push Access, Shared Repository)

**Assumptions:** You have direct read/write access to the main `COMPANY_REPO`. You will typically work on feature branches and then merge them via PRs (or direct merge by a lead).

**Workflow:**

1.  **Initial Setup:**
    * Clone the company repository:
        ```bash
        git clone [https://github.com/ORG_NAME/COMPANY_REPO.git](https://github.com/ORG_NAME/COMPANY_REPO.git)
        cd COMPANY_REPO
        ```

2.  **Start Working on a New Feature/Fix:**
    * **Ensure your local `main` (or `master`) branch is up-to-date:**
        ```bash
        git checkout main # or master [cite: 2]
        git pull origin main # or origin master [cite: 1]
        ```
    * **Create a new feature branch from your updated `main` (or `master`):**
        ```bash
        git checkout -b feature/my-new-task [cite: 2]
        ```

3.  **Develop & Commit:**
    * Make changes.
    * Stage and commit: `git add .` and `git commit -m "feat: Implement new user profile"` [cite: 1]

4.  **Push to Remote (Company Repo):**
    * Regularly push your feature branch to the central company repository: [cite: 2]
        ```bash
        git push origin feature/my-new-task [cite: 2]
        ```

5.  **Prepare for Pull Request (PR) / Merge:**
    * **Before opening a PR, ensure your branch is up-to-date with the main branch.** This minimizes merge conflicts for the team lead.
        ```bash
        git checkout feature/my-new-task [cite: 2]
        git fetch origin [cite: 1]
        git rebase origin/main # or origin/master (Recommended for clean history) [cite: 2]
        # OR: git merge origin/main # (If your team prefers merge commits)
        # Resolve any conflicts
        git push origin feature/my-new-task --force # If you rebased and already pushed [cite: 9]
        # OR: git push origin feature/my-new-task # If you merged or this is the first push after rebase
        ```

6.  **Create Pull Request (PR):**
    * Go to the company repo on GitHub/GitLab. Create a PR from your `feature/my-new-task` branch to `main` (or `master`).

7.  **Address PR Feedback:**
    * Make requested changes, commit, and push. The PR will update automatically.

8.  **Clean Up (After Merge):**
    * Once your PR is merged, delete your local feature branch: [cite: 2]
        ```bash
        git checkout main # or master
        git branch -d feature/my-new-task [cite: 2]
        ```
    * Delete the remote feature branch (if allowed/expected by team policy): [cite: 2]
        ```bash
        git push origin --delete feature/my-new-task [cite: 2]
        ```

## Scenario 3: Repository Owner / Team Leader Workflow (Direct Push Access)

**Assumptions:** You own or manage the `COMPANY_REPO`. You're responsible for reviewing, merging, and maintaining the main branches.

**Workflow:**

1.  **Initial Setup:**
    * Clone the repository:
        ```bash
        git clone [https://github.com/ORG_NAME/COMPANY_REPO.git](https://github.com/ORG_NAME/COMPANY_REPO.git)
        cd COMPANY_REPO
        ```

2.  **Regular Maintenance & Updates:**
    * **Stay updated on `main` (or `master`):**
        ```bash
        git checkout main # or master [cite: 2]
        git pull origin main # Ensure your local main is always current [cite: 1]
        ```
    * **Review Pull Requests (PRs):**
        * On GitHub/GitLab, review incoming PRs. Provide feedback.
        * To review a PR locally (often helpful for testing):
            ```bash
            # Assuming PR is from 'username/repo' and branch 'feature-branch'
            git fetch origin pull/PR_NUMBER/head:pr-branch-name
            git checkout pr-branch-name
            ```
            (The exact fetch command might vary slightly between platforms; GitHub provides it in the PR details).
            * Test the code, then `git checkout main` to return to your main branch when done.

3.  **Merging Pull Requests:**
    * **On the hosting platform (Recommended):** Use GitHub's "Merge Pull Request" button. This often offers options like "Create a merge commit," "Squash and merge," or "Rebase and merge." Choose based on team policy.
    * **From CLI (Less Common for PRs, but possible for direct merges):**
        * Ensure your `main` (or `master`) branch is clean and up-to-date:
            ```bash
            git checkout main [cite: 2]
            git pull origin main [cite: 1]
            ```
        * Merge the feature branch into `main`: [cite: 1]
            ```bash
            git merge <feature_branch_name> [cite: 1]
            # Resolve conflicts if any
            git push origin main # Push the merged changes to the remote [cite: 8]
            ```
        * *Alternatively, if using `rebase` for linearity (careful with shared branches!):*
            ```bash
            git checkout <feature_branch_name> [cite: 2]
            git rebase main [cite: 2]
            git checkout main [cite: 2]
            git merge <feature_branch_name> # This will be a fast-forward merge [cite: 1]
            git push origin main [cite: 8]
            ```

4.  **Branch Management (Team Lead):**
    * **Creating Release Branches:**
        ```bash
        git checkout -b release/1.0 main # Create release branch from main [cite: 2]
        git push origin release/1.0 # Push to remote [cite: 8]
        ```
    * **Hotfix Branches:**
        ```bash
        git checkout -b hotfix/bug-fix-critical main # Or from a release branch [cite: 2]
        # Make fix, commit, push
        # Merge hotfix into main (and release branch if applicable)
        ```
    * **Deleting Merged Branches:**
        * Encourage developers to delete their remote branches after merging.
        * You can also manually delete remote branches: [cite: 2]
            ```bash
            git push origin --delete <branch_name> [cite: 2]
            ```
    * **Merging Feature branches into `main` (when developers aren't using PRs, less common in modern workflows):**
        * A team lead would switch to the master/main branch and then merge a feature branch into it. [cite: 1]
