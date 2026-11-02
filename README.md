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

## Minecraft raid status exporter (v0.3.4)

The separate NEXUS Raid Boss v0.3.4 plugin source now produces `plugins/NexusRaidBoss/raid-status.json` locally every five seconds. **This does not make the file publicly available.** Copy only this JSON using a secured automated upload to a read-only HTTPS endpoint, configure its CORS policy for the NEXUS MC website, then set `raidStatusUrl` in `config.json`. Do not expose Minecraft server credentials or administration APIs. Until the endpoint is configured, the raid panel intentionally says it is not connected.

## cPanel bridge setup (2026-11-02)

The Minecraft plugin already writes its local `raid-status.json`. A separate **secure bridge** is required to upload the status to cPanel. The downloadable setup kit includes a private-token PHP receiver, a public read-only `status.json`, and Linux/Windows upload scripts. Put the public files in `public_html/nexus-raid-api/`, keep the token **outside public_html and never in GitHub**, and schedule the uploader on the game host. Once `https://nexusukrp.co.uk/nexus-raid-api/status.json` displays verified current data, set `config.json` `raidStatusUrl` to that URL. This repository does not automatically publish the existing ChatGPT Sites project.

## Direct Minecraft → cPanel sync (v0.3.5)

NEXUS Raid Boss v0.3.5 adds optional asynchronous authenticated HTTPS publishing from PebbleHost to `https://nexusukrp.co.uk/nexus-raid-api/push.php` every 30 seconds. Configure `website-sync.enabled`, `website-sync.url` and `website-sync.token` in the **private Minecraft plugin** config. Keep that token outside this GitHub repository. After confirming the public `status.json` has a real `updatedAt` timestamp, set `raidStatusUrl` in this repository's `config.json` to `https://nexusukrp.co.uk/nexus-raid-api/status.json`. The ChatGPT Sites original page still needs the widget integrated and republished separately.
