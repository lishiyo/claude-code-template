# Claude Code Project Template

A **technology-agnostic workflow template** for effective human-AI collaboration on mid-to-large software projects. This is optimized for Claude Code but can be easily repurposed for other agents. It attempts to be as lightweight and generalizable as possible while providing enough of a structure and workflow harness to guide any project.

## What This Template Is

This template provides **workflow structure and documentation standards** for working with AI agents (especially Claude Code) on larger projects that require:
- **Multiple coordinated tasks** with clear handoffs between sessions
- **Persistent context management** across development phases
- **Structured planning and documentation** that stays synchronized with code
- **Quality gates and validation** to ensure consistent standards
- **Parallel development coordination** when multiple features are in flight

It follows a clear RESEARCH -> PLAN -> IMPLEMENT -> AUDIT/TEST -> DOCUMENT loop. See [WORKFLOW.md](./memory-bank/reference/WORKFLOW.md) for details.

## What This Template Is NOT

This template is **deliberately unopinionated** about:
- **Programming languages** (Python, TypeScript, Rust, Go, etc.)
- **Frameworks and tech stacks** (React, Django, Express, etc.)
- **Project types** (web apps, CLI tools, libraries, scripts, etc.)
- **Code organization** (no `src/` structure imposed)
- **Build systems or tooling** (works with any project setup)

Instead, it focuses on the **meta-process** of how humans and AI agents can collaborate effectively on software projects that span multiple features, require careful planning, and benefit from structured documentation.

## Included Tools

The template includes optimized **Claude Code agents** and **Claude Code commands** in `.claude/` that may be useful.

## 🚀 Quick Start

### For New Projects
```bash
# 1. Copy template structure
cp -r cc-template/ my-new-project/
cd my-new-project/

# 2. Customize for your project (see Customization Guide below)
# 3. Start first task following memory-bank/reference/WORKFLOW.md
```

### For Existing Projects
```bash
# 1. Copy memory-bank/ folder to your existing project
cp -r cc-template/memory-bank/ your-project/
cp cc-template/CLAUDE.md your-project/

# 2. Customize CLAUDE.md and memory-bank/docs/ for your project
# 3. Begin using workflow for new features
```

### For Forking External Repos
```bash
# 1. Fork the repo
git clone your-fork-url
cd forked-project/

# 2. Add template structure
cp -r /path/to/cc-template/memory-bank/ .
cp /path/to/cc-template/CLAUDE.md .

# 3. Customize and start contributing with structured workflow
```

## ⚙️ Setup Process

### Phase 0: Template Customization (5 minutes)

**REQUIRED - Customize these files first:**

1. **Update `CLAUDE.md`** - Replace template placeholders:
   ```markdown
   ## Project Context
   See `memory-bank/prd.md` for our PRD. [YOUR PROJECT DESCRIPTION HERE]

   ## Project-Specific Rules
   [YOUR CODING STANDARDS, TECH STACK, ETC.]
   ```

2. **Fill Basic Project Info** in `memory-bank/docs/prd.md`:
   - Replace `[Replace with actual project name]`
   - Update problem statement and solution
   - Add your tech stack requirements

### Phase 1: Project Planning (with AI Agent)

**Work with AI agent to flesh out core documentation:**

1. **Complete PRD** (`memory-bank/docs/prd.md`)
   - Detailed requirements and success criteria
   - Technical specifications
   - User stories and acceptance criteria

2. **Create Architecture Overview** (`memory-bank/docs/architecture/OVERVIEW.md`)
   - System design and component interactions
   - Technology choices and rationale
   - Data flow and integration points

3. **Write Implementation Plan** (`memory-bank/docs/implementation_plan.md`)
   - Feature breakdown and priorities
   - Technical milestones
   - Dependency mapping

4. **Generate Task Roadmap** (`memory-bank/tasks/roadmap.md`)
   - Task breakdown from implementation plan
   - Parallel execution strategy
   - Resource allocation and timeline

### Phase 2: Implementation

**Follow structured workflow for each feature:**

1. AI agent reads mandatory files (`CLAUDE.md`, `WORKFLOW.md`, `CONVENTIONS.md`)
2. Create task folder: `memory-bank/tasks/[task-id]/`
3. Research → Planning → Implementation → Validation
4. Quality gates and handoff documentation

## 📁 Template Structure

```
your-project/
   CLAUDE.md                    # ✏️ CUSTOMIZE: AI agent instructions
   README.md                    # ✏️ CUSTOMIZE: Project overview
   memory-bank/                 # 📋 AI workflow and documentation
      docs/                   # ✏️ CUSTOMIZE: Project documentation
         prd.md             # ✏️ REQUIRED: Product requirements
         implementation_plan.md # ✏️ FILL: Overall roadmap
         changelog.md       # 📦 AUTO: Progress tracking
         architecture/
             OVERVIEW.md    # ✏️ FILL: System design
             decision-records/ # 📦 AUTO: ADR documentation
      tasks/                  # 📦 AUTO: Task management workspace
         roadmap.md         # ✏️ FILL: Task breakdown
         backlog.md         # 📦 AUTO: Issue tracking
         [task-id]/         # 📦 AUTO: Individual task folders
      reference/              # 📦 KEEP: Workflow standards
          WORKFLOW.md        # 📦 KEEP: How AI agents work
          CONVENTIONS.md     # 📦 KEEP: Coding standards
          CHECKLIST.md       # 📦 KEEP: Quality validation
          HANDOFF_GUIDELINES.md # 📦 KEEP: Session transitions
   src/                        # ✏️ YOUR CODE: Source code
   tests/                      # ✏️ YOUR CODE: Test files
   [project files]            # ✏️ YOUR CODE: Package.json, etc.
```

