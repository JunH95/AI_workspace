---
description: Performs a comprehensive refactoring of Python and Data Science projects. Cleans up unused files/folders after user approval, modularizes codebase, enforces PEP 8 styling, and documents all functions with detailed Korean docstrings. Use this skill when a project has grown chaotic and needs professional restructuring.
---

# Python & Data Science Refactoring Workflow

> A structured workflow designed to clean up redundant directory structures, monolithic scripts, enforce Python PEP 8 standards, and generate friendly Korean docstrings for ML/DL projects.

---

## 1. Protocol

### Step 1: Auditing & Cleaning Proposal (Gatekeeper Block)
1. Scan the repository for redundant, duplicate, temporary, or cache files (e.g., `__pycache__/`, `.ipynb_checkpoints/`, old `.csv` backups, debug scripts).
2. Scan the source code to identify:
   - Monolithic functions (exceeding 30 lines) that need extraction.
   - Hardcoded hyperparameters, directory paths, or magic numbers.
   - Lack of random seed locking (`numpy`, `random`, `torch`) which violates reproducibility.
3. Propose a detailed **Cleanup & Refactoring Plan** to the user.
   - **CRITICAL:** Output the list of files/directories proposed for deletion or relocation.
   - **CRITICAL:** End your turn immediately and wait for the user's explicit "APPROVE" or "PROCEED" before executing any filesystem mutations.

### Step 2: Structure Cleanup
1. Once approved, execute the filesystem cleanup using terminal command tools (e.g., `Remove-Item` on Windows).
2. Reorganize files into standard layouts (e.g., putting raw data in `data/`, training scripts in `src/`, EDA in `notebooks/`).

### Step 3: PEP 8 & Modularization Execution
1. Refactor python scripts to adhere to **PEP 8** style guidelines (variable naming in snake_case, correct imports ordering).
2. Extract monolithic functions into smaller, single-responsibility functions (under 20-30 lines).
3. Parameterize hardcoded configurations (extract variables to a central `config` dictionary or `.yaml` file).
4. Implement standard reproducibility locks (e.g., `set_seed()` function locking `torch`, `np.random`, and python `random` seeds).

### Step 4: Friendly Korean Docstrings Generation
1. Write detailed Google-style or NumPy-style docstrings for all functions and classes.
2. The docstrings MUST be written in **Korean** and strictly document:
   - `설명 (Description):` What the function does in clear, friendly Korean.
   - `매개변수 (Args):` Type and description of each parameter in Korean.
   - `반환값 (Returns):` Type and description of the returned values in Korean.
   - `예외 (Raises):` Possible exceptions raised.

### Step 5: Verification & Walkthrough
1. Run the test suite or verify the refactored code by dry-running the scripts.
2. Present a clean walkthrough of the changes made, explaining the modularized structure.

---

## 2. Constraints
1. **Strict No-Emoji:** Absolutely no emojis allowed in code, comments, or terminal outputs to avoid Windows cp949 encoding crashes.
2. **Approval Gate:** Never delete files or move folders without presenting the list and obtaining explicit user confirmation in Step 1.
3. **No Overwriting Failures:** Ensure backup configurations are checked if refactoring critical pipelines, keeping original code runnable.
