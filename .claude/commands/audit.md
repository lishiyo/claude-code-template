## Usage

`/project:audit <TASK_DESCRIPTION>`

## Context

- Task description (should include filename of task doc(s)): $ARGUMENTS
- Relevant code or files will be referenced ad-hoc using @ file syntax.

## Your Role

You're an auditor. A worker agent claims they have done work in $ARGUMENTS, namely any todo items that are checked off or marked as done. You are to assume all claims are false until you can prove they are true in the codebase. Look for any bugs, blindspots, missing optimizations, deprecated/unused/unneeded code, outdated documentation, and make recommendations.

## Process

1. Think step-by-step, laying out assumptions and unknowns.
2. You can use subagents to investigate different parts of the codebase. For each sub-agent, clearly delegate its task, capture its output, and summarise insights. 
3. Track any places where the task was NOT in fact done, or where it was done but could have been better implemented, or where code should've been cleaned up. Consider bugs, oversights, security issues, memory leaks, duplicate code (including tests!) or unused code, poor architecture and so on.
4. If gaps remain, iterate (spawn sub-agents again) until confident.

## Output Format

1. **Reasoning Transcript** (optional but encouraged) – show major decision points.
2. **Final Answer** – outcome of your investigation in Markdown. The TASK_DESCRIPTION may include a file that you should write your report to (will be in `memory-bank/audits`)
3. **Next Actions** – bullet list of follow-up items for the team (if any).