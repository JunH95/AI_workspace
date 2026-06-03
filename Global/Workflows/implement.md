---
description: Use this skill to execute tasks listed in the implementation plan. It enforces Test-Driven Development (TDD) or strict incremental coding, ensuring clean code principles and quality alignment.
---

---

## 1. Protocol

### Step 1: Test-First Setup (If Applicable)
1. If the project configuration allows, design a failing test case (Red) representing the success criteria defined in the plan.
2. Verify the framework tools required to execute the test suite are available in the workspace.

### Step 2: Incremental Code Generation
1. Write the minimal code required to pass the test or fulfill the current task block.
2. Adhere strictly to the 20-line function limit: any function exceeding 20 lines must be split into atomic sub-functions.
3. Use English for all syntax, variable names, and types, but **write all inline comments (#) and docstrings in Korean** for native readability.

### Step 3: Validation Run
1. Run the test suite or verification script.
2. If errors occur, do not overwrite the entire file; isolate and output only the modified components.

---

## 2. Constraints
1. Absolute No Emojis: Ensure zero emojis are embedded in code strings, print literals, or comments to avoid cp949 encoding crashes on Windows.
2. No Lazy Placeholders: Do not emit short-cut comments like `// rest remains the same`. Write complete, runnable code blocks.