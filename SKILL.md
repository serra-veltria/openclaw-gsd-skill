---
name: gsd
description: Get Shit Done (GSD) framework for coding tasks. Use for large features, project planning, and reliable execution.
metadata:
  {
    "openclaw": { "emoji": "🚀", "requires": { "anyBins": ["opencode"] } },
  }
---

# GSD (Get Shit Done) Framework

This skill provides a structured workflow wrapper around the `get-shit-done-cc` system for **OpenCode**. It enforces rigorous context management and spec-driven development.

## ⚠️ Prerequisites

1. **Install GSD globally:**
   ```bash
   npm install -g get-shit-done-cc
   ```
2. **Install OpenCode globally:**
   ```bash
   npm install -g opencode-ai
   ```
3. **Models:** By default, this uses **Gemini 3 Pro** (via local LiteLLM proxy) to save costs.

## Usage Guide

Use GSD tools when:
- Starting a new feature or project (`gsd_new_project`)
- Understanding a complex codebase (`gsd_map_codebase`)
- Breaking down work into phases (`gsd_plan_phase`)
- Executing multi-step code changes (`gsd_execute_phase`)
- Verifying implementation against specs (`gsd_verify_work`)

**For quick fixes:** Use `gsd_quick` to execute ad-hoc tasks with GSD guarantees but skip full planning.

### Tool Definitions

The following tools wrap the GSD slash commands inside the `opencode` CLI.

#### `gsd_new_project`
Starts a new project wizard. Use when starting from scratch.
```bash
# Starts interactive wizard
bash pty:true env:{"OPENAI_API_BASE":"http://localhost:4000/v1","OPENAI_API_KEY":"sk-litellm-vertex-serra-2026","MODEL":"gemini-3-pro"} command:"opencode run '/gsd:new-project'"
```

#### `gsd_map_codebase`
Analyzes existing code to generate `ARCHITECTURE.md`, `CONCERNS.md`, etc. Crucial first step for brownfield projects.
```bash
# Analyze current directory
bash pty:true env:{"OPENAI_API_BASE":"http://localhost:4000/v1","OPENAI_API_KEY":"sk-litellm-vertex-serra-2026","MODEL":"gemini-3-pro"} command:"opencode run '/gsd:map-codebase'"
```

#### `gsd_plan_phase`
Breaks down the current goal into atomic XML plans (max 3 tasks per plan).
```bash
# Plan the next phase
bash pty:true env:{"OPENAI_API_BASE":"http://localhost:4000/v1","OPENAI_API_KEY":"sk-litellm-vertex-serra-2026","MODEL":"gemini-3-pro"} command:"opencode run '/gsd:plan-phase'"
```

#### `gsd_execute_phase`
Executes a planned phase using multi-agent orchestration. Spawns fresh contexts for each task.
- `phase`: The phase number to execute (e.g., 1).
```bash
# Execute Phase 1
bash pty:true env:{"OPENAI_API_BASE":"http://localhost:4000/v1","OPENAI_API_KEY":"sk-litellm-vertex-serra-2026","MODEL":"gemini-3-pro"} command:"opencode run '/gsd:execute-phase 1'"
```

#### `gsd_verify_work`
Verifies the implementation against the original specs using a dedicated QA agent.
- `phase`: The phase number to verify (e.g., 1).
```bash
# Verify Phase 1
bash pty:true env:{"OPENAI_API_BASE":"http://localhost:4000/v1","OPENAI_API_KEY":"sk-litellm-vertex-serra-2026","MODEL":"gemini-3-pro"} command:"opencode run '/gsd:verify-work 1'"
```

#### `gsd_quick`
Executes an ad-hoc task with GSD guarantees (context reset) but skips full planning.
- `task`: The task description.
```bash
# Quick fix
bash pty:true env:{"OPENAI_API_BASE":"http://localhost:4000/v1","OPENAI_API_KEY":"sk-litellm-vertex-serra-2026","MODEL":"gemini-3-pro"} command:"opencode run '/gsd:quick \"Fix the login button overflow\"'"
```

## Best Practices
1. **Always map first:** Run `gsd_map_codebase` on existing projects before planning.
2. **One phase at a time:** Execute and verify a phase before moving to the next.
3. **Trust the process:** Let GSD manage context resets. Do not manually clear context.
