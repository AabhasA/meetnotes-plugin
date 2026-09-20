---
description: Pull the action items out of MeetNotes meetings — everything owed by or to the user, across one meeting or the last few weeks. Use when the user asks what they committed to, what they are waiting on, what is still open from a meeting, or wants a to-do list out of their meetings.
---

# Action items from meetings

`$ARGUMENTS` may name a meeting, a person, a project or a period ("this week", "since
Monday"). If it is empty, cover the last 14 days.

1. **Scope it.** `meetnotes_list_recordings` for the window, or `search` when the user
   named a topic or a person. For a single named meeting, `fetch` it directly.
2. **Collect.** `meetnotes_list_actions` per meeting. Each item carries the text, the owner
   as the meeting recorded it, and a due date when one was actually said.
3. **Group by owner, not by meeting.** That is what makes it a to-do list rather than a
   second set of minutes. Put the user's own items first.
4. **Format** each as: `owner — what — due (meeting, date)`. Keep the meeting name on the
   line so any item can be traced back.
5. **Flag the gaps** at the end, briefly: items with no owner, and items with no date. Those
   are the ones that quietly never happen.

Rules:

- **Never invent an owner or a deadline.** If the meeting did not assign it, write
  "unassigned" or "no date". Guessing who owns a task is how a task gets dropped by two
  people at once.
- Quote the action item close to how it was said; do not rewrite a commitment into
  something firmer or vaguer than the meeting made it.
- If the user asks to push these into a task tracker, do it with whatever tool they have
  connected — this plugin only reads them out of the meetings.
