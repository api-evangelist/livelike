---
name: Publish an interactive poll widget to a program
description: Create a LiveLike program and publish (or schedule) a text poll widget to it for a live audience.
api: LiveLike REST API / @livelike/mcp
operations:
  - create_program
  - create_text_poll_widget
  - schedule_widget
auth: OAuth 2.0 Bearer — Admin Access Token (LIVELIKE_ACCESS_TOKEN + LIVELIKE_CLIENT_ID)
---

# Publish an interactive poll widget

Use this to stand up a live poll for an event. Widgets belong to a **program**, so
create (or reuse) a program first, then create the poll widget under it.

## Prerequisites
- An **Admin Access Token** and your **Client ID** (see the Authentication reference).
- Base URL: `https://cf-blast.livelikecdn.com/api/v1/`.

## Steps
1. **Create or select a program** — `create_program` (MCP) or `POST` create-program
   (REST). A program represents the content the widget is attached to. Supply a
   Custom Program ID if you want to address it by your own system's identifier.
2. **Create the text poll widget** — `create_text_poll_widget` (MCP) or the REST
   "Creating Polls" flow. Provide the question and the poll options.
3. **Schedule or publish** — `schedule_widget` (MCP) to publish at a specific
   time, or publish immediately. Live widget updates are delivered over the
   subscribed data channels.

## Rules to follow
- Authenticate with `Authorization: Bearer {admin-access-token}`; keep Admin
  tokens server-side (never expose them in a client).
- Responses are paginated with a `count`/`next`/`previous`/`results` envelope.
- On `4xx`, fix the request before retrying; `5xx` is transient and safe to retry.
