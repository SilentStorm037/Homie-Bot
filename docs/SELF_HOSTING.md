# Self-hosting and Production Operations

This guide is for developers operating an authorised Homie instance. Most server owners should invite the public bot and use the [Public Server Setup Guide](PUBLIC_SERVER_SETUP_GUIDE.md) instead.

## Requirements

- Windows or another Node.js-supported operating system
- Node.js 22.13 or newer
- npm
- A Discord application with a bot user
- A writable data directory
- Optional Twitch developer credentials for Twitch alerts
- Optional domain and Cloudflare account for a public dashboard
- PM2 for recommended long-running production operation

Homie uses the SQLite driver built into supported Node.js releases. Music playback uses the installed media dependencies from `package.json`, including FFmpeg support.

## 1. Create a Discord application

In the [Discord Developer Portal](https://discord.com/developers/applications):

1. Create or select an application.
2. Create its bot user.
3. Enable the gateway intents required by the features you intend to run, including member and message-content access where applicable.
4. Generate a bot token and store it only in `.env`.
5. Copy the application ID for `CLIENT_ID`.
6. Add the bot to an authorised test server.

Never paste a live bot token into chat, source code, screenshots, issues, or commits. Reset it immediately if exposed.

## 2. Install the repository

```powershell
cd "D:\HOMIE BOT\Discord-bot2.1"
Copy-Item .env.example .env
npm ci
```

Node.js must satisfy the version in `package.json`:

```powershell
node --version
npm --version
```

## 3. Configure public environment variables

Use this as the public configuration shape. Values that are not needed may remain blank.

```env
TOKEN=your_discord_bot_token
CLIENT_ID=your_discord_application_id
GUILD_ID=your_development_server_id
OWNER_ID=your_discord_user_id

TWITCH_CLIENT_ID=
TWITCH_CLIENT_SECRET=

DASHBOARD_TOKEN=a_long_random_emergency_owner_token
DASHBOARD_HOST=127.0.0.1
DASHBOARD_PORT=3000
DISCORD_CLIENT_SECRET=
DASHBOARD_PUBLIC_URL=

HOMIE_DB_PATH=./data/homie.sqlite
HOMIE_SHARD_COUNT=1
```

Environment reference:

| Variable | Required | Purpose |
| --- | --- | --- |
| `TOKEN` | Yes | Authenticates the Discord bot user. |
| `CLIENT_ID` | Yes | Discord application ID used for command registration and OAuth. |
| `GUILD_ID` | Development | Development or primary test server ID. |
| `OWNER_ID` | Recommended | Identifies the authorised application owner where required. |
| `TWITCH_CLIENT_ID` | Twitch only | Twitch application client ID. |
| `TWITCH_CLIENT_SECRET` | Twitch only | Twitch application secret; never commit it. |
| `DASHBOARD_TOKEN` | Recommended | Emergency owner login for the dashboard. Use a long random value. |
| `DASHBOARD_HOST` | Dashboard | Local bind address. Keep `127.0.0.1` behind a reverse proxy or tunnel. |
| `DASHBOARD_PORT` | Dashboard | Local dashboard port; defaults to `3000`. |
| `DISCORD_CLIENT_SECRET` | OAuth dashboard | Discord OAuth client secret. |
| `DASHBOARD_PUBLIC_URL` | OAuth dashboard | Exact public HTTPS origin without a trailing slash. |
| `HOMIE_DB_PATH` | Recommended | SQLite database location. Defaults to `./data/homie.sqlite`. |
| `HOMIE_SHARD_COUNT` | Large deployments | Number of Discord gateway shards. Defaults to `1`. |

Generate a strong dashboard token in PowerShell:

```powershell
$bytes = New-Object byte[] 48
[Security.Cryptography.RandomNumberGenerator]::Fill($bytes)
[Convert]::ToBase64String($bytes)
```

Confirm `.env` is ignored:

```powershell
git check-ignore .env
```

Expected output:

```text
.env
```

## 4. Register Discord commands

```powershell
npm run deploy
```

The schema test ensures required options appear before optional options and that the public application-command limit is respected.

## 5. Verify before starting

```powershell
npm run check
npm test
npm audit --omit=dev --audit-level=high
```

Do not deploy a failing build.

## 6. Start locally

```powershell
npm start
```

When dashboard variables are configured, the same bot process serves:

```text
http://127.0.0.1:3000
```

## 7. Run with PM2 on Windows

Install PM2:

```powershell
npm install --global pm2
```

Start the production definition:

```powershell
pm2 start ecosystem.config.js --only homie-prod
pm2 status
pm2 logs homie-prod --lines 50
```

Useful commands:

```powershell
pm2 restart homie-prod --update-env
pm2 stop homie-prod
pm2 delete homie-prod
pm2 save
```

The supplied PM2 configuration enables automatic restart, exponential restart backoff, memory protection, graceful shutdown, and source watching. Runtime data, logs, dependencies, Git metadata, generated assets, and cache directories are excluded from watch restarts.

If PM2 reports `connect EPERM \\.\pipe\rpc.sock`, open an elevated PowerShell window and ensure the same PM2 home is used consistently:

```powershell
$env:PM2_HOME = "$env:USERPROFILE\.pm2"
pm2 status
```

## 8. Publish the dashboard securely

Do not bind Homie directly to a public interface and do not forward port 3000 through the router. Keep:

```env
DASHBOARD_HOST=127.0.0.1
DASHBOARD_PORT=3000
```

The recommended Windows deployment is a [Cloudflare Tunnel](https://developers.cloudflare.com/tunnel/setup/):

1. Add a domain to Cloudflare.
2. Open **Networking → Tunnels** and create a Cloudflared tunnel.
3. On the production computer, run the Windows service installation command supplied by Cloudflare.
4. Add a **Published application** route.
5. Choose a hostname such as `dashboard.example.com`.
6. Set its service URL to `http://127.0.0.1:3000`.
7. Set Homie's public URL:

```env
DASHBOARD_PUBLIC_URL=https://dashboard.example.com
```

8. In Discord Developer Portal → OAuth2, add this exact redirect:

```text
https://dashboard.example.com/auth/callback
```

9. Set the OAuth secret:

```env
DISCORD_CLIENT_SECRET=your_discord_oauth_client_secret
```

10. Restart Homie:

```powershell
pm2 restart homie-prod --update-env
```

Cloudflare supplies public HTTPS and forwards requests through the outbound tunnel to the local HTTP service. A temporary Quick Tunnel can be used for testing, but its random URL changes and is unsuitable for a stable OAuth redirect.

## 9. Dashboard authentication

Homie supports:

- Discord OAuth for normal administrators;
- an emergency owner token stored in the browser and sent as a bearer token;
- scoped `Homie` API credentials created with `/apikey`.

OAuth users only see shared servers where they are the owner or have **Manage Server** or **Administrator**. Sessions use HTTP-only cookies and expire after 12 hours.

## 10. Health, metrics, and integration endpoints

| Endpoint | Authentication | Purpose |
| --- | --- | --- |
| `GET /healthz` | Public | Basic process and Discord readiness check. |
| `GET /metrics` | Authenticated | Operational dashboard metrics. |
| `GET /api/v1/guilds/:id/stats` | Scoped API key | Read-only server statistics. |
| `GET /api/v1/guilds/:id/audit` | Scoped API key | Read-only audit information. |

Create and revoke integration keys with `/apikey`. Keys are shown once and should be treated like passwords.

## 11. Persistence and backups

Runtime data is stored transactionally in SQLite at `HOMIE_DB_PATH`. Do not edit a live database manually.

Create a consistent snapshot:

```powershell
npm run backup:data
```

Back up at least:

- the SQLite database and its valid snapshots;
- `.env` through an encrypted secret-management method;
- the Git repository or remote;
- deployment configuration that is not generated automatically.

Do not publish database files or runtime JSON exports. They may contain member or moderation data.

## 12. Updating an installation

For an ordinary manual update:

```powershell
npm ci
npm run check
npm test
npm run deploy
pm2 restart homie-prod --update-env
```

Only rerun command registration when application-command definitions changed. Always read release notes and back up runtime data before a significant upgrade.

## 13. Troubleshooting

### `git` is not recognised

Install Git for Windows:

```powershell
winget install --id Git.Git -e --source winget
```

Close and reopen PowerShell afterward.

### Discord commands are missing

Run `npm run deploy`, confirm `CLIENT_ID` and the bot token belong to the same application, and restart Discord after propagation.

### Homie cannot manage roles

Move Homie's role above the target roles. Discord prevents bots from managing equal or higher roles regardless of code configuration.

### Dashboard works locally but not publicly

Check:

```text
http://127.0.0.1:3000/healthz
https://dashboard.example.com/healthz
```

Then verify the Cloudflare route points to `http://127.0.0.1:3000`, the tunnel service is running, and the public URL matches the OAuth redirect exactly.

### Discord OAuth returns an error

Confirm all three values are present and from the same Discord application:

```env
CLIENT_ID=
DISCORD_CLIENT_SECRET=
DASHBOARD_PUBLIC_URL=https://dashboard.example.com
```

The Developer Portal redirect must be exactly `DASHBOARD_PUBLIC_URL` plus `/auth/callback`.

### Music cannot play

Check that Homie can Connect and Speak, the member is in a voice channel, media dependencies installed successfully, and the source is reachable from the production machine.

### PM2 repeatedly stops the bot

Inspect both logs and the process state:

```powershell
pm2 status
pm2 logs homie-prod --lines 100
```

Run `npm ci` if a dependency is missing, then restart with `--update-env`.
