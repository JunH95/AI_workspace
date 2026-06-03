---
description: Use this skill at the beginning of a project or during critical mid-project pivots. It enforces a strict requirements-gathering interview, prevents immediate coding, and challenges architectural assumptions to uncover edge cases.
---

---

## 1. Protocol

### Step 1: Divergent Interview (Max 10-15 Questions)
1. Do not write any production code immediately. 
2. Formulate a list of critical technical questions tailored to the user's domain (e.g., data pipeline scaling, model constraints, UI states).
3. Group these questions and ask the user 2-3 items at a time to avoid cognitive overload.

### Step 2: Anti-Gaslighting & Blindspot Analysis
1. Critically evaluate the user's initial proposal. Do not blindly agree.
2. Identify at least 3 potential architectural risks or edge cases (e.g., memory bottlenecks, API rate limits, encoding mismatches).
3. Propose alternative design patterns or mitigating strategies.

### Step 3: Requirement Artifact Generation
1. Consolidate the discussion into a structured markdown document: `.ai/docs/requirements.md`.
2. Include Scope, Tech Stack, Constraints, and Success Criteria.
3. End turn and wait for the user to explicitly type "APPROVE" or "PROCEED" before moving to the planning stage.

---

## 2. Constraints
1. Absolute No Emojis: No emojis are allowed in any generated documentation, interview queries, or logs.
2. Non-Narrow Thinking: Ensure instructions focus on generalized engineering practices rather than over-indexing on specific code snippets.