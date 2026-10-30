---
name: play-golf
description: >-
  Find PGA coaches or group programs, check lesson availability, and book a
  lesson via the PGA Play Golf MCP server. Use when the user wants a golf
  lesson, coaching, a golf camp, a junior clinic, lesson times, or to book
  with a PGA Professional.
---

# Play golf with PGA Coach

Use the **PGA Play Golf** MCP server (`https://mcp.pga.com/mcp`). Do not guess coach or program data; call the tools below.

## Tool selection

| User intent                                            | Tool                          |
| ------------------------------------------------------ | ----------------------------- |
| Private lessons, compare coaches, "find a pro near me" | `search_golf_coaches`         |
| Clinics, camps, classes, group events, programs        | `search_golf_programs`        |
| Schedule, openings, or times for a **chosen** coach    | `get_golf_coach_availability` |
| Book or reserve a specific offering and time           | `book_golf_lesson`            |

- If they want availability but have not picked a coach, run `search_golf_coaches` (or reuse a coach from `search_golf_programs`) and ask them to choose.
- For programs, present titles, dates, prices, coaches, and facilities; send them to each program's URL to register. Do not expose internal IDs (`slug`, `offeringId`, program `id`, pagination cursors) in user-facing text.

## Booking workflow

1. Resolve the coach (search or prior context).
2. Call `get_golf_coach_availability` with the coach's internal `slug` (tool use only).
3. Let the user pick an offering and a time from returned `availableTimes` (exact ISO8601 for `startDateTime`).
4. Collect participant details:
   - **Adult (18+):** first name, last name, email; phone optional.
   - **Junior (17 or younger):** student first/last name, guardian first/last name, email; phone optional.
5. Call `book_golf_lesson` with `offeringId`, `startDateTime`, and the `student` object (`type: "adult"` or `type: "junior"` plus the fields above).

## Authentication

- **Search and availability:** Callable without sign-in on Cursor (mixed auth).
- **`book_golf_lesson`:** Requires a PGA.com OAuth token with scope `mcp:coaching`. If the tool returns an auth challenge, guide the user through MCP OAuth in Cursor, then retry.

## After booking

- Share `lesson.confirmationCode` when returned.
- If `continuationUrl` is returned, send the user there to finish payment or other steps.
- On failure, help them pick another time or offering.
