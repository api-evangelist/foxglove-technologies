---
name: Annotate Foxglove data with typed events
description: Define an event type with custom properties, then create, search and update events that mark points of interest in robot data.
api: openapi/foxglove-technologies-openapi-original.yml
base_url: https://api.foxglove.dev/v1
operations:
  - GET /event-types
  - POST /event-types
  - PATCH /event-types/{id}
  - GET /custom-properties
  - POST /custom-properties
  - GET /events
  - POST /events
  - GET /events/{id}
  - PATCH /events/{id}
  - DELETE /events/{id}
generated: '2026-08-16'
method: generated
source: openapi/foxglove-technologies-openapi-original.yml + https://docs.foxglove.dev/docs/data/events
---

# Annotate Foxglove data with typed events

Events mark a moment or a span in a device's data so it can be found again. The
Foxglove OpenAPI declares no operationIds, so steps name operations as
`METHOD /path` against `https://api.foxglove.dev/v1`.

## Before you start

Capabilities needed on the API key: `events.list`, `events.create`, `events.update`,
`events.delete`, `eventTypes.list`, `eventTypes.create`, `properties.list`,
`properties.create`.

## Steps

1. **Decide whether a type already exists.** `GET /event-types` lists the
   organization's event types. Reuse one rather than minting a near-duplicate —
   types are the validation and filtering vocabulary, and duplicates fragment search.
2. **Define custom properties if the type needs structured fields.**
   `GET /custom-properties` lists the typed metadata definitions;
   `POST /custom-properties` creates one. Expect `409` when the property already
   exists.
3. **Create the event type.** `POST /event-types` with a name, a `colorName` and the
   custom properties it validates. `PATCH /event-types/{id}` edits one later.
4. **Create the event.** `POST /events` with `deviceId`, `start`, `end` (omit `end`
   for an instantaneous event), `eventTypeId` and `properties`. Timestamps are RFC
   3339 UTC with nanosecond precision.
5. **Find events again.** `GET /events` filters and pages the collection;
   `GET /events/{id}` fetches one.
6. **Correct or retire.** `PATCH /events/{id}` updates metadata, properties or the
   event type; `DELETE /events/{id}` removes it.

## Rules an agent must follow

- **No idempotency key exists.** A retried `POST /events` produces a duplicate
  annotation. Search `GET /events` for the same device and time span before retrying.
- **`403` means the key lacks the capability**, not that the event is invalid — the
  endpoint's security requirement names exactly which capability it wanted.
- **Errors carry no code**, only `{"error": "<message>"}`. Do not parse the message
  string as an identity; branch on status.
- **Events fire webhooks.** `event.created` and `event.updated` are delivered
  at-least-once to any configured webhook; downstream consumers must deduplicate on
  `webhookId` + `webhookEventId`. If you are writing events in a loop, expect the
  consumer to see them more than once.

## Reference

- Data model: `data-model/foxglove-technologies-data-model.yml`
- Conventions: `conventions/foxglove-technologies-conventions.yml`
- Webhooks: `asyncapi/foxglove-technologies-webhooks.yml`
