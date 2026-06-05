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
1. Do NOT create or write to any files. Present the comprehensive architectural overview directly in the chat window.
2. Follow this exact structure in the chat output:
   - # Project Overview
   - ## Tech Stack & Dependencies
   - ## Directory Tree & Key Modules Description
   - ## Execution & Setup Guide (How to run)
   - ## Architectural Observations (Potential bottlenecks or structural notes)
3. Ask the user for the next immediate task.

---

## 2. Constraints
1. Absolute No Emojis: Strictly forbidden within any chat outputs or terminal logs.
2. Strictly Read-Only (CRITICAL): You are strictly FORBIDDEN from creating new files, writing to the filesystem, or modifying any existing source code. This workflow is completely read-only, designed solely for context-priming.