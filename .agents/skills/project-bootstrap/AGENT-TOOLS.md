# Optional agent tools

Reference for the interview, plan, and implementation steps in [Project Bootstrap](SKILL.md). Include selected tools and exact installation commands in the plan; execute them only after its approval.

## Browser and design

Add browser and design tools when needed:

```shell
pnpx skills add vercel-labs/agent-browser \
  --skill agent-browser -y

pnpx skills add vercel-labs/agent-skills \
  --skill web-design-guidelines -y
```

## Svelte

For Svelte or SvelteKit projects, include configuration of the [Svelte MCP](https://svelte.dev/docs/ai/mcp) and installation of the Svelte skills:

```shell
pnpx skills add sveltejs/ai-tools \
  --skill svelte-core-bestpractices \
  --skill svelte-code-writer -y
```

## Optional Matt Pocock workflow

During the interview, explain that opting in installs the full configured bundle below, including `ask-matt`, and runs `/setup-matt-pocock-skills` once after approval. This supplements the bootstrap interview rather than replacing it. Leave issue-tracker and domain-document questions to that setup skill.

When enabled, include this exact installation command and the setup sequence in the plan:

```shell
pnpx skills add mattpocock/skills \
  --skill ask-matt \
  --skill domain-modeling \
  --skill improve-codebase-architecture \
  --skill wayfinder \
  --skill codebase-design \
  --skill setup-matt-pocock-skills \
  --skill to-spec \
  --skill code-review \
  --skill implement \
  --skill to-tickets \
  --skill grilling \
  --skill grill-with-docs \
  --skill triage \
  --skill tdd \
  --skill writing-for-agents \
  --skill prototype \
  --skill retro \
  -y
```

After approval:

1. Install the configured bundle.
2. Run `/setup-matt-pocock-skills` once, before scaffolding or using the other Matt skills. Let it ask its own issue-tracker and domain-document questions.
3. Include `/ask-matt` in the generated README as the entry point for follow-up engineering work.

When the workflow is disabled, omit its installation, setup, and README handoff.
