---
name: find-coach-or-program
description: Search PGA coaches or group programs near a city or ZIP. Use when the user asks to find a coach, clinic, camp, or lesson near them.
---

# Find a PGA coach or program

1. Ask for a location if the user has not provided one (city, ZIP, or area).
2. If they want **private lessons**, call `search_golf_coaches` with `searchLocation` (optional `searchRadius`, default 25 miles).
3. If they want **clinics, camps, classes, or group events**, call `search_golf_programs` with `searchLocation` (optional `searchRadius`, default 50 miles).
4. Summarize results in plain language (names, offerings, dates, prices, facilities). Link to profile, program, or booking URLs from the tool response.
5. Offer to check availability or book once they pick a coach.

Do not expose internal IDs (`slug`, `offeringId`, program `id`, pagination cursors) in chat.
