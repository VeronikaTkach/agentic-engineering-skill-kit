# Auth, Data, and Secrets

## Authentication

- Do not trust client-provided user IDs.
- Derive identity from trusted auth context.
- Keep session and access tokens scoped and short-lived.
- Do not put tokens in logs, prompts, screenshots, or client bundles.

## Authorization

Authentication answers who the actor is.

Authorization answers whether that actor can perform this action on this resource.

Check:

- role or permission requirements
- resource ownership
- tenant boundary
- environment boundary
- action type
- approval requirement

## Sensitive Data

Sensitive data includes:

- PII
- credentials
- tokens
- payment data
- private business data
- internal URLs
- customer records
- audit logs

Rules:

- return only fields needed by the caller
- mask PII in logs when possible
- avoid logging request bodies for sensitive endpoints
- use explicit response mappers instead of raw database records
- avoid broad exports

## Secrets

Reject:

- hardcoded API keys
- secrets in examples
- secrets in `.env` committed to source control
- secrets pasted into prompts
- service-role keys in browser code

Prefer:

- environment variables
- secret managers
- short-lived tokens
- scoped credentials

## Database Safety

Review:

- destructive operations
- bulk updates
- missing `where` clauses
- transaction boundaries
- raw SQL interpolation
- missing tenant filters
- missing ownership filters
- migration rollout and rollback

High-risk database actions require explicit approval.
