# GSD Skill for OpenClaw

This skill integrates the **GSD (Get Shit Done)** framework into OpenClaw coding sessions. It forces rigorous context management and spec-driven development for high-quality code.

## Installation

1. Clone this repo into your OpenClaw skills directory:
   ```bash
   git clone https://github.com/serra-veltria/openclaw-gsd-skill ~/.openclaw/skills/gsd
   ```

2. Install the GSD CLI tool globally:
   ```bash
   npm install -g get-shit-done-cc
   ```

3. Ensure `coding-agent` skill is also installed (this skill enhances it).

## Usage

When creating complex features or fixing bugs, invoke the GSD tools instead of raw coding commands.

- `gsd_new_project`: Start a new project (interactive Q&A)
- `gsd_map_codebase`: Map existing code (generates ARCHITECTURE.md)
- `gsd_plan_phase`: Plan a phase (XML atomic plans)
- `gsd_execute_phase`: Execute a phase (multi-agent orchestration)
- `gsd_verify_work`: Verify implementation against specs
