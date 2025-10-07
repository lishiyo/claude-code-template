---
title: "Handoff Protocol for Claude Code Sessions"
description: "What a HANDOFF.md task file should look like on completion of a task"
---

## Required Structure for Task Handoffs

Every active task MUST maintain a HANDOFF.md with these sections:

### 1. Session Log (append, don't overwrite)
- Session timestamp
- What was attempted
- What was completed
- What was blocked/failed

### 2. Current State (overwrite each session)
- Which files were modified
- What's working/tested
- What's broken/untested

### 3. Next Session Setup
- Exact files to include in context
- Specific next steps (be explicit!)
- Known gotchas/warnings

## Example Template

---
## Session: [DATE TIME]

### Completed
- [ ] List actual changes made
- [ ] Include file paths and line numbers for modifications

### Attempted but Blocked
- Issue: [what went wrong]
- Why: [root cause if known]

### Modified Files
- `path/to/file.js` - Added authentication middleware (lines 23-47)
- `path/to/other.js` - Updated imports only

### Current State
- ✅ Auth middleware compiles
- ❌ Tests failing: `auth.test.js` line 34 - missing mock
- ⚠️ Hardcoded secret in config.js line 12

### Next Session Must
1. Fix the failing test by adding mock for `jwt.sign`
2. Move hardcoded secret to .env
3. Continue with route protection (see implementation.md section 3)

### Context for Next Session
Include these files in this order:
1. This handoff file
2. `src/auth/middleware.js`
3. `tests/auth.test.js`
4. `.env.example`
---

## Parallel Work Coordination

If your task might conflict with another active task:
1. List your "claimed" files at session start
2. Check other active tasks' HANDOFF.md files
3. Note any coordination needed