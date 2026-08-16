---
name: Consume Foxglove webhooks safely
description: Receive Foxglove's eight webhook events, verify the HMAC signature, deduplicate at-least-once deliveries, and reconcile against the REST API.
api: openapi/foxglove-technologies-openapi-original.yml
base_url: https://api.foxglove.dev/v1
operations:
  - GET /recordings/{keyOrId}
  - GET /sessions/{keyOrId}
  - GET /devices/{nameOrId}
  - GET /events/{id}
events:
  - recording.created
  - recording.imported
  - session.created
  - device.created
  - device.updated
  - event.created
  - event.updated
  - ping
generated: '2026-08-16'
method: generated
source: https://docs.foxglove.dev/docs/webhooks + https://docs.foxglove.dev/docs/webhooks/security + openapi/foxglove-technologies-openapi-original.yml
---

# Consume Foxglove webhooks safely

Foxglove pushes eight event types to an HTTPS endpoint you configure. Delivery is
at-least-once, so a correct consumer is defined by what it does with duplicates and
with unverified bodies — not by parsing the payload.

## The events

| Event | Fires when |
|---|---|
| `recording.created` | A recording is created. For direct uploads this is the same moment as `recording.imported`. |
| `recording.imported` | A recording finishes importing. |
| `session.created` | A new session is created. |
| `device.created` | A device is added to the organization. |
| `device.updated` | A device is updated. |
| `event.created` | An event is added. |
| `event.updated` | An event is updated. |
| `ping` | Connectivity test for your endpoint. |

## Steps

1. **Verify the signature before parsing.** Compute a SHA-256 HMAC over the **raw
   request body bytes**, keyed with your webhook token, and compare it to the
   `fg-webhook-signature` header. Compare in constant time. Never parse or act on an
   unverified body, and never re-serialize the body before hashing.
2. **Reject stale deliveries.** Drop anything whose `deliveryAttemptedAt` is more than
   a minute old. That is the published replay guard.
3. **Deduplicate.** Every payload carries `webhookId` and `webhookEventId`. Store the
   pair and drop repeats — delivery is at-least-once and Foxglove retries a failure up
   to five times with increasing delay.
4. **Answer fast.** Return a `2xx` within **5 seconds**. Enqueue the work; do not do it
   inline. A slow `200` is a failure and will be retried.
5. **Read the envelope, then the body.** Every payload carries `type`, `timestamp`,
   `attemptedAt`, `webhookId`, `webhookEventId`; the rest is per-type. Switch on `type`
   and treat an unknown `type` as a no-op rather than an error — new event types can
   appear.
6. **Reconcile against REST for anything that matters.** The payload is a summary. For
   the authoritative record fetch `GET /recordings/{keyOrId}`,
   `GET /sessions/{keyOrId}`, `GET /devices/{nameOrId}` or `GET /events/{id}` before
   taking an irreversible action.
7. **Do not treat `recording.created` as "ready".** Wait for `recording.imported`, or
   check `importStatus` on the recording, before querying its data.

## Rules an agent must follow

- Verify first, parse second, act third.
- Duplicate delivery is normal, not an incident.
- The webhook token is a secret of equal weight to an API key; rotate it if it leaks,
  which invalidates in-flight signatures.
- `POST /site-bucket-notifications` is the opposite direction — object storage
  notifying Foxglove — and is not part of this flow.

## Reference

- Event surface: `asyncapi/foxglove-technologies-webhooks.yml`
- Conventions: `conventions/foxglove-technologies-conventions.yml`
- Docs: https://docs.foxglove.dev/docs/webhooks
