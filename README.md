# Project Template

A small, technology-neutral starting point for new projects. This repository contains agent instructions and a project-bootstrap skill, not an application and not a preselected runtime.

## Use it

1. Clone this repository into the new project directory.
2. Open your coding agent in that directory and invoke `project-bootstrap` using its skill command or picker.
3. Answer the interview questions and approve the proposed stack and implementation plan.
4. Let the skill generate and validate the starter.

This skill is manual-only; the agent must not start it automatically. No separate prompt is needed. The [skill](.agents/skills/project-bootstrap/SKILL.md) reads the repository instructions and guides the workflow from interview through setup.

## Optional Matt Pocock workflow

During the interview, you can opt into the Matt Pocock engineering skills. If enabled, the approved bootstrap plan installs the configured bundle, including `ask-matt`, and runs `/setup-matt-pocock-skills` once. See the [project-bootstrap skill](.agents/skills/project-bootstrap/SKILL.md#optional-agent-tools) for the commands.

That setup skill owns issue-tracker and domain-document questions. After setup, use `/ask-matt` as the entry point for follow-up work such as specifications, implementation, code review, and tickets. It supplements the template interview; it does not replace it.

## Supported starting variants

The skill can generate a minimal:

- frontend application
- backend service
- full-stack application
- library or CLI
- documentation/tooling-only project

The variant is selected during the interview. Framework, language, runtime, deployment target, and package manager remain project decisions.

## Conventions

- Keep the generated project as small as its requirements allow.
- Use `pnpm` for JavaScript/TypeScript frontend work.
- Use `uv` for Python projects and the standard Go toolchain for Go projects.
- For frontend projects, prefer `oxlint` and `oxfmt` when the chosen ecosystem supports them.
- For Python backends, prefer `ruff` for linting and formatting.
- Add tests and a test command appropriate to the selected stack.
- Never install dependencies, initialize services, or choose deployment infrastructure without explicit approval.
- Use Conventional Commits.

## What belongs here

Keep this repository limited to reusable instructions and scaffolding guidance. Do not add application-specific source code, dependencies, secrets, or deployment configuration.
