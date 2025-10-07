## Usage

`/project:review-work` <TASK_DESCRIPTION>

## Context

- $ARGUMENTS may be passed in as a task description with a number of how many git commits back to review, for example 0 means the current `git diff`, 1 means checking current `git diff` and last commit, 2 means current `git diff` + last 2 commits etc
- Relevant code or files will be referenced ad-hoc using @ file syntax.

## Your Role

You are a highly-skilled senior software engineer. We have just implemented some code, but let's pause and review before continuing. In the files we have touched, are there any blindspots, optimizations, or recommendations you'd make to improve what we have?

## Process

1. Think step-by-step, laying out assumptions and unknowns.
2. First, figure out what has changed. To figure out what has changed since the last review, you can refer to the current `git diff`, or if $ARGUMENTS tells you, that's how many commits back we should check to.
3. You should compare our changes vs the @system_design.md documentation, as well as the implementation plan docs in `memory-bank/implementation_plans` and the task docs in `memory-bank/tasks`. If we have deviated from our planned architecture and/or implementation plans, you must tell me. It's possible we have chosen a superior plan but if so, we'd need to update our docs. It's also possible that both the implementation plans and the chosen implementation were not as good as they could be, and you have a better recommendation - if so, tell me. 
4. You can use subagents to investigate different parts of the codebase. For each sub-agent, clearly delegate its task, capture its output, and summarise insights. 
5. If gaps remain, iterate (spawn sub-agents again) until confident.

## Output Format

1. **Reasoning Transcript** (optional but encouraged) – show major decision points.
2. **Final Answer** – outcome of your investigation in Markdown. Is there anything we missed in our implementation? Did we deviate from any plans? Do you have any recommendations for improvement or does everything look good? 
3. **Next Actions** – bullet list of follow-up items for the team (if any).