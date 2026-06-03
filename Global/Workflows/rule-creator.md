---
description: Analyzes the target project's environment (languages, packages, configuration files) to intelligently draft and generate a tailored local rule file (`rule_local.md`) containing custom behavior controls and quality standards. Use this skill at the initiation of a new project or when significant tech stack changes occur.
---

# Project Rule Creator Workflow

> A specialized workflow that inspects a local workspace to dynamically generate custom behavior rules (`rule_local.md`) tailored to the specific technology stack, directory layout, and typical AI pitfalls of that project.

---

## 1. Protocol

### Step 1: Tech Stack & Environment Discovery
1. Silently inspect the current repository structure. Check for specific markers:
   - Python: `requirements.txt`, `pyproject.toml`, `setup.py`, `environment.yml`
   - JavaScript/TypeScript: `package.json`, `tsconfig.json`
   - C# / Unity: `.sln`, `Assets/` directory, Assembly Definition files
   - Java/Kotlin: `build.gradle`, `pom.xml`
2. Identify the core frameworks, libraries, and runtime versions (e.g., PyTorch, React, Next.js, Pandas, FastAPI).
3. Analyze the directory structure to understand standard conventions used in the codebase (e.g., `src/`, `notebooks/`, `tests/`, `components/`).

### Step 2: Trap Mapping (Pitfall Identification)
1. Based on the discovered stack, identify at least 3-5 well-known AI code generation failures, deprecation traps, or design issues.
   - *Example (Data Science):* Failing to set random seeds (`numpy`, `torch`, `random`), Pandas `SettingWithCopyWarning`, GPU/CPU device mismatch.
   - *Example (React/Next.js):* Client vs Server component mismatches, React hook stale closures, ignoring absolute import structures.
   - *Example (Unity):* Accessing GameObjects in loops, ignoring serialization attributes, using standard C# events instead of UnityEvents.

### Step 3: Draft Local Rule Ledger (`rule_local.md`)
1. Create a structured custom rules file: `.ai/Rules/rule_local.md` (or local equivalent path).
2. The file MUST follow this exact structure:
   - # Local Project Rules: [Project Name / Domain]
   - > [Summary: Specific execution boundary and purpose of these rules]
   - ## 1. Tech Stack Boundaries (Discovered frameworks & targets)
   - ## 2. Core Quality Controls (Specific lint rules, typing, structure)
   - ## 3. AI Hallucination Guardrails (Pitfalls identified in Step 2 with explicit rules to prevent them)
   - ## 4. Test & Verification Guidelines (Standard testing framework and commands)
3. Ensure absolutely **NO emojis** are used in the generated rule file.
4. Explanations inside the file must be in English for LLM performance, with brief Korean context comments if helpful.

### Step 4: Gatekeeper Finalization
1. Inform the user of the discovered stack and present the generated `.ai/Rules/rule_local.md` content.
2. Verify that the rule file is safely saved in the local project's rules directory, ensuring it does not pollute the global `ai_workspace` folder.

---

## 2. Constraints
1. **No Global Pollution:** Never write local rules into the global `Global/Rules/` directory. They must remain strictly localized to the target project.
2. **Context Efficiency:** Do not create massive rules. Focus on 3-5 high-impact, actionable behavioral constraints that prevent recurring local errors.
3. **No-Emoji Enforcement:** Maintain a clean, professional, emoji-free format to prevent cp949 encoding crashes in Windows terminals.
