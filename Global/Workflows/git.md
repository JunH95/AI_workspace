---
description: Automatically stages all local changes, generates a highly descriptive Conventional Commit message in English based on git diff, commits the changes, and pushes directly to the remote main/master branch without user confirmation. Use this skill when the user wants to quickly save and push their work in a personal/solo project context.
---

# Solo Git Automation Workflow

> A fully automated pipeline that executes git add, commit, and push in a single sequence without requiring user confirmation, specialized for solo development.

---

## 1. Protocol

### Step 1: Status Discovery
1. Run `git status` to identify modified, untracked, or deleted files.
2. If there are no local changes, output "No local changes to commit." and terminate the workflow immediately.

### Step 2: Diff Analysis
1. Run `git diff` for tracked changes, and inspect the content of untracked files to understand the modifications.
2. Analyze the changes to determine the primary intent of the session (e.g., feature addition, bug fix, documentation update, refactoring).

### Step 3: Conventional Commit Generation
1. Formulate a precise, concise, and professional commit message in **English** following the Conventional Commits specification.
2. The format MUST be: `<type>(<scope>): <short description in lowercase>`
   - **Allowed Types:**
     - `feat`: A new feature
     - `fix`: A bug fix
     - `docs`: Documentation changes
     - `style`: Formatting, missing semi-colons, etc. (no production code changes)
     - `refactor`: Refactoring production code (neither fixes a bug nor adds a feature)
     - `test`: Adding missing tests or correcting existing tests
     - `chore`: Updating build tasks, package manager configs, etc. (no production code changes)
   - **Scope:** Optional. Use it to specify the module or component changed (e.g., `feat(dataloader): add PyTorch custom dataset`).
   - **Subject:** A brief summary in English, in lowercase, starting with a verb in the present tense (e.g., `add custom pandas loader`, `fix cp949 encoding crash`).
3. Ensure absolutely **NO emojis** are used in the commit message or the subject to prevent Windows terminal encoding errors.

### Step 4: Execute Staging & Committing
1. Stage all local changes by running `git add -A` (or `git add .` as appropriate).
2. Execute the commit using the generated message: `git commit -m "<commit_message>"`

### Step 5: Execute Push
1. Identify the current active branch by running `git branch --show-current`.
2. Push the committed changes directly to the remote tracking branch (e.g., `git push origin <branch_name>`).
3. Confirm successful execution by outputting the terminal execution log.

---

## 2. Constraints
1. **Unattended Execution:** Do NOT pause to ask for user approval or confirm the commit message. Proceed directly to push.
2. **Strict No-Emoji:** Absolutely no emojis are allowed in the generated commit messages or any terminal outputs to maintain compatibility with Windows environments.
3. **English Commit Messages:** All commit messages MUST be written in English for repository governance, even if explanations in chat are in Korean.
