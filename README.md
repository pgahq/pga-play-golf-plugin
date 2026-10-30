# PGA Play Golf

Cursor plugin for the PGA of America MCP server. Find a PGA coach or group program near you, check lesson availability, and book a lesson from Cursor.

## What's included

| Component | Path                                | Purpose                                             |
| --------- | ----------------------------------- | --------------------------------------------------- |
| Manifest  | `.cursor-plugin/plugin.json`        | Plugin metadata and logo                            |
| MCP       | `mcp.json`                          | PGA Play Golf MCP server at `https://mcp.pga.com/mcp` |
| Skill     | `skills/play-golf/SKILL.md`         | Tool routing and booking workflow                   |
| Rule      | `rules/pga-play-golf-mcp.mdc`       | Tool selection and privacy guardrails               |
| Command   | `commands/find-coach-or-program.md` | Search for coaches or programs near a location      |
| Logo      | `assets/logo.svg`                   | PGA of America mark for the marketplace listing     |
| License   | `LICENSE`                           | MIT                                                 |
| Changelog | `CHANGELOG.md`                      | Release notes                                       |

## Tools

| Tool                          | Purpose                                                                |
| ----------------------------- | ---------------------------------------------------------------------- |
| `search_golf_coaches`         | Find PGA coaches for private lessons near a location                   |
| `search_golf_programs`        | Find clinics, camps, classes, and other group programs near a location |
| `get_golf_coach_availability` | Openings and offering details for one selected coach                   |
| `book_golf_lesson`            | Book a lesson (requires PGA.com sign-in with `mcp:coaching` scope)     |

Coach and program search and coach availability work without signing in. Booking always requires PGA.com sign-in through MCP OAuth with the `mcp:coaching` scope.

## Usage

1. Install **PGA Play Golf** from the Cursor Marketplace.
2. Open **Customize** and make sure the **pga-play-golf** MCP server is enabled.
3. Ask the agent something like "Find a PGA coach for private lessons near Frisco, TX" or "Any junior golf camps near 30301?", or run the `find-coach-or-program` command.
4. When you book, Cursor prompts you to sign in to PGA.com.

No API keys or plugin variables are required.

## Local testing

1. Clone this repository into `~/.cursor/plugins/local/pga-play-golf` (or symlink it there).
2. Reload the Cursor window.
3. Open **Customize** and enable the **pga-play-golf** MCP server.
4. Run a coach search, then start a booking to confirm the OAuth prompt.

To test against the dev server, override the MCP server URL in Cursor MCP settings with `https://mcp.dev.pga.com/mcp`. The bundled `mcp.json` always points at production.

## License

[MIT](LICENSE) © 2026 PGA of America
