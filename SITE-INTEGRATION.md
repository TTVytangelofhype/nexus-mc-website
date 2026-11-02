# Publish the NEXUS MC widgets into the original website

The original site is published to https://nexusmc.nexusukrp.co.uk through ChatGPT Sites (custom-domains.chatgpt.site).

**This repository is not that site's source project.** Pushing here does not update the live ChatGPT Sites deployment.

When you open the original site in its supported editor:

1. Back up/export the current site.
2. Replace only the hard-coded **Updates & Progress v0.0.1** section with the widget implementation from `widget.js` and the matching markup from `index.html`, adapting paths to the host.
3. In the original site, serve/copy `config.json`, `updates.json`, and `widget.js` together or use stable absolute HTTPS URLs to these assets.
4. Ensure the live feed https://nexusukrp.co.uk/nexus-raid-api/status.json sets Access-Control-Allow-Origin: https://nexusmc.nexusukrp.co.uk (also account for the ChatGPT Sites editor preview origin if needed).
5. Verify rendering with a live raid (state announcing/running), refresh and countdown transitions, unavailable feed behaviour, mobile layout, and release fallbacks.
6. Publish to the existing domain without changing Cloudflare DNS.

Changes in this repo are **not** automatically deployed. Do not point Cloudflare to GitHub Pages or replace the whole existing homepage without explicitly migrating.
