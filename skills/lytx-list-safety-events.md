---
name: List and analyze fleet safety events
description: Retrieve DriveCam safety events for a fleet, enrich them with metadata, statuses, behaviors and triggers, and analyze driving risk.
api: openapi/lytx-safety-openapi.yml
operations: [Events_GetEvents, Events_GetEventsWithMetadata, Events_GetEventStatuses, Events_GetEventBehaviors, Events_GetEventTriggers]
provider: lytx
---

# List and analyze fleet safety events

## Goal
Pull the safety events a Lytx DriveCam fleet has generated and enrich each with its status, behaviors, and triggers so an agent can summarize risk.

## Auth
Get a bearer token from `POST https://login.lytx.com/api/auth/user` (username/password) or Advanced (OIDC/SSO) auth. Send `Authorization: Bearer {token}` on every request. Tokens last ~1 hour.

## Steps
1. Call `Events_GetEvents` (GET) with `startDate`/`endDate` and `limit`/`offset` to page the event list for the group.
2. For richer records, use `Events_GetEventsWithMetadata` instead of the bare list.
3. Resolve reference data once: `Events_GetEventStatuses`, `Events_GetEventBehaviors`, and `Events_GetEventTriggers` to map status/behavior/trigger codes to labels.
4. Optionally call `Events_GetDynamicRisk` to fetch the dynamic risk scoring for the window.

## Conventions
- Pagination is offset/limit; order with `order`/`sortProperty`.
- Errors are plain HTTP status codes (401 = bad/missing token, 403 = not authorized, 404 = bad endpoint/param). See errors/lytx-error-codes.yml.
