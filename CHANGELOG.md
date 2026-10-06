# Changelog

All notable changes to this plugin are documented here. This project follows [Semantic Versioning](https://semver.org/).

## 1.0.0

Initial public release of the PGA Play Golf Cursor plugin.

- **MCP server:** connects Cursor to the PGA of America MCP server at `https://mcp.pga.com/mcp`.
- **Skill `play-golf`:** tool routing and the booking workflow for coaches, programs, availability, and lessons.
- **Rule `pga-play-golf-mcp`:** routes golf coaching requests to the right tools and keeps internal IDs out of chat.
- **Command `find-coach-or-program`:** searches PGA coaches or group programs near a city or ZIP.
