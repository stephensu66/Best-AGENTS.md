# AGENTS.md

## Goals and Priority

This document defines the execution boundaries, delivery quality, and traceability requirements for agents working in this project. The goal is to make tasks directly executable, results verifiable, and process traceable.

Priority rules must be applied in the following order:

1. The user's current explicit request
2. Safety rules
3. The rules in this document
4. `README.md` and other project documentation

If a user request conflicts with safety rules, safety rules must take precedence.

## Execution Principles

- You must understand the task goals, constraints, and expected results before making changes.
- You must follow the existing project structure, naming conventions, and interface contracts.
- You must keep changes minimal and only modify content directly related to the current task.
- You must prioritize reusing existing functions, components, modules, and project patterns.
- You must validate external inputs and handle exception paths explicitly.
- You must ensure the output is runnable and maintainable, and you must not fabricate results or invent missing context.
- You must protect sensitive information and must not write it into code, logs, comments, or documents.
- It is forbidden to add dependencies, delete files, or modify Git history without a valid reason.
- It is recommended to check `README.md`, `package.json`, and documented project commands before running commands.
- It is recommended to add logs and comments only when necessary; any new comments must be written in English.

## Development Workflow

1. Understand the task: confirm the goals, inputs and outputs, constraints, and acceptance criteria.
2. Remove ambiguity: if there are critical uncertainties, ask concise clarifying questions first.
3. Define the approach: choose the simplest, most direct, and most reliable minimal viable change.
4. Implement the change: follow existing patterns and avoid out-of-scope refactoring.
5. Self-verify: run the necessary validation and record the results; if validation fails, you must explain the cause and the next recommended step.
6. Deliver clearly: explain what was done, what changed, how it was verified, and whether any risks remain.

## Response Rules

If the task is unclear, you must ask clarifying questions first and must not proceed by assumption.

If the task is clear, the final response must include at least the following fields:

1. What was done
2. Which files were modified
3. Validation results
4. `summary.md` update status
5. Follow-up suggestions, if any

For bug-fix tasks, you must explain the root cause, the change logic, and the impact scope.

For feature tasks, you must explain the new capability, the core implementation, and the validation approach.

## `summary.md` Rules

Default rule: before the final response for every completed user request, you must update `summary.md` in the project root.

Only exception: if the user explicitly requests not to update `summary.md` for the current task, you may skip the update, but the final response must clearly explain why it was not updated.

Language rule: `summary.md` should default to the user's current conversation language instead of forcing English. The `User Request` section should preserve the user's original intent as faithfully as possible, using the user's wording or a close paraphrase when appropriate.

If `summary.md` does not exist, you must create it first with the following initial content:

```markdown
# Project Summary

This file records a brief summary of each user request and AI response so future work can quickly recover project context. The language of each entry should normally follow the user's language for that task.
```

If `summary.md` already exists:

- You must append only at the end of the file.
- It is forbidden to overwrite, delete, or reorder existing entries.

Each appended entry must use the following template:

```markdown
---

## YYYY-MM-DD HH:mm

### User Request

- Briefly summarize the problem or task raised by the user.

### AI Response

- Briefly summarize the answer, analysis, modification, implementation, or conclusion.

### Modified Files

- If files were modified, list the file paths and the changes made.
- If no files were modified, write: No file changes.

### Important Notes

- Record important decisions, commands, constraints, follow-up work, or cautions.
```

Record requirements:

- You must append one entry for every user request.
- Even if no code was changed, you must still record the conclusion.
- The language of each entry should follow the user's language for that task unless the user explicitly asks for a different language.
- The `User Request` section should preserve the user's actual request state and wording as closely as practical.
- You must avoid writing sensitive information; if sensitive content is involved, describe it abstractly.
- If updating fails, the final response must clearly explain the failure reason.

## Forbidden Actions

- It is forbidden to rewrite unrelated code or perform out-of-scope refactoring.
- It is forbidden to change public interfaces or behavioral semantics without being asked.
- It is forbidden to introduce unnecessary abstraction layers or complexity.
- It is forbidden to add mocks, fake data, or placeholder implementations unless the user explicitly requests them.
- It is forbidden to claim something was validated or tested when no validation was actually run.
- It is forbidden to treat unknown project details as established facts.
