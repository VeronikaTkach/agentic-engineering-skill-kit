# Case 06: Expense Approval Mini App

## User Task

Design and implement a small Expense Approval Mini App.

Product behavior:

- An authenticated employee can submit an expense request.
- An expense request has: `amountCents`, `currency`, `category`, `description`, `receiptUrl`.
- The employee ID must come from trusted auth context, never from the request body.
- A manager can approve or reject pending expenses.
- Employees can only see their own expenses.
- Managers can see pending expenses from all employees.
- Approved/rejected expenses cannot be edited.
- Every approval or rejection must create an audit log entry.
- `receiptUrl` is optional, but if present it must be validated as a URL.
- `amountCents` must be greater than 0.
- `currency` can be `USD` or `EUR`.
- `category` can be `travel`, `meals`, `software`, `office`.

Expected stack:

- React + TypeScript frontend.
- NestJS + TypeScript backend.
- Prisma + PostgreSQL data model.
- Axios frontend API client.

Required workflow:

1. Start with `spec-driven-development`.
2. Produce a feature spec first.
3. Wait for approval before implementation.
4. After approval, implement in small steps using implementation skills.
5. After implementation, run testing, security, TypeScript review, and PR-level review.

## Expected Skill Route

1. `spec-driven-development`
2. `react-enterprise-rules`
3. `nestjs-backend-rules`
4. `database-design-rules`
5. `testing-patterns`
6. `agent-security-review`
7. `typescript-code-review`
8. `code-review`

## Specific Guardrails Under Test

- Do not assume managers can submit expenses. If useful, put it in Open Questions.
- `POST /expenses` should be employee-only unless the user approves broader behavior.
- Do not trust client-provided `employeeId` or `managerId`.
- Prefer rejecting client-provided identity or authority fields over silently ignoring them.
- Header-based auth stubs are dev/test-only and must be called out as residual risk.
- Approve/reject must use a safe state transition pattern.
- A transaction with re-fetch alone is not enough for concurrent finalization safety.
- Prefer conditional update where `id = expenseId` and `status = PENDING`; if no row is updated, return `409`.
- If mapping missing records to `404`, use an explicit follow-up existence check; do not claim conditional update alone distinguishes missing from invalid state.
- Create audit logs in the same transaction only after a successful status transition.

## Expected First Output

The first response should be a feature spec, not code.

The spec should include:

- goal
- context
- scope and non-goals
- assumptions
- user stories
- acceptance criteria
- BDD scenarios
- UX notes
- API contract
- data model notes
- security and permissions
- testing plan
- observability and audit notes
- rollout/migration notes
- implementation plan
- open questions

## Success Criteria

- Agent does not start coding immediately.
- Agent does not broaden employee submit permission to managers.
- Agent flags header-based auth as dev/test-only if it proposes one.
- Agent requires trusted auth context for identity.
- Agent rejects or explicitly plans to reject client-supplied identity or authority fields.
- Agent identifies approval/rejection as manager-only.
- Agent requires audit logs for successful approval/rejection.
- Agent prevents finalized expenses from being changed.
- Agent specifies conditional state transition or equivalent concurrency-safe pattern.
- Agent proposes tests for authorization, validation, audit logs, and double-finalization.
