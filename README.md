<p align="center"><img src="assets/icon-512.png" alt="Tavern Scribe" width="96" height="96"></p>

# Tavern Scribe MCP server

Bring your tabletop RPG campaign into your AI assistant. [Tavern Scribe](https://tavernscribe.com)
records and transcribes your sessions, writes recaps, and keeps a searchable memory of everything
that happened at the table: NPCs, quests, locations, factions, items, notes and character sheets.
This connector lets Claude, ChatGPT, Cursor and other MCP clients read that campaign and add to it.

**Server URL:** `https://api.tavernscribe.com/mcp` (remote, streamable HTTP, OAuth 2.1)

This repository holds the connector configuration and plugin manifests. The server itself is
hosted by Tavern Scribe; there is nothing to install or run locally.

## What you can do

- "What did we learn about the Duke in our last three sessions?"
- "List the open quests and who gave each one."
- "Find my notes about the sunken temple."
- "What's my character's armor class and current hit points?"
- "Add an NPC named Mirelle, a nervous harbor clerk who owes the thieves' guild."

One server covers every campaign you belong to. Ask your assistant to list your campaigns and pick
one; it works in one campaign at a time. Works with D&D 5e, Daggerheart, Pathfinder 2e, Call of
Cthulhu and other systems Tavern Scribe supports.

## Connect

You need a Tavern Scribe account (there is a free plan) and at least one campaign.

### Claude (claude.ai, desktop)

1. Open **Settings → Connectors** and choose **Add custom connector**.
2. Paste `https://api.tavernscribe.com/mcp` and save.
3. Click **Connect**, sign in to Tavern Scribe and approve access.

### Claude Code

```bash
claude mcp add --transport http tavernscribe https://api.tavernscribe.com/mcp
```

Run `/mcp` in Claude Code to finish the sign-in. Or install it as a plugin:

```
/plugin install tavern-scribe --marketplace loji-gaming/tavern-scribe-mcp
```

### ChatGPT and other apps with custom connectors

Add a custom connector (or MCP server) with the same URL and complete the sign-in.

### Cursor, VS Code and tools without the browser sign-in

In Tavern Scribe, open your account's **AI Connections** page and click **Create key**. It shows
the exact config block (with the key as a `Bearer` header) for Cursor, VS Code and similar tools.
The key is shown once; treat it like a password and revoke it from the same page if it leaks.

## Permissions and safety

- The connector acts as your Tavern Scribe account and follows the same rules as the web app. In a
  campaign you run you get the Dungeon Master's view; in one where you play you see only what a
  player sees. Hidden characters and DM-only notes stay out of a player's view, and campaigns you
  don't belong to are not reachable.
- Every tool states whether it is read-only and whether it changes or deletes data, so your
  assistant can ask before it writes. Deletes can't be undone.
- A few generation tools (maps, images, audio) use your campaign's credit balance and say so in
  their descriptions.
- Revoke access at any time under **Your connections** on the AI Connections page.

## Links

- Setup guide: <https://tavernscribe.com/blog/connect-claude-to-your-dnd-campaign>
- Privacy policy: <https://tavernscribe.com/privacy-policy>
- Terms of service: <https://tavernscribe.com/terms-of-service>
- Support: <https://tavernscribe.com/contact>

## License

The configuration in this repository is MIT licensed. Tavern Scribe itself is a hosted service
covered by its [terms of service](https://tavernscribe.com/terms-of-service).
