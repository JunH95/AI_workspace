# Project Initialization Pipeline

> A scaffolding skill that sets up a new local project environment based on the PM Agent's domain decisions, migrating necessary global Agents, Skills, and domain-specific Rules into a `.ai` directory.

---

## 1. Definition & Role
- **Dynamic Bootstrapper:** Prepares a codebase to become an AI-aware environment by injecting ONLY the necessary assets based on the project's domain (e.g., Web, Data Science).
- **Context Isolator:** Prevents global context contamination by physically segregating the scoped Agents, Skills, and local Rules into the target project's `.ai` subdirectory.

## 2. Execution Pipeline
1. **Parameter Gathering:** 
   - Ask the user for the absolute path of the new target project.
   - Ask the user for the Target Domain (e.g., "Data Science", "React Frontend", "General") decided during the PM Agent meeting.
2. **Directory Scaffolding:** Execute shell commands to create the structure inside the target project:
   - `<target_project>\.ai\Agents`
   - `<target_project>\.ai\Skills`
   - `<target_project>\.ai\Rules`
3. **Selective Asset Migration:** Execute shell commands (`Copy-Item`) to copy:
   - Global Core Agents: `c:\dev\ai_workspace\Agents\*` -> `.ai\Agents`
   - Global Core Skills: `c:\dev\ai_workspace\Skills\*` -> `.ai\Skills`
   - Domain-Specific Rules (if matched): `c:\dev\ai_workspace\Rules\Domains\<TargetDomain>\*` -> `.ai\Rules`
4. **Verification:** Verify that the files were successfully copied and confirm readiness.

## 3. Constraints
- **System Isolation:** NEVER copy the `System\` directory. Those are meta-tools strictly reserved for the `ai_workspace` master repository.
- **Global Rule Exclusion:** Do NOT copy `rule_global.md` as it is natively injected via IDE Customizations.
- **Non-Destructive:** NEVER overwrite existing `.ai` directories in the target project without explicit user confirmation.
- **Absolute Paths Required:** Always use absolute file paths in shell commands to prevent accidental copying to incorrect relative directories.
