---
name: Onboard a Foxglove device and issue its tokens
description: Register a robot as a Foxglove device, issue and manage its device token, attach custom properties, and verify data coverage.
api: openapi/foxglove-technologies-openapi-original.yml
base_url: https://api.foxglove.dev/v1
operations:
  - GET /projects
  - POST /devices
  - GET /devices/{nameOrId}
  - PATCH /devices/{nameOrId}
  - DELETE /devices/{nameOrId}
  - POST /device-tokens
  - GET /device-tokens
  - PATCH /device-tokens/{id}
  - DELETE /device-tokens/{id}
  - GET /custom-properties
  - POST /actions/devices/{nameOrId}/update-property-time-interval
  - GET /devices/{nameOrId}/property-time-intervals
  - GET /data/coverage
generated: '2026-08-16'
method: generated
source: openapi/foxglove-technologies-openapi-original.yml + https://docs.foxglove.dev/docs/fleet/device-tokens
---

# Onboard a Foxglove device and issue its tokens

Bringing a robot onto the platform is: pick the project, create the device, issue the
credential the robot itself will use, then confirm data is arriving. Operations are
named `METHOD /path` because the specification declares no operationIds.

## Before you start

Capabilities: `projects.list`, `devices.create`, `devices.list`, `devices.update`,
`deviceTokens.create`, `deviceTokens.list`, `deviceTokens.update`, `properties.list`,
`data.coverage.list`. Only an organization admin can mint the API key you are using.

## Steps

1. **Pick the project.** `GET /projects` lists the containers that own devices and
   recordings. A device belongs to exactly one project via `projectId`.
2. **Create the device.** `POST /devices` with a name and the project. A `409` means
   the name is taken — resolve it with `GET /devices/{nameOrId}` and reuse it rather
   than inventing a variant name.
3. **Set retention and behaviour.** `PATCH /devices/{nameOrId}` sets
   `retainRecordingsSeconds`, `enabled`, `remoteAccessEnabled` and
   `autoDeleteAfterImport`. Decide retention before data starts flowing, not after.
4. **Issue the device token.** `POST /device-tokens` creates the credential the robot
   or its Foxlet agent presents. This is a *different* credential class from your API
   key — do not put an organization API key on a robot.
5. **Manage the token's lifetime.** `GET /device-tokens` lists them,
   `PATCH /device-tokens/{id}` toggles `enabled`, `DELETE /device-tokens/{id}` revokes
   one. Revocation is the only rotation mechanism published; there is no expiry
   contract, so rotation is your responsibility.
6. **Attach fleet metadata.** `GET /custom-properties` lists the typed properties;
   set a device's value over a time window with
   `POST /actions/devices/{nameOrId}/update-property-time-interval`, and read the
   history back with `GET /devices/{nameOrId}/property-time-intervals`. Use this when
   a property changes over the device's life (a firmware version, a deployment site)
   rather than overwriting a single current value.
7. **Verify data is arriving.** `GET /data/coverage` shows the time spans the device
   has data for. Empty coverage after an upload means the import has not completed —
   check `GET /data/pending-imports` and `GET /data/import-errors`.

## Rules an agent must follow

- **No idempotency key.** `POST /devices` and `POST /device-tokens` are not safe to
  blind-retry; a retried token creation leaves an extra live credential. Re-list
  before retrying.
- **Deleting a device is destructive** and is not reversible through the API.
  `DELETE /devices/{nameOrId}` should require explicit human confirmation.
- **`403` names a missing capability**, not a permissions bug in your code.
- **Honour `Retry-After` on `429`.** No numeric rate limit is published.

## Reference

- Authentication and the full 48-capability list:
  `authentication/foxglove-technologies-authentication.yml`
- Data model: `data-model/foxglove-technologies-data-model.yml`
- Device docs: https://docs.foxglove.dev/docs/data/devices
