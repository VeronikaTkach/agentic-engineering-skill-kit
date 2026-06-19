# Backend Review

## NestJS Boundaries

- Controllers should stay thin.
- Services should contain business logic.
- DTOs should validate input.
- Guards should enforce route-level auth.
- Persistence should not be called directly from controllers.

## API Safety

- Validate body, params, and query input.
- Do not trust client-provided user IDs.
- Do not return sensitive internal fields.
- Use appropriate HTTP exceptions.
- Bound pagination limits.

## Authorization

- Authentication is not authorization.
- Check resource ownership.
- Check role or permission requirements.
- Avoid broad admin-only shortcuts when domain permissions matter.

## Background Work

- Long-running jobs should be idempotent where possible.
- Avoid unbounded retries.
- Log enough context for debugging.
