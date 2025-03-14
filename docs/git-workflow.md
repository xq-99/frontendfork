# Git Workflow Guide

This document explains the Git workflow we follow in the project to ensure consistency, smooth collaboration, and easy management of code.

## Branching Model

We use the following Git branching model:

### 1. **Main Branch (`main`)**

- This is the **stable** branch where the **production-ready** code lives.
- Only **tested and reviewed** code should be merged into `main`.
- Merges to `main` should be done using **Pull Requests** (PRs) after thorough code review.

### 2. **Development Branch (`dev`)**

- The `dev` branch is the **integration branch** where all features and fixes are tested together before they go into `main`.
- This branch is used to collect features and bug fixes for the upcoming release.
- Merges into `dev` should also happen via **Pull Requests**.

### 3. **Feature Branches (`feature/<name>`)**

- These branches are used to develop new features or functionality.
- Always branch off from the latest `dev` branch.
- The branch name should be descriptive and reflect the task or feature being worked on.
  
  Example:
  ```bash
  git checkout -b feature/user-authentication dev
  ```

- When the feature is complete, create a **Pull Request** to merge it back into `dev`. Make sure your branch is **up-to-date** with `dev` before opening a PR.

### 4. **Bugfix Branches (`bugfix/<name>`)**

- These branches are used for fixing bugs or issues that arise during development or in production.
- Just like with feature branches, branch off from `dev`, and the branch name should reflect the issue being fixed.
  
  Example:
  ```bash
  git checkout -b bugfix/fix-login-error dev
  ```

### 5. **Hotfix Branches (`hotfix/<name>`)**

- Hotfixes are **urgent fixes** that need to be applied directly to `main`.
- Create a `hotfix` branch from `main` and then merge it back to both `main` and `dev`.
  
  Example:
  ```bash
  git checkout -b hotfix/fix-critical-bug main
  ```

---

## Commit Message Guidelines

Each commit should have a **clear, concise** message that describes what was done.

### Format:
```
<type>(<scope>): <subject>

<body>

<footer>
```

- **type**: Indicates the purpose of the commit (e.g., `feat`, `fix`, `docs`, `chore`, etc.).
- **scope**: A short description of what part of the code the commit affects (e.g., `auth`, `api`, `ui`).
- **subject**: A concise description of what the commit does. Start with a **verb** (e.g., "Add", "Fix", "Refactor").
- **body** (optional): A more detailed explanation of what was done, why, and how.
- **footer** (optional): Includes additional information like issue references (e.g., `Closes #123`).

### Example Commit Messages:

- `feat(auth): add JWT authentication`
- `fix(api): handle 500 errors`
- `docs: update README with setup instructions`
- `chore: clean up unused imports`

---

## Pull Requests (PRs)

- All changes to `dev` or `main` must go through **Pull Requests**.
- PRs should be as **small and focused** as possible. Try to break down large changes into smaller tasks and PRs.
- **PR Description**: Always include a detailed description of the changes made, what problem is being solved, and any relevant information.
- **Review Process**: At least one team member should review the PR before merging. Any necessary changes should be addressed.
- **Merge Strategy**: Prefer **Squash and Merge** for a cleaner commit history. Avoid using "Merge Commit" unless necessary.

---

## Rebase vs. Merge

- **Rebase** your feature branch with `dev` before opening a Pull Request to ensure that your branch is up-to-date.
  
  Example:
  ```bash
  git checkout feature/user-authentication
  git fetch origin
  git rebase origin/dev
  ```

- **Merge** is acceptable when resolving conflicts, but we prefer rebasing to keep a linear history.

---

## GitHub Actions

Every time code is pushed to `dev` or `main`, our GitHub Actions will run automated tests and checks to ensure that nothing is broken before merging.

If tests fail, please fix them before proceeding.

---

## Summary of Branches

| Branch      | Description                                  |
|-------------|----------------------------------------------|
| `main`      | Stable production-ready code                 |
| `dev`       | Integration branch for testing and merging   |
| `feature/*` | For developing new features                  |
| `bugfix/*`  | For fixing bugs or issues                    |
| `hotfix/*`  | For urgent fixes in production               |

---

This workflow will ensure that we maintain **clean code** and **smooth collaboration** throughout the project. Feel free to ask questions if you're unsure about any part of the process!
