---
name: project-bootstrap
description: Manually invoked workflow to interview the user and generate a minimal starter project from this technology-neutral template.
disable-model-invocation: true
---

# Project Bootstrap

Turn a cloned template into the smallest useful starter through an interview, an approved plan, and validation.

Start only when the user invokes this skill through the host's skill command or picker. Reading this file or matching a task does not authorize the workflow. Conduct it yourself using the host's tools; no separate prompt or manual invocation of another interview skill is needed.

## 1. Prepare

Read `AGENTS.md` and `README.md` at the repository root, three directories above this skill's directory. Inspect the repository and working-tree changes. Preserve existing work and carry recorded decisions into the interview.

Check whether `find-skills` is available. If missing, ask for approval to install this bootstrap tool:

```shell
pnpx skills add vercel-labs/skills \
  --skill find-skills -y
```

If declined or unavailable, continue without it. This approval covers only bootstrap tooling; project setup requires the plan approval in step 3. Installation commands in this skill and its references are for bootstrapping a cloned project, never for editing the template.

**Gate:** Existing work and decisions are accounted for, and `find-skills` is available or explicitly skipped.

## 2. Interview

Use the available `grill-me` / `grilling` skill through the host's skill mechanism to challenge vague requirements and expose missing decisions. If unavailable, conduct the focused interview yourself.

Treat the user's answers and repository files as the source of truth. Ask only questions that apply to the selected variant and remain unanswered:

- **Outcome:** Project name, one-sentence purpose, smallest useful first milestone, and work excluded from it.
- **Variant:** Frontend application, backend service, full-stack application, library or CLI, or documentation/tooling-only project.
- **Stack:** Language, framework, runtime version, and package manager. Apply the compatible [tooling defaults](#tooling-defaults).
- **Architecture:** Responsibilities and boundaries; data flows, domain entities, APIs, integrations, storage, authentication/authorization, and failure modes.
- **Operations:** Local development, Docker, reverse proxy such as Caddy, environments, hosting/platform, CI/CD checks and deployment flow, secrets/configuration, migrations, backups, logging, and monitoring. Cover offline use, performance, privacy, and compliance constraints.
- **UI, when present:** Users and tasks, screens and states, responsive behavior, accessibility, interactions, visual language, design system, browser/device support, and existing brand or design references.
- **Commands:** Development, formatting, linting, type checking, tests, and deployment checks.
- **Optional agent tools:** Whether the Matt Pocock workflow is wanted, and whether browser, design, or stack-specific tools are needed. Read the relevant [optional agent tools](#optional-agent-tools) reference before explaining or proposing them.

For undecided choices, explain trade-offs briefly and recommend the smallest neutral option. Confirm architecture, stack, deployment, and visual choices with the user rather than choosing silently. Record unknowns as assumptions or deferred decisions.

**Gate:** Every applicable topic has an answer, an explicit assumption, or a deferral; the variant, stack, and first milestone are selected. Resolve decisions that block a concrete plan before proceeding.

## 3. Obtain plan approval

Present a concise plan with:

- selected variant and stack;
- architecture boundaries and data flow;
- proposed directory structure and files;
- local development and operations scope, marking Docker, Caddy, CI/CD, hosting, migrations, backups, and observability as included or deferred;
- UI scope and design/accessibility direction, when applicable;
- setup and development commands, formatting/linting/type-checking/test approach, and validation commands;
- configuration boundaries and required environment variables;
- assumptions and deferred responsibilities;
- selected optional agent tools, their exact installation commands, and the setup sequence from their reference; state whether the Matt workflow is enabled.

Wait for explicit approval covering the stack, plan, and setup commands, including any remote skill installation. Until then, do not add framework-specific files, install project packages, execute remote scaffolding commands, initialize databases, or create cloud resources.

**Gate:** The user has approved the concrete plan and selected toolchain, including each opt-in installation.

## 4. Implement

1. Install and configure approved agent tools using their reference. If the Matt workflow is enabled, complete its setup before scaffolding.
2. Create the smallest runnable structure and add the selected runtime and development tooling.
3. Add the first vertical slice or smoke test. Test behavior that can be tested; include at least one meaningful smoke or unit test. Add type checking when conventional for the selected language and stack.
4. Document the variant, stack, reproducible setup, start command, development and validation commands, configuration boundaries, and next milestone in the project README. Keep secrets in environment variables and provide a safe example file when configuration is needed.

Keep speculative features in deferred work rather than implementing them.

**Gate:** The approved starter and its tests, tooling, and contributor documentation exist; any unimplemented plan items are identified as blockers.

## 5. Validate and report

Run the documented start command and applicable formatting, linting, type-checking, and test commands. Check that required environment variables are documented without real secrets, and that no secrets, generated caches, or machine-specific paths are included in changes intended for commit.

Report changed files, commands run and their results, failures, and remaining decisions. Explain any failed or unavailable check rather than claiming it passed. Use Conventional Commits if the user requests a commit.

**Gate:** A new contributor can understand, reproduce, and run the starter from its README. Every applicable check has a recorded result; any failure or blocker is explained in the handoff.

## Tooling defaults

Apply only after the user selects a compatible stack:

- JavaScript/TypeScript frontend: `pnpm`; prefer `oxlint` and `oxfmt`.
- Python backend: `uv`; prefer `ruff` for linting and formatting.
- Go project: the standard Go toolchain, `gofmt`, and `go test`.
- Other stacks: use established ecosystem tooling and explain the choice.

## Optional agent tools

When discussing or planning browser/design tools, Svelte/SvelteKit tooling, or the Matt Pocock workflow, read the matching section of [AGENT-TOOLS.md](AGENT-TOOLS.md). It owns installation commands and branch-specific setup and handoff instructions.
