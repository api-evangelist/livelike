---
name: Create and authenticate a user profile
description: Create a LiveLike user profile (optionally by Custom ID) and obtain a Profile Access Token to act on behalf of an end user.
api: LiveLike REST API
operations:
  - create-user-profile
  - create-profile-by-custom-id
  - get-user-profile
auth: OAuth 2.0 Bearer
---

# Create and authenticate a user profile

Profiles represent your end users inside LiveLike. Creating a profile yields a
**Profile Access Token** scoped to that profile, used for widget interaction and
chat participation.

## Steps
1. **Create a profile** — `create-user-profile` (`POST /api/v1/profiles/`) to
   mint a new profile, or `create-profile-by-custom-id` to tie the profile to an
   identifier from your own system.
2. **Capture the Profile Access Token** returned on creation; use it as
   `Authorization: Bearer {profile-access-token}` for that user's requests.
3. **Read the profile** — `get-user-profile` (`GET /api/v1/profiles/{id}/`) or
   get-by-custom-id to fetch profile state.

## Rules to follow
- Use **Profile Access Tokens** for end-user actions (widgets, chat) — never
  embed Admin or Personal API tokens in client apps.
- For server-driven login integrations, mint tokens with
  Client-generated Access Tokens using your own user IDs.
- Base URL: `https://cf-blast.livelikecdn.com/api/v1/`.
