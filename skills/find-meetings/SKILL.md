---
description: Search MeetNotes meetings and read what was actually said. Use when the user asks when something was discussed, what a named person said about a topic, whether a subject ever came up, or wants to quote a meeting.
---

# Search the meeting archive

`$ARGUMENTS` is the thing to look for: a topic, a client, a number, a phrase, a person.

1. `search` across the account's meetings. It matches the transcripts, so a phrase actually
   spoken works better than a title guess.
2. `fetch` the meetings worth opening. For a question about wording — who said it, how it
   was put, what number was quoted — go to `meetnotes_get_transcript` and read the turns
   around the hit rather than the summary.
3. **Answer with the quote and the anchor**: the speaker, the meeting, the date. A search
   result nobody can trace back is not worth much.
4. If nothing matches, say nothing matched and suggest one or two other phrasings. Never
   assemble a plausible answer out of other meetings and present it as the one they asked
   about.

Notes:

- Meetings can switch language mid-sentence; a search in English may well sit inside a
  meeting held in another language. Quote the line as it was spoken and translate beside
  it, rather than silently replacing it.
- Recordings still processing will not have a transcript yet. `meetnotes_get_job` says
  where a recording is; tell the user to try again shortly rather than reporting the
  meeting as empty.
