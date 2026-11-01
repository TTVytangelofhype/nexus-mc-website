# NEXUS MC — Website Integrations

This repository contains the **raid-status panel and automatic release changelog** for NEXUS MC. It is a standalone integration preview, **not a copy of the existing ChatGPT Sites website**.

## Features
- Public GitHub release feed for the Updates & Progress section.
- A read-only raid status panel (shows 'Not connected' until a live HTTPS endpoint exists).
- Client-side refresh every five minutes.

## Setup
1. Publish a GitHub Release in this repository (for example, tag `mc-2026.11.01`).
2. Open the preview locally with `python -m http.server 8080`.
3. In `config.json`, set `raidStatusUrl` to a secured, read-only HTTPS JSON endpoint when available.
4. Integrate these widgets into the **original** NEXUS MC ChatGPT Sites project. This repository does not automatically deploy to that site.

### Raid JSON example
`{"state":"waiting","bossName":null,"players":0,"nextRaidAt":null,"updatedAt":"2026-11-01T00:00:00Z"}`

Never expose RCON passwords, server console commands or private player data in public status feeds. Ensure any endpoint permits CORS for the published NEXUS MC domain.

The existing site is hosted at `https://nexusmc.nexusukrp.co.uk` through ChatGPT Sites. **Do not change its Cloudflare DNS record or replace it with this preview.**
