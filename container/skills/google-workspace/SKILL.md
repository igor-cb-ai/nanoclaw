---
name: google-workspace
description: Access Gmail, Google Calendar, Drive, Docs, and Sheets via the gws CLI. Use for reading/sending emails, checking or creating calendar events, listing Drive files, and working with Docs or Sheets. Use whenever the user asks about their email, calendar, or Google files.
allowed-tools: Bash(gws:*)
---

# Google Workspace CLI (gws)

Access Gmail, Calendar, Drive, Docs, Sheets, and more via `gws` Bash commands. Returns structured JSON.

## Gmail

```bash
# List recent emails
gws gmail messages list --params '{"maxResults": 10}'

# Read a message (replace MESSAGE_ID)
gws gmail messages get --params '{"id": "MESSAGE_ID", "format": "full"}'

# Send an email
gws gmail messages send --body '{"raw": "<base64-encoded RFC 2822 message>"}'

# Search emails
gws gmail messages list --params '{"q": "from:someone@example.com is:unread", "maxResults": 5}'
```

## Calendar

```bash
# List today's events
gws calendar events list --params '{"calendarId": "primary", "maxResults": 10, "timeMin": "'$(date -u +%Y-%m-%dT%H:%M:%SZ)'"}'

# Create an event
gws calendar events insert --params '{"calendarId": "primary"}' --body '{
  "summary": "Meeting",
  "start": {"dateTime": "2026-03-21T10:00:00-03:00"},
  "end": {"dateTime": "2026-03-21T11:00:00-03:00"}
}'
```

## Drive

```bash
# List files
gws drive files list --params '{"pageSize": 10}'

# Search files
gws drive files list --params '{"q": "name contains '\''report'\''", "pageSize": 10}'
```

## Discover any API method

```bash
gws schema gmail.users.messages.list      # Gmail list params
gws schema calendar.events.list           # Calendar list params
gws schema drive.files.list               # Drive list params
```

## Auth status

```bash
gws auth status   # Check authentication and scopes
```
