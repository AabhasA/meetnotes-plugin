---
description: Send the MeetNotes Notetaker into a Zoom, Google Meet or Microsoft Teams call so the call is transcribed and minuted, or transcribe an audio file the user has. Use when the user pastes a meeting link and wants it recorded, asks to have a call covered, or has a recording to turn into minutes.
---

# Get a call or a recording into MeetNotes

## A live or upcoming call

The user gives a Zoom, Google Meet or Microsoft Teams link.

1. `meetnotes_invite_notetaker` with the link, and the start time if the call is later. A
   join can be booked up to 7 days ahead.
2. **Tell the user what will happen, before they walk into the call**: the bot joins as a
   visible participant named "MeetNotes Notetaker", and **the host has to admit it from the
   waiting room** — a booked join that nobody admits records nothing. Everyone on the call
   sees it is there.
3. An account may have at most **2 invitations waiting or in a call at once**. If the call
   is refused for that reason, say which bookings are already holding the slots.
4. The call spends the account's minutes like any other meeting.
5. Afterwards the meeting shows up like any other: recap it, or pull its action items.

A booking can be cancelled, and the bot asked to leave, from the MeetNotes app.

## A recording the user already has

`meetnotes_import_audio` takes an audio file — one attached to the conversation, or at a
URL the server is willing to fetch. It comes back as a job; `meetnotes_get_job` reports
progress, and the finished meeting has the transcript and the minutes like any other.

Long files take a while. Report the job as running rather than waiting in a loop, and check
back when the user asks.

## Say this once, not every time

A call is being recorded and transcribed. Whether the other people on it need to be told —
and in several places they legally do — is the user's call, not ours, but it is worth one
line the first time they use the notetaker.
