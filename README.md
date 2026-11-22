# VIN Detective AI

An open-source, evidence-first vehicle VIN investigation workflow for AI assistants.

## Features (v0.2.0)

- Extract and validate a VIN entered as text or shown in a photograph using supported host AI capabilities.
- Research manufacturer specifications, recalls, title and auction history using sources accessible to the host assistant.
- Search for exact-VIN salvage auction listings and *verified* original accident photos.
- Summarize mechanical risks and estimate a negotiation range using documented market comparables where available.
- When web search finds nothing, look up the VIN directly on auction archives (BidCars, Copart lot pages, mirrors) using a browser tool, without bypassing bot checks or logins.
- Show the original auction photos in the chat as one numbered gallery image that also displays in the Claude mobile app, along with the gallery link.
- Clearly label verified facts, claims from third-party archives, estimates, and unknowns.

**This release is a research skill, not a live VIN-history API.** It does not include paid CARFAX, Copart or IAAI access, its own auction-photo collection, or a hosted MCP server. Results depend on the host assistant's tools and accessible sources.

## ChatGPT plugin

The portable manifest is `plugin.json`; the skill lives at `skills/vin-investigation/SKILL.md`. Use the compatible plugin install/import procedure for your ChatGPT/Codex environment. The separately saved ChatGPT plugin is not automatically synchronized with GitHub changes.

## Claude and other assistants

The `SKILL.md` workflow can be adapted to platforms supporting Agent Skills. Follow each platform's packaging and installation requirements; compatibility is not automatic for the entire plugin.

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md). Do not commit private vehicle data, secrets, or third-party auction photos without redistribution rights.

## Disclaimer

Not an official title, legal, mechanical, insurance, or vehicle-history certification. Always verify titles and repair history with authoritative records and a qualified professional.

## License

MIT, see [LICENSE](LICENSE).
