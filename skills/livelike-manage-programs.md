---
name: Manage LiveLike programs
description: List, inspect, create, update, and start/stop LiveLike programs that contain interactive widgets.
api: LiveLike REST API / @livelike/mcp
operations:
  - list_programs
  - get_program
  - create_program
  - update_program
  - program_action
auth: OAuth 2.0 Bearer — Admin Access Token
---

# Manage LiveLike programs

A **program** represents a piece of content inside LiveLike and is the container
for widgets. Use this skill to administer programs for an application.

## Steps
1. **List programs** — `list_programs` with filtering and pagination to find the
   program you want (`count`/`next`/`previous`/`results` envelope).
2. **Get a program** — `get_program` for the full detail of one program (or
   fetch by Custom Program ID).
3. **Create a program** — `create_program` inside an application; optionally set
   a Custom Program ID.
4. **Update a program** — `update_program` to change program attributes.
5. **Start / stop a program** — `program_action` to mark a program as started or
   stopped, which controls whether its widgets are live.

## Rules to follow
- Requires an **Admin Access Token** (`Authorization: Bearer …`).
- Paginate through `next` until it is null; do not assume a single page.
