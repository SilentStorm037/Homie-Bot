# Homie

**One Discord bot for moderation, safety, support, automation, community engagement, creator alerts, music, and everyday server management.**

Homie is a verified, multi-server Discord bot designed to replace a collection of separate moderation and community bots. Server owners can configure it with slash commands or through a responsive web dashboard, while members get consistent commands and self-service tools.

[Add Homie to Discord](https://discord.com/oauth2/authorize?client_id=1492673658567524353&permissions=8&integration_type=0&scope=bot+applications.commands) · [Join the support server](https://discord.gg/RjuSrGXHSa) · [Setup guide](docs/PUBLIC_SERVER_SETUP_GUIDE.md) · [Command reference](docs/COMMAND_REFERENCE.md)

## Why Homie

- **One configuration:** channels, roles, safety, support, engagement, and publishing are managed together.
- **Beginner friendly:** `/setup`, `/config view`, contextual command help, and the dashboard explain what to do next.
- **Server specific:** every community keeps its own settings, channels, roles, messages, and enabled features.
- **Auditable:** moderation, dashboard changes, publishing, and administrative actions are recorded where supported.
- **Privacy aware:** members can inspect or remove optional personal data with `/privacy`.
- **Reliable:** reminders, giveaways, scheduled messages, moderation expiries, and other timed actions continue through restarts.

## Feature overview

| Area | Included capabilities |
| --- | --- |
| Moderation | Warnings, cases, notes, timeouts, kicks, bans, temporary bans, soft bans, message clearing, slowmode, channel locking, nickname and role tools |
| Safety | Advanced automod, spam and duplicate detection, invite/link/domain filtering, mention and caps limits, anti-raid monitoring, quarantine, verification, and emergency lockdown |
| Member support | Tickets, ticket panels, transcripts, claiming and participants, DM modmail, forms, applications, suggestions, moderation appeals, and feedback |
| Community | Welcome and leave flows, autoroles, colour roles, starboard, reaction roles, role panels, polls, giveaways, tags, birthdays, AFK, highlights, and invite attribution |
| Progression | XP levels, leaderboards, role rewards, channel/role exclusions, multipliers, achievements, achievement cards, and optional community currency |
| Creator tools | Twitch and TikTok account linking, live notifications, per-member messages, server defaults, images, pings, and test tools |
| Automation | Trigger/action workflows, reminders, scheduled messages, sticky-style managed content, cleanup rules, feeds, live counters, and temporary voice hubs |
| Publishing | Plain messages, rich embeds, editing, scheduling, announcements, update posts, and audited delivery |
| Entertainment | Shared voice music queues, repeat, shuffle, queue removal, volume controls, jokes, facts, compliments, roasts, coin flips, and 8-ball |
| Smart replies | Server personality, reply modes, channel allowlists, cooldowns, custom taught replies, explicit memory, and member memory controls |
| Platform | Responsive dashboard, scoped read-only API keys, audit history, privacy export/deletion, and localisation settings |

The detailed platform breakdown is available in [Homie All-in-One Platform](docs/ALL_IN_ONE_PLATFORM.md).

## Dashboard

The Homie dashboard provides a visual alternative to slash-command configuration. It automatically adapts to desktop, tablet, and mobile screens and includes:

- guided first-time setup and contextual page instructions;
- channel, role, welcome, moderation, security, and community settings;
- ticket, suggestion, form, appeal, automation, feed, counter, poll, and role-panel management;
- message and embed publishing, editing, and scheduling;
- activity history, scoped API credentials, and server health;
- unsaved-change warnings, page search, contextual help, dark/light themes, and reduced-motion support.

Discord sign-in only shows servers where the signed-in user is the owner or has **Manage Server** or **Administrator**. See the [Dashboard User Guide](dashboard/README.md).

## Add Homie to a server

1. [Invite Homie](https://discord.com/oauth2/authorize?client_id=1492673658567524353&permissions=8&integration_type=0&scope=bot+applications.commands).
2. Move Homie's role above every role it needs to create, assign, remove, or reposition.
3. Run `/setup` to check Discord permissions and missing configuration.
4. Run `/config view` for a readable overview of the current server settings.
5. Configure the features your community needs through the dashboard or slash commands.
6. Run `/setup` again and test member-facing features before announcing them.

The recommended sequence and working examples are in the [Public Server Setup Guide](docs/PUBLIC_SERVER_SETUP_GUIDE.md).

## Essential first commands

```text
/setup
/config view
/serverconfig welcome-channel
/config set-mod-log-channel
/serverconfig welcome
/automod status
/security status
/colour sync
```

Only configure features the server intends to use. An unset channel or disabled module remains inactive.

## Discord permissions and role hierarchy

Homie only performs actions allowed by Discord. Depending on the enabled features, it may need:

- Manage Roles
- Manage Channels
- Manage Messages
- Moderate Members
- Kick Members
- Ban Members
- View Audit Log
- Send Messages and Embed Links
- Add Reactions and Read Message History
- Connect and Speak for music

Homie's highest role must be above managed colour roles, autoroles, quarantine or verification roles, reaction-role targets, level rewards, and any role staff expect it to assign. Administrator is convenient during initial setup, but server owners may replace it with a carefully selected permission set afterward.

## Command reference

Homie registers a broad suite of Discord application commands. Use `/help` inside Discord for server-aware help; disabled features and commands unavailable to a member are handled according to configuration and permissions.

The complete grouped reference is maintained in [docs/COMMAND_REFERENCE.md](docs/COMMAND_REFERENCE.md), covering:

- moderation and cases;
- security and automod;
- support, tickets, forms, suggestions, and appeals;
- roles, colours, levels, achievements, and economy;
- community features and creator alerts;
- publishing, automation, feeds, counters, voice, and music;
- smart replies, memory, privacy, language, and integrations.

## Message placeholders

Supported message editors replace placeholders when a message is sent. Availability depends on the feature:

| Placeholder | Result |
| --- | --- |
| `{user}` | Mentions the relevant Discord member |
| `{username}` | Displays the member or creator username |
| `{server}` | Displays the Discord server name |
| `{url}` | Inserts a supported creator or feed URL |
| `{age}` | Displays a saved birthday age when permitted |
| `{ageWithSuffix}` | Formats an age such as `21st` or `32nd` |
| `\n` | Creates a new line in supported text inputs |

Example:

```text
Welcome {user} to {server}!\nRead the rules, choose your roles, and make yourself at home.
```

## Data and privacy

Homie stores only the data needed for enabled features, including server configuration, moderation records, reminders, birthdays, creator usernames, XP, achievements, optional smart memory, tickets, and scheduled jobs.

- Anonymous vents are published without retaining the submitter's identity.
- `/privacy export` provides a member's stored data for that server.
- `/privacy delete confirm:DELETE` removes optional data and pseudonymises records that must remain for moderation integrity.
- Dashboard sessions are HTTP-only and expire automatically.
- Integration API keys are scoped to one server, read-only, revocable, and displayed once.

Read the [Privacy Policy](docs/PRIVACY_POLICY.md) and [Terms of Service](docs/TERMS_OF_SERVICE.md) for the full public policy.

## Documentation

| Guide | Audience |
| --- | --- |
| [Public Server Setup Guide](docs/PUBLIC_SERVER_SETUP_GUIDE.md) | Discord server owners and administrators |
| [Command Reference](docs/COMMAND_REFERENCE.md) | Members, moderators, and administrators |
| [Dashboard User Guide](dashboard/README.md) | Server owners and administrators |
| [All-in-One Platform](docs/ALL_IN_ONE_PLATFORM.md) | Complete feature overview |
| [Privacy Policy](docs/PRIVACY_POLICY.md) | All users |
| [Terms of Service](docs/TERMS_OF_SERVICE.md) | All users |

## Support

For setup questions, troubleshooting, bug reports, or feature help, join the [Homie support server](https://discord.gg/RjuSrGXHSa).
