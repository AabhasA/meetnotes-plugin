# MeetNotes plugin for Claude

Your [MeetNotes](https://getmeetnotes.com) meetings inside Claude — search them, read the
speaker-labelled transcript, pull the open action items, export the minutes as a PDF or
Word file, and send the MeetNotes Notetaker into a Zoom, Google Meet or Microsoft Teams
call.

MeetNotes records the meetings that have no call at all — a room, on the phone you already
own — as well as online calls, and writes the minutes: summary, key takeaways, decisions,
and action items with owners.

## Install

```
/plugin marketplace add anthropics/claude-plugins-community
/plugin install meetnotes@claude-community
```

Or, to try it straight from this repository:

```
claude --plugin-dir ./meetnotes-plugin
```

## Connect

The plugin bundles one remote MCP server — `https://getmeetnotes.com/mcp`, Streamable HTTP.
Nothing to install, no key to paste.

1. Run `/mcp`, pick **meetnotes**, and authenticate. OAuth 2.1 with PKCE and dynamic client
   registration; a browser window does the rest.
2. **Sign in with the same email you use in the MeetNotes app.** A different email is a
   different account.
3. Approve the scopes: `meetings:read`, `actions:read`, `exports:create`,
   `transcripts:create`.

No MeetNotes account yet? The app is free to start with 100 minutes included —
[iOS](https://getmeetnotes.com/), [Android](https://getmeetnotes.com/),
[Mac and Windows](https://getmeetnotes.com/download/).

## What you get

| Skill | What it does |
|---|---|
| `/meetnotes:recap` | What was decided in a meeting, who owes what, what was left open |
| `/meetnotes:action-items` | Every commitment across the last two weeks, grouped by owner |
| `/meetnotes:find-meetings` | Search the archive and quote what was actually said |
| `/meetnotes:export-minutes` | Minutes as PDF, Word, Markdown or JSON, to send on |
| `/meetnotes:notetaker` | Send the Notetaker into a call, or import a recording |
| `/meetnotes:setup` | Connect the account, or fix a connection that is failing |

Claude also reaches for these on its own when a request is about your meetings.

### Tools on the MCP server

`meetnotes_get_capabilities` · `meetnotes_list_recordings` · `search` · `fetch` ·
`meetnotes_get_transcript` · `meetnotes_list_actions` · `meetnotes_export_meeting` ·
`meetnotes_import_audio` · `meetnotes_invite_notetaker` · `meetnotes_about` ·
`meetnotes_get_job`

## What it can and cannot touch

Read-only over your meetings, except for three things you ask for explicitly: creating an
export file, importing an audio file you supply, and inviting the Notetaker to a call.
It cannot delete a meeting, change your minutes balance, or buy anything — minutes and
plans are handled in the MeetNotes app, never through this connection.

Privacy policy: <https://getmeetnotes.com/privacy.html>

## Support

<support@getmeetnotes.com> · [getmeetnotes.com/mcp](https://getmeetnotes.com/mcp/)

Published by Ultragames Entertainment Private Limited. This repository holds the plugin
wrapper — the manifest, the MCP pointer and the skills — under MIT. The MeetNotes service
itself is a hosted product.
