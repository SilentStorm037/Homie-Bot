# Homie All-in-One Platform

Homie combines moderation, security, support, community engagement, automation, content publishing, member utilities, analytics, and server administration in one bot. Configuration is server-specific and stored transactionally in SQLite.

## Moderation and security

- Unified numbered moderation cases with evidence, reason editing, voiding, expiry, user history, and recent-case views.
- Warnings, timeouts, temporary bans, bans, soft bans, kicks, bulk cleanup, channel locks, slowmode, and private moderator notes.
- Automod for wildcard words, mentions, capitals, invites, links/domains, emoji/newline/attachment floods, duplicate messages, and message-rate spam.
- Anti-raid join windows, minimum account age, quarantine, verification, emergency lockdown, and automatic expiry jobs.
- Detailed server event and moderator audit logs, including actor attribution where Discord's audit log allows it.

Start with `/automod status`, `/security status`, `/cases recent`, and `/config view`.

## Support and feedback

- Private tickets with panels, claiming, participant management, transcripts, logs, limits, and closing reasons.
- DM-based modmail conversations with persistent staff threads and two-way replies.
- Suggestions with staff decisions, configurable forms with modal submissions, and moderation appeals.
- Invite attribution and inviter leaderboards.

Start with `/ticket setup`, `/modmail setup`, `/suggestion channel`, `/form create`, and `/invites leaderboard`.

## Community and engagement

- Multi-emoji starboard that preserves source images and updates when reactions, messages, or attachments change.
- Interactive polls, weighted giveaways, role panels, reaction roles, recurring reminders, AFK notices, highlight notifications, custom tags with variables, levels, role rewards, birthdays, achievements, and colour roles.
- Optional Homie Coins economy with daily rewards, transfers, staff adjustments, and leaderboards.
- Join-to-create temporary voice rooms and live member/server-stat counter channels.
- Shared voice music queues with search/URL playback, pause, resume, skip, stop, queue, and volume controls.

Useful commands include `/poll`, `/giveaway`, `/rolepanel`, `/level`, `/economy`, `/voicehub`, `/music`, `/counter`, `/highlight`, and `/tag`.

## Publishing and automation

- Managed messages and embeds can be sent, edited, or scheduled with `/message`.
- RSS/Atom-compatible subscriptions cover sites that expose feeds, including common YouTube and GitHub feed URLs.
- Trigger-and-action automations can reply, send messages, react, or add/remove roles.
- Per-channel automatic message cleanup supports all messages or bot-only output.
- Git releases can generate versioned Discord changelogs for configured update channels.

## Dashboard, integrations, and operations

- The dashboard supports an owner token or Discord OAuth. OAuth users only see servers where they have Manage Server or Administrator.
- The dashboard automatically adapts to desktop and mobile layouts and includes guided setup, contextual help, navigation search, dark/light themes, and unsaved-change protection.
- Administrators can manage configuration, support workflows, community systems, automations, publishing, audit history, diagnostics, and API credentials without memorising commands.
- Dashboard writes are validated, rate-limited, origin checked, protected from prototype-key injection, and written to the audit log.
- `/apikey` creates revocable, single-server, read-only API keys. Use `Authorization: Homie <key>` with `GET /api/v1/guilds/<id>/stats` or `GET /api/v1/guilds/<id>/audit` according to the key's scope.
- `/privacy export` downloads a user's server data. `/privacy delete confirm:DELETE` deletes optional data and pseudonymizes records retained for moderation integrity.
- Durable jobs survive restarts and retry failed reminders, giveaways, scheduled messages, poll closures, moderation expiries, delayed roles, and cleanup tasks.
- `/healthz`, authenticated `/metrics`, structured logs, graceful shutdown, PM2 backoff/memory limits, SQLite snapshots, automated tests, dependency auditing, and GitHub Actions support production operation.

## Dashboard OAuth environment

Set these values in production:

```env
CLIENT_ID=your_discord_application_id
DISCORD_CLIENT_SECRET=your_discord_oauth_secret
DASHBOARD_PUBLIC_URL=https://your-dashboard.example
DASHBOARD_TOKEN=a-long-random-owner-token
```

Add `https://your-dashboard.example/auth/callback` as a Discord OAuth redirect URL. Keep the client secret and dashboard token out of Git.

## Persistence and backups

Node.js 22.13 or newer is required for the built-in SQLite driver. Runtime data defaults to `data/homie.sqlite`. `npm run backup:data` creates a consistent SQLite snapshot; the normal release backup also keeps 30 days of runtime snapshots when `HOMIE_BACKUP_ROOT` is configured.

Use `npm run check` and `npm test` before manual deployments. The approved end-to-end release remains `npm run release:auto`.
