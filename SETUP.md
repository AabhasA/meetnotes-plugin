---
description: Connect this Claude session to the user's MeetNotes account, or fix a MeetNotes connection that is failing. Use when a MeetNotes tool returns an authentication or authorization error, when no MeetNotes tools are available, or when the user asks how to connect MeetNotes.
---

# Connecting MeetNotes

The plugin ships one remote MCP server, `meetnotes`, at `https://getmeetnotes.com/mcp`
(Streamable HTTP). There is nothing to install and no API key to paste for a normal user.

## Normal sign-in

1. The server uses OAuth 2.1 with PKCE and dynamic client registration, so the client
   handles the whole handshake. In Claude Code, run `/mcp` and pick **meetnotes** →
   **Authenticate**; a browser window opens.
2. Sign in with **the same email the user uses in the MeetNotes app**. A different email
   is a different account with different meetings — this is the single most common
   support question. If they signed into the app with Apple or Google, use the same button.
3. Approve the scopes. They are read-only except for exports, audio import and the
   notetaker invitation:
   `meetings:read`, `actions:read`, `exports:create`, `transcripts:create`.
4. Confirm it worked by calling `meetnotes_get_capabilities` — it returns the plan, the
   minutes balance and which tools this account may use.

## If it fails

- **401 / "not authenticated"** — the access token expired. Re-run the authenticate step.
- **403 / a tool refuses** — the account's plan does not include that tool. Call
  `meetnotes_get_capabilities` and tell the user which plan the tool needs; do not retry.
- **No MeetNotes tools listed at all** — the plugin is installed but the MCP server has
  not started. Run `/reload-plugins`, or restart the session.
- **An empty meeting list on a brand-new account** — nothing is wrong. The user has not
  recorded a meeting yet. Point them at the MeetNotes app (iOS, Android, Mac, Windows) or
  at inviting the notetaker to a call.

## For teams with a partner key

Organisations that already hold a MeetNotes partner API key can send it as a bearer token
instead of running OAuth. That is a server-to-server arrangement — direct the user to
support@getmeetnotes.com rather than configuring it ad hoc.

## Never do

- Never offer to sell minutes, quote a price, or link to a checkout. Minutes and plans are
  bought in the MeetNotes app or on getmeetnotes.com, never through this connection.
- Never guess at a meeting the user cannot see. If a search returns nothing, say so.
