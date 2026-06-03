---
description: Create new skills, modify and improve existing skills, and measure skill performance. Use this skill whenever you need to design an automated workflow from scratch, optimize triggering descriptions, or run quantitative and qualitative evaluations on agent behaviors. Make sure to use this skill whenever the user wants to turn a repeated chat routine into a permanent automation artifact.
---

---

## 1. Protocol

### Step 1: Capture Intent & Interview
1. Extract answers from the conversation history regarding the user's goal, required tools, and sequence of steps.
2. Proactively ask clarifying questions about edge cases, input/output formats, and success criteria before writing code.
3. Identify whether the output is objective (verifiable via test cases) or subjective to determine evaluation defaults.

### Step 2: Draft SKILL.md
1. Generate the skill with exact components: name, description, and markdown instructions.
2. Write "pushy" descriptions to prevent under-triggering, explicitly stating target contexts where this skill must win.
3. Explain the reasoning ("why") behind instructions to leverage the model's theory of mind, avoiding heavy-handed constraints.

### Step 3: Test Case Setup & Baseline Runs
1. Create 2-3 realistic test prompts based on actual user scenarios and save them to evals/evals.json.
2. Execute parallel runs for both the with-skill configuration and the baseline configuration (without_skill or old_skill snapshot).
3. Capture runtime metrics including total_tokens and duration_ms immediately upon completion and save to timing.json.

### Step 4: Evaluate & Aggregate
1. Draft objective assertions while runs are in progress and update eval_metadata.json.
2. Grade each run using programmatic scripts, ensuring the grading.json schema uses text, passed, and evidence fields.
3. Run the benchmark aggregation script to generate benchmark.json and benchmark.md with mean and delta metrics.
4. Launch the static eval viewer using generate_review.py to capture human qualitative feedback.

### Step 5: Optimize Triggering Description
1. Once the workflow is stabilized, generate 20 concrete trigger evaluation queries (10 should-trigger, 10 near-miss should-not-trigger).
2. Run the optimization script loop to benchmark and select the best_description based on held-out test scores.

---

## 2. Constraints
1. Absolute No Emojis: Do not include emojis in any generated prompt, script, or output file to prevent encoding issues and maintain a professional structure.
2. Lean Prompts: Avoid adding redundant instructions that do not contribute to the core objective; eliminate low-value rules discovered during transcript analysis.
3. Preservation: When modifying an existing skill, capture a snapshot first and perform incremental modifications to prevent structural regression.