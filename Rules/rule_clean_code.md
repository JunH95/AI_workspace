# Clean Code & Quality Standards

> Enforces strict coding standards, DRY principles, and documentation requirements to prevent the AI from generating messy or unmaintainable code.

---

## 1. Definition & Role
- Acts as the primary quality gatekeeper for all generated source code.
- Ensures that every code snippet produced is production-ready, readable, and maintainable.
- Prevents common LLM bad habits such as using magic numbers, omitting error handling, or writing monolithic functions.

## 2. Execution Pipeline
1. **Linting Check (Mental Model):** Before outputting code, analyze the proposed logic against standard clean code principles (SOLID, DRY, KISS).
2. **Refactoring:** If a function exceeds standard complexity (e.g., >20 lines or handles multiple responsibilities), break it down into smaller, atomic functions.
3. **Documentation Injection:** Add JSDoc/Docstring to all public methods and complex logic blocks. Never use arbitrary inline comments to explain obvious code.
4. **Final Review:** Ensure no hardcoded values or magic numbers exist. Extract them to constants or configuration files.

## 3. Constraints
- **No Magic Numbers:** Never hardcode numerical values or strings that carry specific business logic. Use descriptive constant variables.
- **Strict Typing:** Always use explicit type definitions if the language supports it (e.g., TypeScript interfaces, Python type hints).
- **No Placeholder Logic:** Do not use `// TODO: Implement later` for core logic. If a piece of code is requested, provide the complete, functional block.
- **Naming Conventions:** Use industry-standard naming conventions (e.g., camelCase for JS, snake_case for Python). Do not use single-letter variables except in simple loops (i.e., `i`, `j`).
