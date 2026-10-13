# Project Template Instructions

This repository is a generator template, not an application. Its job is to help an agent create a small, deliberate project after interviewing the user.

## Before changing the template

- Read `README.md` and `.agents/skills/project-bootstrap/SKILL.md`.
- Keep the template technology-neutral.
- Do not add a runtime, framework, dependency manifest, application source, or deployment configuration to this repository.
- Do not run dependency installation or external setup commands while modifying the template.

## When bootstrapping a cloned project

- Start project-bootstrap only when the user manually invokes it; reading its instructions does not authorize running the workflow.
- Use the project-bootstrap skill as the source of truth.
- Ask for the project variant and important constraints before scaffolding.
- Present a short implementation plan and wait for approval before making architecture-defining changes.
- Do not install dependencies or initialize external services until the user chooses the toolchain and approves it.
- Prefer the smallest working starter over speculative abstractions.
- Add formatting, linting, type checking where relevant, and tests with a documented command for each.
- For frontends, use `pnpm`; prefer `oxlint` and `oxfmt` when compatible with the selected stack.
- For Python backends, use `uv` and prefer `ruff`.
- For Go projects, use the standard Go toolchain and its conventional test command.
- Keep secrets in environment variables and provide a safe example file when configuration is needed.
- Validate the generated project with the selected formatter, linter, type checker, and tests.
- Use Conventional Commits.

## Change checklist

Before declaring a generated project ready, confirm:

- the selected variant and stack are documented;
- the project starts with one documented command;
- formatting and linting are configured where applicable;
- tests exist and run with one documented command;
- configuration boundaries and required environment variables are documented;
- no secrets or machine-specific paths were committed.
