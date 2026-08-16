---
name: Upload and track a Foxglove recording
description: Upload an MCAP or ROS bag to the Foxglove data platform for a device, then follow it through import until it is queryable.
api: openapi/foxglove-technologies-openapi-original.yml
base_url: https://api.foxglove.dev/v1
operations:
  - POST /data/upload
  - GET /devices
  - GET /recordings
  - GET /recordings/{keyOrId}
  - GET /data/pending-imports
  - GET /data/import-errors
  - GET /data/coverage
generated: '2026-08-16'
method: generated
source: openapi/foxglove-technologies-openapi-original.yml + https://docs.foxglove.dev/docs/data/importing-data
---

# Upload and track a Foxglove recording

The Foxglove OpenAPI declares **no operationIds**, so every step below names the
operation the only way the specification identifies it: `METHOD /path` against
`https://api.foxglove.dev/v1`.

## Before you start

- Get an API key from an organization admin (Settings → API keys). Send it as
  `Authorization: Bearer fox_sk_...` on every request.
- The key must carry the capability each endpoint declares. This flow needs
  `data.upload`, `devices.list`, `recordings.list`, `data.imports.pending.list` and
  `data.coverage.list`.
- All timestamps are RFC 3339 UTC with up to nine fractional digits
  (`2026-08-16T09:15:30.123456789Z`).

## Steps

1. **Find the device.** `GET /devices` lists the robots in the project; `GET
   /devices/{nameOrId}` resolves one by name or id. Recordings are attached to a
   device, so resolve this first. If the device does not exist yet, `POST /devices`
   creates it — expect `409` if the name is already taken.
2. **Upload the file.** `POST /data/upload` uploads the MCAP or ROS bag. Supply the
   device and, if you want a stable handle of your own, a `key`; you can then address
   the recording later as `GET /recordings/{keyOrId}` using your key rather than the
   Foxglove id.
3. **Watch the import.** Upload and availability are not the same moment.
   `GET /data/pending-imports` lists work still in flight; `GET /recordings/{keyOrId}`
   returns the recording with an `importStatus`. Poll the recording rather than
   assuming success.
4. **Check for failures.** `GET /data/import-errors` lists imports that failed. Do
   this before concluding that a missing recording was never uploaded.
5. **Confirm the data is queryable.** `GET /data/coverage` reports the time spans
   available for a device. A recording that imported successfully widens its device's
   coverage; that is the check that the data is actually usable, not merely stored.
6. **Optional — group it.** `POST /sessions` creates a session and
   `PATCH /sessions/{keyOrId}` updates which recordings belong to it. Sessions group
   recordings from a single device.

## Rules an agent must follow

- **There is no idempotency key.** Retrying `POST /data/upload` or `POST /devices`
  creates a second write. Before retrying a POST that may have succeeded, re-read the
  collection (`GET /recordings`, `GET /devices`) and only retry if the resource is
  genuinely absent.
- **Pagination is offset-based and uncounted.** `limit` defaults to 2000 and cannot
  exceed 2000 (`400` if you try); use `offset` to page, and `sortBy`/`sortOrder` where
  the endpoint documents them. Responses are bare arrays with no total, so a full page
  does not tell you whether more remain — request `limit+1` or page until short.
- **Errors are free text.** Every failure is `{"error": "<message>"}` with no code.
  Branch on the HTTP status: `400` bad parameters, `403` the key lacks the capability,
  `404` wrong id or wrong project, `409` already exists.
- **Back off on 429.** Rate limits are unpublished. On `429`, honour `Retry-After` and
  retry with exponential backoff.
- **Prefer Recordings over Imports.** The `/data/imports` endpoints are deprecated in
  the specification; use `/recordings`.

## Reference

- Conventions: `conventions/foxglove-technologies-conventions.yml`
- Errors: `errors/foxglove-technologies-problem-types.yml`
- Rate limits: `rate-limits/foxglove-technologies-rate-limits.yml`
- Webhooks (get told when an import finishes instead of polling):
  `asyncapi/foxglove-technologies-webhooks.yml`
