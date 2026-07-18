# Homie Dashboard

The Homie dashboard is a responsive web interface served by the bot process. It provides visual setup and everyday management for administrators who prefer forms, previews, and guided workflows over slash commands.

## User experience

- Automatic desktop, tablet, and mobile layouts
- Persistent mobile navigation and full slide-out menu
- First-time guided setup
- Contextual help and recommended next actions
- Searchable navigation
- Dark and light themes
- Reduced-motion accessibility support
- Unsaved-change indicators and navigation warnings
- Responsive cards, tables, forms, emoji picker, message previews, and status feedback

## Dashboard sections

| Section | What it manages |
| --- | --- |
| Home | Server health, setup completion, activity, enabled modules, and shortcuts |
| Get started | Permissions, guided server provisioning, and setup checklist |
| Channels & roles | Feature destinations, managed roles, role creation, and core modules |
| Protection | Automod, blocked content, spam limits, anti-raid behavior, and verification |
| Welcome & rewards | Greetings, autoroles, starboard, levelling, achievements, birthdays, colours, and economy |
| Smart replies | Reply modes, personality, cooldowns, channels, taught replies, and memory controls |
| Connections | Twitch, TikTok, feeds, counters, and external content sources |
| Advanced settings | Searchable access to the complete server configuration |
| Member support | Tickets, modmail, suggestions, forms, and appeals |
| Automation | Reaction roles, role panels, polls, sticky content, cleanup, voice hubs, and workflows |
| Content library | Tags, custom replies, feedback, and reusable content |
| Publish | Plain messages, Discord JSON, embeds, editing, and scheduling |
| Activity log | Dashboard, moderation, and system activity |
| Data & API | Runtime health, exports, diagnostics, privacy settings, and integration credentials |

## Local start

Set at least a dashboard owner token:

```powershell
$env:DASHBOARD_TOKEN="use-a-long-random-value"
$env:DASHBOARD_HOST="127.0.0.1"
$env:DASHBOARD_PORT="3000"
npm start
```

Open:

```text
http://127.0.0.1:3000
```

The dashboard starts and stops with the Discord bot because both are hosted by the same Node.js process.

## Authentication

### Discord OAuth

OAuth is the recommended login for server administrators. Set:

```env
CLIENT_ID=your_discord_application_id
DISCORD_CLIENT_SECRET=your_discord_oauth_secret
DASHBOARD_PUBLIC_URL=https://dashboard.example.com
```

Register the exact callback in Discord Developer Portal:

```text
https://dashboard.example.com/auth/callback
```

OAuth requests the Discord `identify` and `guilds` scopes. A user only sees shared servers where they:

- own the server;
- have **Manage Server**; or
- have **Administrator**.

Dashboard sessions use an HTTP-only cookie, use `SameSite=Lax`, become Secure on HTTPS deployments, and expire after 12 hours.

### Owner token

`DASHBOARD_TOKEN` is an emergency or local owner credential. The UI stores it in that browser and sends it as a bearer token. Generate a long random value and never share or commit it.

### Integration API keys

`/apikey` creates revocable, read-only keys scoped to one Discord server and selected API permissions. Keys are displayed once.

## Production deployment

Keep the dashboard bound locally:

```env
DASHBOARD_HOST=127.0.0.1
DASHBOARD_PORT=3000
```

Place a trusted HTTPS reverse proxy or Cloudflare Tunnel in front of it. For Cloudflare Tunnel:

1. Create a tunnel in Cloudflare.
2. Install the supplied Cloudflared service command on the production computer.
3. Create a Published application route such as `dashboard.example.com`.
4. Point its service URL to `http://127.0.0.1:3000`.
5. Set `DASHBOARD_PUBLIC_URL=https://dashboard.example.com`.
6. Add `https://dashboard.example.com/auth/callback` to Discord OAuth redirects.
7. Restart Homie with updated environment variables.

Do not expose port 3000 directly, bind it to every network interface, or use plain public HTTP. The full walkthrough is in [Self-hosting and Production Operations](../docs/SELF_HOSTING.md).

## Security model

Dashboard protections include:

- OAuth server filtering based on Discord permissions;
- optional owner bearer-token authentication;
- request rate limiting;
- JSON content-type enforcement for writes;
- same-origin validation for state-changing browser requests;
- prototype-key rejection during settings merges;
- server-side type, range, and relationship validation;
- Discord permission and role-hierarchy validation;
- suppression of unexpected mentions in published content;
- activity auditing for configuration, moderation, resource, and publishing changes;
- read-only, scoped integration credentials.

The browser interface is not treated as a security boundary. Every important write is validated again by the server.

## Endpoints

| Endpoint | Access | Description |
| --- | --- | --- |
| `GET /` | Public shell | Loads the dashboard login and application client. |
| `GET /auth/discord` | Public | Starts Discord OAuth. |
| `GET /auth/callback` | Public | Validates OAuth state and creates a session. |
| `GET /auth/logout` | Public | Clears the active dashboard session. |
| `GET /healthz` | Public | Reports basic service and Discord readiness. |
| `GET /metrics` | Authenticated | Returns dashboard operational metrics. |
| `/api/bootstrap` | Authenticated | Returns the bot identity and manageable servers. |
| `/api/guilds/:id` | Authenticated | Returns the selected server's dashboard model. |
| `/api/guilds/:id/settings` | Authenticated | Validates and updates server settings. |
| `/api/guilds/:id/community` | Authenticated | Validates and updates community data. |
| `/api/v1/guilds/:id/stats` | Scoped key | Read-only integration statistics. |
| `/api/v1/guilds/:id/audit` | Scoped key | Read-only integration audit information. |

Additional authenticated resource endpoints power tickets, suggestions, forms, appeals, feeds, automations, counters, voice hubs, polls, scheduled messages, sticky messages, role panels, moderation actions, publishing, and API-key management.

## Operational checks

```powershell
npm run check
npm test
npm audit --omit=dev --audit-level=high
```

Dashboard tests cover authentication, safe settings merging, origin and content-type write policy, settings validation, reaction-role publishing, emoji data, mobile layout support, and required accessibility/UX elements.

## Troubleshooting

### Login says Discord OAuth is not configured

Set `CLIENT_ID`, `DISCORD_CLIENT_SECRET`, and `DASHBOARD_PUBLIC_URL`, then restart Homie.

### Discord says redirect URI is invalid

The redirect saved in the Developer Portal must exactly match:

```text
<DASHBOARD_PUBLIC_URL>/auth/callback
```

Check protocol, hostname, subdomain, path, and trailing slash.

### Public URL returns a Cloudflare error

Confirm the tunnel is connected and its service URL is `http://127.0.0.1:3000`. Test `/healthz` locally first.

### A server is missing after login

The signed-in Discord account must share the server with Homie and own it or have Manage Server/Administrator.

### A setting will not save

Read the displayed validation error, confirm Homie's Discord permissions and role position, and ensure referenced channels or roles still exist.

### Mobile layout does not appear

Reload the page after clearing an unusually aggressive browser cache. Layout selection responds to mobile browser information, viewport width, orientation, and the visible mobile viewport.
