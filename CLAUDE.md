---
Title: Root Claude.md File
Description: Instructions that Claude must read every time. 
---

# Project Guidelines for Claude

This is a skeleton/template for creating new projects in Claude Code.

## Project Context

See `memory-bank/prd.md` for our PRD. <<FILL THIS OUT: Include our currently active context here.>>

## Documentation Standards

See `memory-bank/reference/CONVENTIONS.md` for documentation standards and conventions. You MUST read this file.

## Project-Specific Rules

<FILL THIS OUT>

## Development Workflow

### CRITICAL: Always Follow the Workflow

**BEFORE STARTING ANY TASK**: You MUST follow the workflow defined in `memory-bank/reference/WORKFLOW.md`:
1. Create task subfolder in `memory-bank/tasks/[task-id]/` (e.g., `2-1-baml-foundation`)
2. Document research in the task subfolder's `research.md`
3. Create implementation plan with todos in `plan.md`
4. Get user approval before implementing
5. Track progress and update todos during implementation
6. Create `audit.md` for post-implementation review when requested, this will be another agent's audit of your work, you may have to fix something
7. Create `handoff.md` in the task subfolder following `HANDOFF_GUIDELINES.md`

**NEVER skip this workflow** - it's critical for project organization and tracking.

### Task Implementation
1. Read the full task description in `docs/implementation_plan.md`
2. Check dependencies in `tasks/roadmap.md`
3. Update task status in roadmap when starting/completing
4. Follow the directory structure defined in `docs/architecture/OVERVIEW.md`

### Testing Requirements

<<FILL THIS OUT>>

### Code Quality

<<FILL THIS OUT>>


## Memory Bank Organization

```
memory-bank/
├── docs/               # Core project documentation
  |-- architecture/     # Architecture overview and ADRs
├── tasks/              # Task tracking and implementation workspace
└── reference/          # Standards, schemas, decisions, workflow
```

**Key Files:**
- `memory-bank/reference/WORKFLOW.md` - How to implement tasks
- `memory-bank/reference/data_schemas.md` - All data structure definitions
- `memory-bank/docs/architecture/OVERVIEW.md` - system design, ADR logs in `decision-records` subfolder
- `memory-bank/reference/TESTING.md` - Testing standards and patterns

## Parallel Development Guidelines

### When Multiple Agents Work Together

<<FILL THIS OUT>>

### Critical Dependencies

<<FILL THIS OUT>>

## Error Handling Priorities

<<FILL THIS OUT>>

## Success Metrics to Remember

<<FILL THIS OUT>>

## When in Doubt

1. Check the PRD first (`docs/prd.md`)
2. Review architecture overview and decisions (`docs/architecture/` files)
3. Follow the parallel execution strategy (`tasks/roadmap.md`)
4. Keep documentation synchronized with code changes
