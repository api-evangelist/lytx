---
name: Manage fleet vehicles
description: List, read, create, update and delete vehicles in the Lytx fleet, and read vehicle statuses.
api: openapi/lytx-vehicles-openapi.yml
operations: [Vehicle_GetVehicles, Vehicle_GetVehicle, Vehicle_AddVehicle, Vehicle_UpdateVehicle, Vehicle_DeleteVehicle, Vehicle_GetVehicleStatuses]
provider: lytx
---

# Manage fleet vehicles

## Goal
Full CRUD over the vehicles in a Lytx fleet.

## Auth
Bearer token in `Authorization` header. Write operations require a Full Access user at the appropriate group level.

## Steps
1. `Vehicle_GetVehicles` (GET) — list vehicles for a group (limit/offset, includeSubGroups).
2. `Vehicle_GetVehicle` (GET) — read one vehicle by identifier.
3. `Vehicle_AddVehicle` (POST) — create a vehicle.
4. `Vehicle_UpdateVehicle` (PUT) — update a vehicle.
5. `Vehicle_DeleteVehicle` (DELETE) — remove a vehicle.
6. `Vehicle_GetVehicleStatuses` (GET) — read the vehicle status reference.

## Conventions
- Group hierarchy: vehicles belong to a group (groupId); use includeSubGroups to traverse descendants.
- No idempotency-key; treat POST/PUT/DELETE as non-idempotent and check state before retrying.
