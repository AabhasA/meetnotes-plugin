---
description: Recap a MeetNotes meeting — what was decided, what was agreed and who owes what. Use when the user asks what happened in a meeting, wants yesterday's or this morning's call summarised, or names a meeting and asks for the gist.
---

# Recap a meeting

`$ARGUMENTS` is what the user said about which meeting: a title, a person, a topic, a date,
or nothing at all.

1. **Find the meeting.**
   - Nothing given → `meetnotes_list_recordings` and take the most recent completed one.
   - A topic, person or phrase → `search`, then `fetch` the best hit.
   - Several plausible matches → list the titles with their dates and ask which one. Do not
     recap the wrong meeting and make the user read it to find out.
2. **Read it.** `meetnotes_get_transcript` gives the speaker-labelled transcript; the
   meeting record carries the minutes that were already written — summary, key takeaways,
   decisions, action items with owners. Prefer the stored minutes over re-summarising the
   raw transcript, and only go to the transcript for detail the minutes do not carry.
3. **Write the recap** in this shape, and keep it short enough to read on a phone:
   - one line on what the meeting was and when
   - **Decisions** — what was actually settled
   - **Action items** — owner → what → by when, only where the meeting said so
   - **Open** — what was raised and left unresolved
4. **Names.** Use the speaker names as MeetNotes has them. If a speaker is still
   "Speaker 2", say "Speaker 2" — do not invent a name from context, and mention once that
   naming the speaker in the app fixes it for every future meeting too.

Offer, but do not do unasked: an export of the minutes as a PDF or Word file
(`meetnotes_export_meeting`) if the user wants to send it on.
