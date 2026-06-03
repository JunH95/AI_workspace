---
description: Use this skill when introduced to a new, unfamiliar repository or complex codebase. It systematically analyzes the tech stack, directory structure, and entry points to generate an architectural overview without wasting context tokens.
---

---

## 1. Protocol

### Step 1: Structural Discovery & Tech Stack Audit
1. Never read all source files sequentially.
2. Run high-level discovery commands (e.g., recursive file listing) and locate configuration files like `requirements.txt`, `package.json`, `setup.py`, or `Dockerfile`.
3. Identify the core language, framework versions, and external package dependencies.

### Step 2: Entry Point & Core Flow Mapping
1. Locate the main execution entry points (e.g., `main.py`, `app.py`, `src/index.ts`).
2. Trace the high-level data flow and identify key modules (e.g., data loaders, model definitions, API handlers, utility suites).

### Step 3: Project Overview Generation
1. Consolidate findings into a comprehensive markdown document: `docs/project_overview.md`.
2. Follow this exact structure:
   - # Project Overview
   - ## Tech Stack & Dependencies
   - ## Directory Tree & Key Modules Description
   - ## Execution & Setup Guide (How to run)
   - ## Architectural Observations (Potential bottlenecks or structural notes)
3. Present a high-level summary of the generated file to the user and ask for the next immediate task.

---

## 2. Constraints
1. Absolute No Emojis: Strictly forbidden within `docs/project_overview.md` or any terminal summary outputs.
2. Zero Overwriting: Do not alter, modify, or refactor any existing source code during this analysis workflow.