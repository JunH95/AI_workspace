# Repository Governance Rule: Gemini Instructions

> [Meta-Controller: The highest-priority configuration management guidelines Gemini MUST adhere to when maintaining the `ai_workspace` repository, expanding subdirectories, and creating/modifying contexts (Agents, Skills, Docs).]

---

## 1. Scope & Boundaries (Separation of Roles)

1. **Delegation of Daily Behavior:** Routine coding styles, tone constraints, and debugging processes are delegated to `Rules/global_rules.md`.
2. **Repository Meta-Control:** This file (`GEMINI.md`) acts as the meta-controller ensuring standard specification, quality, and structural integrity when generating or refactoring Markdown assets in this repository.

## 2. Artifact Generation & Expansion Standards

When the user requests to create or update specifications, Gemini MUST satisfy the following quality criteria based on the target directory:

### Agents/ (Persona Specifications)
* **Purpose:** Define specific roles specialized in technology stacks (e.g., Pandas, PyTorch) or domains.
* **Requirements:** Clearly specify the persona, scope of work, and runtime guidelines to prevent blind code generation and encourage autonomous reasoning.

### Skills/ (Procedural Workflows)
* **Purpose:** Define task-centric architecture (e.g., data cleaning, model validation).
* **Requirements:** Structurally describe the pipeline connecting Input, Process (Step-by-step), and Output formats.

### Docs/ (Knowledge & Study Hub)
* **Purpose:** Archive AI feature manuals, prompt engineering study notes, and architectural theory learned during conversations.
* **Requirements:** Document concepts clearly with examples. **CRITICAL:** All documentation MUST include explicit URLs or references to official documentation or verified sources to guarantee reliability and prevent hallucination.

## 3. Strict Constraints & Language Policy

1. **Strict Language Routing (CRITICAL):**
   - **System Assets (`Agents/`, `Skills/`, `Rules/`, `GEMINI.md`):** MUST be written entirely in **English** to maximize token efficiency and instruction-following performance of the LLM.
   - **Human-Facing Assets (`README.md`, `Docs/`):** MUST be written in **Korean** for the user's readability and study purposes.
2. **No Visual Elements (No Emojis/Emoticons):** Strictly prohibit the use of emojis and emoticons in all Markdown texts and comments to maintain professional engineering documentation standards.
3. **Model-Agnostic Design:** Maintain standard Markdown specifications, excluding platform-specific syntax, so the context is instantly interpretable if migrated to other LLMs (Claude, GPT, etc.).
4. **Professional Tone:** Maintain an objective, concise, and professional engineering tone.
5. **No Sensitive Information:** Ensure API Keys, tokens, passwords, or PII (e.g., local directory usernames) are never hardcoded.

## 4. Repository Management & Pipeline

Gemini MUST NOT arbitrarily modify files. All asset management MUST strictly follow this 5-step pipeline:

1. **Asset Analysis:** Scan existing directories (`Agents/`, `Skills/`, `Rules/`, `Docs/`) to map relationships and diagnose potential conflicts.
2. **Proactive Documentation (Continuous Evolution):** If the user asks about or learns a new AI concept/feature during the session, Gemini SHOULD proactively suggest documenting it in the `Docs/` directory.
3. **Change Briefing (Plan Before Action):** Before creating or refactoring modules, Gemini MUST brief the user on the purpose and core architecture, and obtain **explicit approval**.
4. **Atomic Update:** Upon approval, compile the Markdown assets according to the standard format. Keep the `README.md` directory structure synchronized.
5. **Independence:** Design each Markdown file to minimize interdependencies so it can run autonomously when loaded individually.

---

## 5. Standard Output Format (Template)

When designing new Agents and Skills, Gemini MUST expand upon the following architectural template to guarantee consistency:

```markdown
# [Clear Component Title]

> [One-line summary: Define the physical runtime role and target of this file]

---

## 1. Definition & Role
- Detailed description of responsibilities and goals...

## 2. Execution Pipeline
- Step-by-step procedural logic...

## 3. Constraints
- Prohibited actions, exception handling rules, architectural limits...
```