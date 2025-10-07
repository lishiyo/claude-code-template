## Usage

`/project:review-audit <AUDIT_FILE_PATH>`

## Context

- Path to audit file: $ARGUMENTS
- Relevant code or files will be referenced ad-hoc using @ file syntax.

## Your Role

You have implemented some code that has just been reviewed by an auditor. Review the audit in $ARGUMENTS - it will note which task was reviewed. The audit is not necessarily valid - sometimes it thinks you didn't finish something for example, when it is an upcoming todo in the tasks doc. Your job is to assess the validity of the audit, and for any valid and critical issues, add them as empty todos in the Task you just implemented (so you will fix them immediately), and for any valid but non-critical issues, add them as todos in a later phase of the task doc after verifying with me first.

## Process

1. Think step-by-step, laying out assumptions and unknowns.
2. Do not assume the auditor is correct. Check each of its claims - assess whether it is valid or invalid, and if valid, how important the issue is to fix. Even if it is a valid issue, it might already be in an upcoming todo in the tasks doc, so always read the empty todos in the full task doc. 
3. You can use subagents to investigate different parts of the codebase in assessing the claims of the auditor. For each sub-agent, clearly delegate its task, capture its output, and summarise insights. 
4. If gaps remain, iterate (spawn sub-agents again) until confident.

## Output Format

1. **Reasoning Transcript** (optional but encouraged) – show major decision points.
2. **Final Answer** – outcome of your investigation in Markdown. Each claim should be addressed as valid or invalid, and an assessment of the criticalness of the issue, with explanation why.
3. **Next Actions** – bullet list of follow-up items for the team (if any). The follow-up items if any should likely include: add any valid and critical issues as empty todos in the task doc, for the Task that was just audited; add any valid but non-critical issues in a later phase in the tasks doc.