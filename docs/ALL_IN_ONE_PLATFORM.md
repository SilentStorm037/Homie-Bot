# Homie All-in-One Platform

Homie combines moderation, security, support, community engagement, automation, content publishing, member utilities, analytics, and server administration in one bot. Each server has its own configuration and enabled features.

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
- Server update channels can receive clear, versioned Homie changelogs.

## Dashboard, privacy, and integrations

- Discord sign-in only shows servers where a user has Manage Server or Administrator.
- The dashboard automatically adapts to desktop and mobile layouts and includes guided setup, contextual help, navigation search, dark/light themes, and unsaved-change protection.
- Administrators can manage configuration, support workflows, community systems, automations, publishing, audit history, and API credentials without memorising commands.
- Dashboard changes are validated and recorded in activity history.
- `/apikey` creates revocable, single-server, read-only integration credentials with selected scopes.
- `/privacy export` downloads a user's server data. `/privacy delete confirm:DELETE` deletes optional data and pseudonymizes records retained for moderation integrity.
- Reminders, giveaways, scheduled messages, poll closures, moderation expiries, delayed roles, and cleanup tasks continue across bot restarts.
