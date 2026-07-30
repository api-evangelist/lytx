---
name: Search events and retrieve video media
description: Find a vehicle, search its video-platform events, and retrieve the video media / timeline for an event.
api: openapi/lytx-video-openapi.yml
operations: [Vehicle_GetVehicles, Event_SearchEvents, Event_GetEventViewMedia, Vehicle_GetVehicleTimeline, Event_CreateEvent]
provider: lytx
---

# Search events and retrieve video media

## Goal
Locate a vehicle, search the events it produced on the Lytx video platform, and pull the associated video media.

## Auth
Bearer token in `Authorization` header (see conventions/lytx-conventions.yml).

## Steps
1. `Vehicle_GetVehicles` (GET) to find the target vehicle and its identifier.
2. `Event_SearchEvents` (POST) with a time window / vehicle filter to find events.
3. `Event_GetEventViewMedia` (GET) to obtain the viewable video media for a specific event.
4. `Vehicle_GetVehicleTimeline` (GET) to place the event on the vehicle's timeline.
5. To register a custom event, use `Event_CreateEvent` (POST).

## Conventions
- Offset/limit pagination; date filtering via startDate/endDate.
- Video/media retrieval may be asynchronous — poll status where provided.
