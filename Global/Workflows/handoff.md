---
description: Use this skill at the end of a session or when switching contexts. It compresses the current conversation state, decisions made, and outstanding items into a transferrable markdown ledger.
---

---

## 1. Protocol

### Step 1: State Compression
1. Summarize the technical achievements, modified files, and active configuration states from the current session.
2. Extract all architectural decisions made and log them clearly.

### Step 2: Compile Handoff Artifact
1. Generate a standardized handoff ledger and save it to `.ai/docs/handoff.md`:
   - # Session Handoff Ledger
   - ## Current Status (Where we left off)
   - ## Tech Stack & Environment State
   - ## Next Immediate Steps (Action items for the next session)
   - ## Known Issues & Blocks

### Step 3: Final Output
1. Present the text summary of the handoff ledger to the user, highlighting the exact step the next agent should pick up.

---

## 2. Constraints
1. Absolute No Emojis: Forbidden anywhere within the handoff file or final summary text.