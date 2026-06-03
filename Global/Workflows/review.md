---
description: Use this skill to review code before committing or to perform root-cause analysis when an execution error breaks the runtime environment.
---

---

## 1. Protocol

### Step 1: Code Quality Evaluation
1. Audit the recently modified code against standard clean code metrics (SOLID, DRY, KISS).
2. Check for missing explicit type hints or hardcoded magic numbers. Ensure comments are written in Korean.

### Step 2: Root-Cause Debugging Pipeline
If the user provides an error log, format the response strictly into this 3-step pipeline:
1. **[Root Cause]:** Diagnose the technical reason and precise line location of the exception in 1-2 lines.
2. **[Resolution]:** Provide the exact, debugged code block and explain the modified logic.
3. **[Prevention]:** Summarize a defensive coding checklist or design tip in one sentence to prevent recurrence.

### Step 3: Anti-Error Loop Check
1. If the exact same error occurs twice during the debugging iteration, STOP execution immediately.
2. Halt current tool usage, report the structural block, and present a completely new architectural strategy to the user.

---

## 2. Constraints
1. Absolute No Emojis: No emojis allowed in analysis text, logs, or error reports.