**Legend:**
- ✏️ **CUSTOMIZE**: Must be updated for your project
- 📦 **KEEP/AUTO**: Use as-is or auto-generated by workflow
- 📋 **WORKFLOW**: Core template structure

## 📖 Common Usage Scenarios

### Scenario 1: Brand New Project

**Perfect for**: Starting a project from scratch with AI assistance

**Process**:
1. Copy entire template
2. Customize `CLAUDE.md` with project context
3. Work with AI to complete `docs/prd.md` and `architecture/OVERVIEW.md`
4. Create `implementation_plan.md` and `roadmap.md`
5. Begin first task using workflow

**Example**: Building a new web application, CLI tool, or library

### Scenario 2: Adding Features to Existing Project

**Perfect for**: Bringing structure to ongoing projects

**Process**:
1. Copy `memory-bank/` folder and `CLAUDE.md` to existing project
2. Document current state in `architecture/OVERVIEW.md`
3. Create PRD for new features in `prd.md`
4. Use workflow for all new development going forward

**Example**: Adding authentication to existing app, new API endpoints

### Scenario 3: Contributing to External Repository

**Perfect for**: Fork and modify workflow with clear documentation

**Process**:
1. Fork repository
2. Add template structure for your changes only
3. Create focused PRD for your specific contributions
4. Use workflow to implement changes
5. Submit PR with clear documentation trail

**Example**: Adding feature to open source project, fixing bugs

### Scenario 4: Legacy Project Modernization

**Perfect for**: Bringing old projects up to current standards

**Process**:
1. Add template structure
2. Document existing architecture in `OVERVIEW.md`
3. Create modernization plan in `implementation_plan.md`
4. Use workflow to incrementally improve codebase

**Example**: Updating old Node.js app, adding TypeScript, improving tests

## ✅ Developer Setup Checklist

**Before First Task:**

- [ ] **Copy template files** to your project directory
- [ ] **Update `CLAUDE.md`** with project-specific context and rules
- [ ] **Customize `memory-bank/docs/prd.md`** with your project requirements
- [ ] **Verify AI agent setup** - agent can read and understand `CLAUDE.md`
- [ ] **Test workflow** - try one small task to validate process

**For Team Projects:**

- [ ] **Share template structure** with all team members
- [ ] **Establish coordination** - who updates roadmap.md
- [ ] **Set up shared understanding** of workflow phases
- [ ] **Create first tasks** in roadmap.md for parallel work

**Quality Verification:**

- [ ] **Lint configuration** - ensure project linting rules work with template
- [ ] **Test setup** - verify test commands work as expected
- [ ] **Documentation standards** - team agrees on conventions
- [ ] **Git workflow** - template files properly tracked in version control

## 🤖 AI Agent Instructions

**When you use this template:**

1. **Always read `CLAUDE.md` first** - contains project-specific context
2. **Follow `memory-bank/reference/WORKFLOW.md`** for all tasks
3. **Use `memory-bank/reference/CHECKLIST.md`** at each phase
4. **Update documentation** as you make changes
5. **Create proper handoffs** using `HANDOFF_GUIDELINES.md`

## ⚙️ Advanced Configuration

### Custom Workflow Modifications

The template workflow can be customized for specific project needs:

- **Add project-specific steps** to `WORKFLOW.md`
- **Extend checklists** in `CHECKLIST.md` for your tech stack
- **Create custom conventions** in `CONVENTIONS.md`
- **Add specialized agents** for complex domains

### Integration with Existing Tools

Template works alongside:
- **Git hooks** - for automated quality checks
- **CI/CD pipelines** - using documentation as source of truth
- **Issue trackers** - link tasks to GitHub issues
- **Code reviews** - use audit.md files for review preparation

## 💡 Examples

### Example: Adding Authentication to Web App

```bash
# 1. Set up task
mkdir memory-bank/tasks/1-1-auth-system
cd memory-bank/tasks/1-1-auth-system

# 2. Follow workflow
# - research.md: Investigate current auth patterns
# - plan.md: Design JWT implementation
# - Implementation with tests
# - audit.md: Quality review
# - handoff.md: Session documentation

# 3. Update roadmap
# Mark task complete in memory-bank/tasks/roadmap.md
```

### Example: Bug Fix with Documentation

```bash
# 1. Create task folder
mkdir memory-bank/tasks/2-1-fix-login-bug

# 2. Document investigation in research.md
# 3. Plan fix in plan.md
# 4. Implement with tests
# 5. Update any affected documentation
# 6. Complete handoff.md for knowledge transfer
```

## 🔧 Troubleshooting

**AI agent not following workflow?**
- Check that `CLAUDE.md` mandatory reading section is complete
- Verify workflow checkpoints are clear in `WORKFLOW.md`
- Ensure agent has access to all required files

**Documentation getting out of sync?**
- Use "living documentation" principle - update docs in same commit as code
- Review `CONVENTIONS.md` for documentation standards
- Set up git hooks to require documentation updates

**Tasks taking too long?**
- Break down complex tasks in `plan.md`
- Use parallel task strategy from `roadmap.md`
- Check if blockers need external help

**Quality issues?**
- Review `CHECKLIST.md` thoroughly
- Use implementation-auditor agent for reviews
- Ensure all quality gates are passing

## 🤝 Contributing

To improve this template:

1. Use the template's own workflow
2. Create task in `memory-bank/tasks/` for your improvement
3. Follow research → planning → implementation → validation
4. Submit PR with complete documentation trail

## 📄 License

[Add your license here]

---

**Need help?** Check `memory-bank/reference/` for detailed guidelines or review the example task in `memory-bank/tasks/0-example-feature/`.
