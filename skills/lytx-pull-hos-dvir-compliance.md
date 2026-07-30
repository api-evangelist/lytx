---
name: Pull HOS logs and DVIR inspections
description: Retrieve Hours-of-Service logs and DVIR inspection records for ELD/FMCSA compliance workflows.
api: openapi/lytx-hos-openapi.yml
operations: [Hos_GetHosLogs, Hos_GetHosLogs_ByUser, getDvirs, getDvirById, getInspectionLists]
provider: lytx
---

# Pull HOS logs and DVIR inspections

## Goal
Collect Hours-of-Service (HOS) logs and Driver Vehicle Inspection Reports (DVIR) for compliance reporting.

## Auth
Bearer token in `Authorization` header.

## Steps
1. `Hos_GetHosLogs` (GET) — HOS logs for the group over a date window (startDate/endDate).
2. `Hos_GetHosLogs_ByUser` (GET) — HOS logs scoped to a specific driver/user.
3. `getDvirs` (GET, openapi/lytx-dvir-openapi.yml) — list DVIR inspection reports.
4. `getDvirById` (GET) — one DVIR report by id.
5. `getInspectionLists` (GET) — the inspection-list templates.

## Conventions
- Date filtering with startDate/endDate; offset/limit pagination.
- HOS/DVIR are FMCSA ELD-domain data; treat as compliance records.
