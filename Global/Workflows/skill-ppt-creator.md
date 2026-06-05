---
description: Inspects local project artifacts to logically audit the project outcomes, drafts a beautifully styled presentation in Marp Markdown, and compiles it into a high-quality PPTX file after user approval. Use this skill at the end of a project to create final presentations.
---

# PPT Presentation Creator Workflow

> A structured workflow that audits project outcomes for logical consistency, designs adaptive presentation slides using Marp CSS, and compiles them into a premium PowerPoint (.pptx) file.

---

## 1. Protocol

### Step 1: Project Audit & Logical Self-Verification
1. Scan the local workspace (especially `.ai/docs/requirements.md`, `.ai/docs/implementation_plan.md`, `reports/`, and code files) to extract the complete timeline and key results.
2. Formulate the core narrative logic adapting to the project's unique nature (e.g., Context ➔ Challenge ➔ Method ➔ Results ➔ Conclusion).
3. Perform a **Logical Self-Verification Check**:
   - Do the final results mathematically and logically support the initial project objectives?
   - Is there any contradiction in the methodology explained vs the code implemented?
   - Are there missing logical transitions?
   - *If gaps are found, call them out to the user and request clarification before drafting slides.*

### Step 2: Visual Assets Mapping
1. Identify all generated data visualization images (e.g., `.png`, `.jpg` plots under `reports/` or `docs/`) and note their file paths.
2. Determine if additional logical visualizations (e.g., system architecture, data preprocessing flow) are needed. If so, draft them using Mermaid syntax.
3. If critical visualization data is missing, explicitly prompt the user: *"Please run the visualization script or provide [X] chart to maximize presentation quality."*

### Step 3: Draft Marp Slides & Present (Gatekeeper Block)
1. Write the presentation markup using Marp Markdown syntax, saving it to `.ai/docs/slides.md`.
2. Apply premium modern design parameters in Marp configurations:
   - Use curated color palettes (e.g., dark modes, smooth gradients, sleek HSL tailwinds).
   - Leverage Marp layout directives (e.g., columns, grids, header/footer controls).
   - Embed the visual assets mapped in Step 2.
3. Present the slide-by-slide outline and main textual content in the chat.
4. **CRITICAL:** End your turn immediately and wait for the user's explicit "APPROVE" or "PROCEED" before executing compilation.

### Step 4: Compile to PPTX
1. Once approved, execute the Marp CLI compilation tool using `npx`:
   `npx -y @marp-team/marp-cli .ai/docs/slides.md --pptx -o output_presentation.pptx`
2. Confirm the successful generation and provide the absolute path to the output `.pptx` file.

---

## 2. Constraints
1. **Strict No-Emoji:** Prohibit emojis in slide content, markdown files, and terminal logs to prevent Windows cp949 rendering crashes.
2. **Strict Approval:** Under no circumstances should you run the `npx marp-cli` compilation command before the user explicitly approves the slide draft in Step 3.
3. **Logical Integrity:** Every claim in the slides must trace back to verifiable code execution or data results present in the workspace. No fictional metrics.
