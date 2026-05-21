# Skill Generator

> A meta-workflow that automatically generates structured and security-enhanced new Skill specification files (.md) conforming to the repository governance standards.

---

## 1. Definition & Role
- Designs and outputs a new Skill specification to be applied to a specific technical domain or automation task requested by the user, conforming to the specifications of the top-level management guidelines (`GEMINI.md`) and global rules (`Rules/global_rules.md`).
- Minimizes the effort of developers who have to write rules from scratch, and serves to consistently produce outputs with a token-efficient markdown architecture optimized for AI comprehension.

## 2. Execution Pipeline
1. **Requirements Analysis and Abstraction:** Define the target of the skill the user wants to create (e.g., unit test generation, code refactoring) and its core automation objective.
2. **Context Mapping:** Map the behavioral constraints stipulated in the top-level `GEMINI.md` (prohibition of emojis, model-agnostic design, prohibition of exposing sensitive information, etc.) and the standard output format.
3. **Compile Skill Specification:** Combine the analyzed requirements and mapped specifications to output the final markdown file content as a complete code block conforming to the standard template below.

### [Standard Output Template Example]
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

## 3. Constraints
1. **Strict Adherence to Structural Specifications:** All generated subordinate skill files MUST strictly adhere to the 3-tier structure of Definition & Role, Execution Pipeline, and Constraints, and sections cannot be arbitrarily reduced or altered.
2. **Mandatory Inheritance of Hardening Defense Mechanisms:** The newly generated skill MUST explicitly include specific constraints (prohibition of arbitrary omissions, verification of real APIs, incremental modification principle, etc.) capable of controlling the AI's chronic mistakes, tailored to the nature of the task.
3. **Injection of Security Constraints:** It MUST forcefully include security guidelines that prevent sensitive information, such as API Keys, tokens, credentials, or local absolute paths containing user accounts, from being hardcoded within the source code during the utilization of the generated skill.