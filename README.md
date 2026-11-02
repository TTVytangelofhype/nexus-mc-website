# NEXUS MC — Unified Website Integration

**Live website:** https://nexusmc.nexusukrp.co.uk (existing ChatGPT Sites project).  
**Source of integrations:** this GitHub repository. GitHub updates do **not** automatically publish to the live ChatGPT Sites website.

## Confirmed working
- NEXUS Raid Boss v0.3.5 uploads raid status directly from PebbleHost to the cPanel endpoint using private authenticated HTTPS.
- Public read-only feed: https://nexusukrp.co.uk/nexus-raid-api/status.json
- `config.json` points the website widget to this feed.

## Website components
- `chatgpt-sites-section.html`: ready-to-integrate HTML/CSS for the **Updates & Progress** section and raid panel. Adapt in the actual ChatGPT Sites editor; do not deploy this as a replacement homepage.
- `widget.js`: release history, live raid countdown, Minecraft colour-code stripping, stale-status checks.
- `updates.json`: verified development history fallback if no GitHub Release exists yet.
- `config.json`: public endpoint, release-repository and refresh settings.
- `index.html`: independent preview.
- `SITE-INTEGRATION.md`: safe integration and publishing checklist.
- `CONSOLIDATED-PROJECT.md`: project history and original chat references.

## Work still needed
The original editable ChatGPT Sites project must be opened and updated with these components, preserving server rules, voting, factions, rankings, cosmetics, and other existing pages. Then publish that site through its own controls. No change to Cloudflare DNS, cPanel cron, or PebbleHost schedules is needed.

## Security
Never commit the Minecraft token, PHP receiver secret, RCON passwords, private player data, or server credentials.

## Preview
Serve this directory locally (for example `python -m http.server 8080`) and visit http://localhost:8080. The browser needs internet access and the cPanel endpoint must allow cross-origin GET requests for the page's origin.
