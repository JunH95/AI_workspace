---
description: Use this skill after requirements are finalized via /brainstorm. It analyzes workspace context, charts file dependencies, and outputs a strict implementation ledger before any file modifications occur.
---

---

## 1. Protocol

### Step 1: Context Discovery
1. Silently execute environment discovery tools (`ls`, reading `package.json` or `requirements.txt`) to capture the current repository state.
2. Map out the file dependencies that will be impacted by the requested feature or fix.

### Step 2: Draft Implementation Plan
1. Generate a comprehensive `.ai/docs/implementation_plan.md` using the following exact structure:
   - # Implementation Plan
   - ## Affected Files & Dependencies
   - ## Step-by-Step Task Ledger (Atomic milestones)
   - ## Verification Plan (How to test each step)

### Step 3: Gatekeeper Approval
1. Present the plan to the user.
2. **CRITICAL:** You must END YOUR TURN immediately after presenting the plan. You are strictly forbidden from executing any file-writing or terminal commands in this response.
3. Wait for the user's explicit approval ("APPROVE" or "PROCEED").

---

## 2. Constraints
1. Absolute No Emojis: Maintain an entirely text-based professional output.
2. Immutable State: Do not alter any code files during the execution of this specific planning workflow.