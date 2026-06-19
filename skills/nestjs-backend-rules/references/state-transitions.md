# State Transitions

## Purpose

Use explicit state transition rules for workflows such as approval, rejection, cancellation, publishing, payment, and finalization.

## Rules

- Define allowed source and target states.
- Reject invalid transitions with a clear error.
- Do not trust the client to tell the current state.
- Keep transition logic in the service/domain layer.
- Write audit logs in the same transaction as successful transitions.

## Conditional Update Pattern

For concurrent approve/reject style workflows, prefer a conditional update:

```text
update only where id = targetId and status = expectedCurrentStatus
```

If no row is updated:

- return `409 Conflict`
- do not create an audit log
- do not report success

Then create the audit log in the same transaction after the state transition succeeds.

## Why Re-Fetch Alone Is Not Enough

Fetching a record inside a transaction and then updating it can still be fragile if two requests observe the same state before either transition commits.

Use one of:

- conditional update
- row lock
- serializable transaction

For Prisma applications, conditional update or `updateMany` with the expected current state is often the simplest pattern.

## Review Checklist

- Are allowed transitions explicit?
- Is the current state checked server-side?
- Is the update conditional on expected current state?
- Does invalid transition return 409?
- Is audit logging atomic with the successful transition?
- Are double-submit or race conditions tested?
