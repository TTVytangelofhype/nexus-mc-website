# NEXUS MC — Consolidated Project

This is the **single source of truth for NEXUS MC website integration work** across the two previous ChatGPT discussions and the current development thread.

## Conversation references
- https://chatgpt.com/c/6a79d167-9c18-83ed-a982-b5943ac92a0e
- https://chatgpt.com/c/6a98a5e0-d65c-83ed-9f5c-0349ba7e5a2d

**Important:** The conversation links are references only. Private ChatGPT conversation content was not accessible through the current tool connection, so this file does **not** claim to reproduce their unseen details. These conversations are not technically merged inside ChatGPT.

## Existing production infrastructure
- Public site: https://nexusmc.nexusukrp.co.uk
- Website host: ChatGPT Sites, custom-domain CNAME to custom-domains.chatgpt.site
- GitHub website integration: https://github.com/TTVytangelofhype/nexus-mc-website
- Java: play.nexusukmc.co.uk
- Bedrock: play.nexusukmc.co.uk port 8146
- Raid API: https://nexusukrp.co.uk/nexus-raid-api/status.json (cPanel)
- Raid plugin: NEXUS Raid Boss v0.3.5 with direct HTTPS status publishing
- Project's previous public site includes rules, rankings, factions, cosmetics, events, voting, and a static v0.0.1 development card

## Completed in this repository
- Automatic GitHub Release feed with fallback to `updates.json`
- Live raid display from `config.json` endpoint
- Frontend countdown with stale-feed detection
- Minecraft colour-code removal from boss name
- Basic validation workflow
- Instructions in `SITE-INTEGRATION.md`

## Still required
1. Obtain original editable ChatGPT Sites source/project (not merely its extracted page text).
2. Preserve all current site sections and styles, then integrate widgets.
3. Validate cross-origin access from the published site to the cPanel API.
4. Publish through the original ChatGPT Sites editing system; GitHub commits alone do not deploy the site.
5. Validate live raid and mobile behaviour in production.
6. Optional: publish GitHub release entries to supersede fallback history.

## Safety
Never commit the private PHP receiver token, Minecraft admin credentials, RCON details, or private player data. Do not change live Cloudflare DNS merely to display the new components.
