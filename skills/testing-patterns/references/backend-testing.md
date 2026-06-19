# Backend Testing

## NestJS Service Tests

Use for:

- business rules
- error behavior
- authorization policy helpers
- orchestration logic

Mock:

- external APIs
- email providers
- payment gateways

Avoid mocking:

- the function under test
- simple domain code that should run directly

## Controller and API Tests

Use for:

- request validation
- route contracts
- auth behavior
- response shape
- HTTP status codes

## Database Tests

Use when:

- query behavior matters
- constraints matter
- transactions matter
- Prisma mappings matter

Prefer isolated test databases or transaction rollback patterns.

## Guards

Test:

- unauthenticated access
- insufficient permissions
- valid permissions
- resource ownership when guard handles it
