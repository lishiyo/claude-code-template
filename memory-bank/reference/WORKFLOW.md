---
title: "Optimized Project Workflow for Agent"
description: "Overall guidelines for AI agents like Claude on how to implement a task"
---

## Project Structure

We need to keep the docs in `memory-bank` up to date:
```
memory-bank/
├── docs/                   # Project-wide documentation
|   └── architecture/          # System design & component docs
│      ├── OVERVIEW.md        # Overall architecture, components
│      └── decision-records/   # ADR docs
│   ├── prd.md             # Product requirements & tech stack
│   ├── implementation_plan.md # Overall implementation roadmap
│   └── changelog.md       # Progress tracking & decisions
├── tasks/                  # Task implementation workspace
│   ├── roadmap.md         # High-level task breakdown
│   ├── backlog.md         # Discovered issues not yet prioritized
│   └── [task-id]/         # Per-task workspace
│       ├── research.md    # Research notes on the task
│       ├── plan.md        # Implementation plan & todos
│       └── audit.md       # Post-implementation review
        └── handoff.md     # Living document for session handoffs
└── reference/             # Standards, references, guidelines
    ├── data_schemas.md    # Data schemas reference
    ├── TESTING.md         # Testing guidelines & standards
    └── WORKFLOW.md        # This file - how we work together
```

## Streamlined Process

### Phase 1: Understanding
- Read relevant docs in `memory-bank/docs/` and existing code if any. Search internet if relevant.
- Use parallel research agents for complex discovery tasks
- Ask clarifying questions upfront - batch them together
- Document understanding in `tasks/<task-id>/research.md`; create that `<task-id>` subfolder if it doesn't exist yet, and make sure the task-id name includes the number first then a short semantic label (e.g. `1-1-bootstrap`)

### Phase 2: Planning
- Given the `research.md` and high-level docs (e.g. `implementation_plan.md`), come up with a plan for implementing the user request. We should reuse existing patterns, components and code where possible.
- Write the comprehensive plan to `plan.md` in the task subfolder. The plan should include all context required for an engineer to implement the feature.
- Create todo checklist within the same document, using `task-decomposer` subagent
- Include "What we're NOT doing" section to prevent scope creep
- Get user approval before implementation

### Phase 3: Implementation (Main work)
- Execute against the todo list, updating status inline
- Document discoveries, blockers, and decisions in `plan.md`
- Run tests and linting after each logical component
- Commit frequently with descriptive messages

### Phase 4: Validation
- Run full test suite and address any failures
- Quick self-review for code quality and consistency
- Update `docs/changelog.md` if the change is significant, or if you have discovered any learnings
- Mark task as complete
- With my go-ahead (no need for very simple tasks), let's do an audit/code review using a subagent:
  - Send list of completed todos to a SEPARATE `implementation-auditor` agent to conduct a separate review of your work, it should write to a new `audit.md` file in the `<task-id>` subfolder
  - Review the `audit.md`, if the issues are valid and important, add them as new todos to the same task and fix them now; if valid and not important, add to `backlog.md` instead
  - I may also ask you to use `code-cleanup-specialist` and/or `doc-code-sync-checker` subagents if you've made substantial changes to the codebase
- Stop here with a summary of how I can test this manually (what I should expect to see) so I can manually review this task has been successfully completed
- After I approve this was done, write a concise but clear handoff.md file in the `<task-id>` subfolder, following `reference/HANDOFF_GUIDELINES.md`.

## When to Use Sub-Agents

- Genuinely parallel research tasks that would benefit from concurrency
- Major refactoring where `code-cleanup-specialist` adds value
- Post-implementation when `doc-code-sync-checker` is needed for large changes

## Key Principles

- **Documentation Quality**: All docs should start with a clear purpose statement (frontmatter at top for markdown files)
- **Living Documentation**: Update `system_architecture.md` and other core docs when making significant changes
- **Focus on Value**: Prefer working code over extensive documentation processes
- **Quality Built-In**: Test and lint during development, not as separate phases

## Task Documentation Template

Each `tasks/<task-id>/plan.md` should follow this structure:

```markdown
# [Task Name]

**Parallel-Safe:** (Yes or No)
**Blocks:** ...
**Blocked By:** ...
**Touches Files:** 

## Understanding
- Current state
- Requirements
- Key constraints/patterns found

## Plan
- Implementation approach
- What we're NOT doing (scope boundaries)

## Todos
- [ ] Step 1
- [ ] Step 2
- [x] Completed step

## Success Criteria (examples below, check off on validation)
- [ ] JWT token generation/validation
- [ ] User session management
- [ ] Unit tests passing
- [ ] Integration with existing middleware

## Implementation Notes
- Discoveries made during implementation
- Blockers encountered and solutions
- Decisions made and rationale
```