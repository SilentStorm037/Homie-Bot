# Homie

**One Discord bot for moderation, safety, support, automation, community engagement, creator alerts, music, economy games, and everyday server management.**

Homie is a verified multi-server Discord bot designed to replace a pile of separate moderation and community bots. Server owners can configure it with slash commands or the dashboard, while members get simple prefix commands for fun, coins, memes, Quote Hall, ship cards, and utility tools.

[Add Homie to Discord](https://discord.com/oauth2/authorize?client_id=1492673658567524353&permissions=8&integration_type=0&scope=bot+applications.commands) - [Join the support server](https://discord.gg/QDG3drwfJF) - [Setup guide](docs/PUBLIC_SERVER_SETUP_GUIDE.md) - [Feature playbook](docs/FEATURE_SETUP_PLAYBOOK.md) - [Command reference](docs/COMMAND_REFERENCE.md)

## What Homie does

| Area | Included capabilities |
| --- | --- |
| Setup | `/setup`, `/config view`, unified `/config set-X-channel` destination commands, dashboard setup health, and guided configuration. |
| Logs | Dedicated user, moderation, message, server, and voice logs with `/serverconfig setup-log-channels`. |
| Moderation | Warnings, cases, notes, timeouts, kicks, bans, tempbans, softbans, message cleanup, slowmode, and channel locks. |
| Protection | Automod filters, progressive strikes, invite/domain rules, anti-raid, quarantine, verification, and lockdown. |
| Roles | Autoroles, delayed roles, reaction roles, role panels, colour roles, managed role creation/removal, and nickname tools. |
| Welcome and leave | Welcome channels, leave channels, random welcome messages, welcome images, welcome DMs, and placeholders. |
| Community | Starboard, Quote Hall image cards, anonymous posts, venting, polls, giveaways, birthdays, highlights, tags, and invites. |
| Economy games | Daily and weekly coins, streaks, occasional bonus items, shop items, steal, bomb, shield, trap, scratch cards, fishing, mining, pets, quests, crates, raffles, and gambling. |
| Creator alerts | Twitch, TikTok, and YouTube links, default live messages, custom creator messages, ping choices, and test tools. |
| Automation | Scheduled messages, cleanup rules, counters, temporary voice hubs, and trigger/action automations. |
| Music | Shared voice queue, search/URL playback, queue controls, repeat, shuffle, and volume. |
| Smart replies | Mention-aware smart replies, channel allowlists, cooldowns, personalities, taught replies, and optional memory controls. |
| Privacy and platform | Data export/deletion, retention settings, read-only API keys, dashboard audit history, and localisation. |

## Start here

1. Invite Homie.
2. Move Homie's role above every role it needs to manage.
3. Run `/setup`.
4. Run `/config view`.
5. Set channels with `/config set-X-channel`.
6. Run `/serverconfig setup-log-channels` if you want Homie to create staff log channels.
7. Configure only the features your server actually needs.
8. Test before announcing features to members.

The full step-by-step walkthrough is in [docs/PUBLIC_SERVER_SETUP_GUIDE.md](docs/PUBLIC_SERVER_SETUP_GUIDE.md).

## Essential setup commands

```text
/setup
/config view
/serverconfig setup-log-channels
/config set-welcome-channel channel:#welcome
/config set-leave-channel channel:#goodbye
/config set-mod-log-channel channel:#mod-logs
/config set-starboard-channel channel:#starboard
/config set-twitch-channel channel:#live-now
/config set-tiktok-channel channel:#live-now
/youtubeconfig channel channel:#live-now
/automod status
/security status
```

Most saved destinations use the `/config set-X-channel` format. YouTube live alerts currently use `/youtubeconfig channel` because the YouTube live system has its own dedicated configuration commands.

## Prefix commands

Homie uses slash commands for setup/admin workflows and prefix commands for fun/economy/community actions. Both prefixes work:

```text
h! daily
!h daily
```

Popular prefix commands:

```text
h! meme
h! quote
h! ship @Member
h! daily
h! weekly
h! shop
h! moneybag
h! richest
h! steal @Member
h! bomb @Member
h! joke
h! 8ball question
h! marry @Member
```

See the [Command Reference](docs/COMMAND_REFERENCE.md) for the complete current list.

## Documentation

| Guide | Best for |
| --- | --- |
| [Public Server Setup Guide](docs/PUBLIC_SERVER_SETUP_GUIDE.md) | Full step-by-step setup from a clean server. |
| [Feature Setup Playbook](docs/FEATURE_SETUP_PLAYBOOK.md) | Quick setup by feature area: logs, mod, roles, starboard, welcome, reaction roles, support, automation, and more. |
| [Command Reference](docs/COMMAND_REFERENCE.md) | Every slash command and prefix command grouped by purpose. |
| [Setup Completion Checklist Guide](docs/SETUP_COMPLETION_CHECKLIST.md) | Understanding the dashboard setup percentage. |
| [Dashboard User Guide](dashboard/README.md) | Using the web dashboard. |
| [All-in-One Platform](docs/ALL_IN_ONE_PLATFORM.md) | High-level feature overview. |
| [Privacy Policy](docs/PRIVACY_POLICY.md) | Data and privacy terms. |
| [Terms of Service](docs/TERMS_OF_SERVICE.md) | Public usage terms. |

## Support

For setup questions, troubleshooting, bug reports, or feature help, join the [Homie support server](https://discord.gg/QDG3drwfJF).
