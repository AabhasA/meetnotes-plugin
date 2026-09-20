---
description: Export MeetNotes minutes as a PDF, Word, Markdown or JSON file so they can be sent to people who have no MeetNotes account. Use when the user wants to share, send, download or attach the minutes of a meeting.
---

# Export minutes

`$ARGUMENTS` names the meeting and, sometimes, the format.

1. **Identify the meeting** — `search` or `meetnotes_list_recordings`, then `fetch`. If more
   than one matches, ask before exporting; an export is a file the user will forward.
2. **Pick the format.** Ask only if the user did not say:
   - **PDF** — to send to someone who should read it, not edit it. The default.
   - **Word** — when they want to edit the minutes before sending.
   - **Markdown** — to paste into a doc, wiki or ticket.
   - **JSON** — to feed another system.
3. `meetnotes_export_meeting` with the meeting and the format. It returns a link to the
   file.
4. **Hand over the link** and say what is in the file: summary, key takeaways, decisions,
   action items with owners, and the speaker-labelled transcript.

Before sending it onward:

- If the user is about to forward minutes outside their company, say once — briefly — what
  the file contains, so a confidential aside does not leave the building by accident. Say
  it; do not refuse.
- The dates in the file are in the meeting owner's timezone, not the reader's.
- Do not paste the whole transcript into the chat when the user asked for a file. The file
  is the deliverable.
