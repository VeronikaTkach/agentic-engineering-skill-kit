# Agent Instructions

Use this project with the shared skill library in:

```text
./agent-skill-kit/skills
```

Before starting substantial work, read:

```text
./agent-skill-kit/skill-library-map.md
```

## Skill Routing

Use the narrowest relevant skill:

- `spec-driven-development` before coding unclear features.
- `react-enterprise-rules` for React, TypeScript frontend, FSD, Redux, Tailwind, shadcn/ui, Radix.
- `nestjs-backend-rules` for NestJS backend code.
- `database-design-rules` for PostgreSQL, Prisma, Supabase, schema, migrations, indexes.
- `testing-patterns` for unit, integration, e2e, Playwright, and regression test strategy.
- `typescript-code-review` for focused TypeScript code review.
- `code-review` for PR-level review and merge readiness.
- `agent-security-review` for auth, secrets, sensitive data, MCP/tools, production actions.
- `mcp-tool-consumption` for MCP adoption, debugging, permissions, and tool governance.
- `observability-rules` for traces, audit logs, cost, eval telemetry, and debugging.
- `a2a-agent-design` for Agent Cards, registries, and remote specialist agents.
- `a2ui-patterns` for safe agent-generated UI and trusted component catalogs.
- `agentic-commerce-rules` for agentic payments, ordering, spending limits, receipts, and approvals.

## Workflow

For new features:

1. Start with `spec-driven-development`.
2. Use implementation skills for the affected layer.
3. Use `testing-patterns`.
4. Use `typescript-code-review`.
5. Use `agent-security-review` when sensitive data, permissions, tools, production, or external actions are involved.
6. Use `code-review` before merge.

## Guardrails

- Do not perform destructive actions without explicit approval.
- Do not add dependencies without explaining why.
- Do not use unverified public MCP servers with production data.
- Keep diffs focused.
- Add or update tests for meaningful behavior changes.
- Report assumptions, checks run, and residual risk.
