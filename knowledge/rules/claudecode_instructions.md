# Claude Code Instructions

## Role
You are a collaborative AI engineer working within the AI-Loop framework.
Your primary concern is correctness, clarity, and closing the feedback loop.

## Core Principles

### STOCK — Universal knowledge (knowledge/)
- Treat files in `knowledge/` as long-lived, project-wide truth.
- Before changing any rule or definition, record the rationale in `knowledge/adr/`.
- Prefer explicit definitions in `knowledge/defines/` over ad-hoc assumptions.
- Organize `knowledge/defines/` by domain:
  - `loop/` — how the validation/feedback cycle in `loop/` works and what "done" means.
  - `skill/` — reusable, step-by-step procedures for recurring work.
  - `model/` — which class of model to use for which kind of task.

### FLOW — Dynamic task context (flow/)
- Each task starts from a file in `flow/tasks/`.
- Read the task file fully before writing any code.
- Update the task file status when work starts and when it completes.

### EXECUTION — Product code (src/)
- All deliverable code lives under `src/`.
- Keep commits small and scoped to a single task.
- Never commit directly to `main`; use feature branches.

### LOOP — Validation and feedback (loop/)
- After each implementation, run validation and write results to `loop/feedback/`.
- If GitHub Actions fails, read `loop/feedback/` before proposing a fix.
- A task is only "done" when CI is green and feedback is clean.

## Workflow

1. Read the active task from `flow/tasks/`.
2. Check relevant definitions in `knowledge/defines/` and rules in `knowledge/rules/`.
3. Implement in `src/`.
4. Run local checks and record output in `loop/feedback/`.
5. Push and confirm CI passes via `.github/workflows/ai-validation.yml`.
6. Mark task complete and move to next.

## Output Quality

- Write no comments unless the WHY is non-obvious.
- Prefer editing existing files over creating new ones.
- Do not add features or abstractions beyond what the task requires.
- If a decision is significant, create an ADR in `knowledge/adr/` before proceeding.
