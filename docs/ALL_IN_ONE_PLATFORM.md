# Homie All-in-One Platform

Homie combines moderation, protection, logs, support, role management, community engagement, economy games, automation, publishing, music, smart replies, dashboard controls, and privacy tools in one verified Discord bot. Each server keeps its own settings, channels, roles, and enabled features.

## Setup and dashboard

- `/setup` audits permissions and missing configuration.
- `/config view` shows saved destinations.
- `/config set-X-channel` commands connect welcome, leave, logs, starboard, Quote Hall, anonymous posts, suggestions, birthdays, creator alerts, verification, modmail, announcements, updates, games, greetings, and NSFW meme channels.
- The dashboard gives server owners a visual setup flow, setup health, channel/role management, protection settings, welcome/rewards, support workflows, automation, publishing, and activity history.

## Moderation, protection, and logs

- Warnings, cases, notes, timeouts, kicks, bans, temporary bans, soft bans, message cleanup, slowmode, locks, and mass role kicks.
- Automod for blocked words, mentions, caps, invites, links/domains, emoji/newline/attachment floods, duplicate messages, and message-rate spam.
- Progressive Automod strikes and configurable enforcement.
- Anti-raid detection, quarantine, verification, minimum account age checks, and lockdown.
- Dedicated user, moderation, message, server, and voice log destinations.

## Roles and member onboarding

- Welcome and leave messages with placeholders, random welcome mode, welcome images, and optional DMs.
- Immediate and delayed autoroles.
- Reaction roles, button role panels, managed colour roles, gradient/holographic colour support where Discord allows it, and admin role tools.
- Verification channel and verified/quarantine role support.

## Support and staff workflows

- Tickets with panels, claims, participants, transcripts, and logs.
- Modmail routed to a staff channel.
- Suggestions with staff decisions.
- Modal forms for applications, registration, feedback, or custom submissions.
- Moderation appeals and feedback commands.

## Community and games

- Starboard with configured emojis and media preservation.
- Quote Hall image cards saved with `h! quote`.
- Anonymous posts and anonymous venting.
- Polls, giveaways, tags, highlights, invite tracking, birthdays, levels, achievements, and achievement cards.
- Homie Coins economy with `h! daily`, streaks, shop items, steal, bomb, shield, trap, lockpick, scratch cards, fishing, mining, pets, quests, crates, raffles, and gambling.
- Memes, ship cards, jokes, facts, 8-ball, compliments, roasts, AFK, avatar lookups, and playful marriage commands.

## Creator alerts, publishing, and automation

- Twitch and TikTok account links, server defaults, per-member live messages, role/everyone/creator pings, and test tools.
- `/message` for sending, editing, and scheduling messages or embeds.
- `/announce` and `/update` for configured announcement/update destinations.
- RSS/Atom feeds, cleanup rules, server counters, temporary voice hubs, and trigger/action automations.
- Music playback with queue controls, repeat, shuffle, volume, and stop.

## Smart replies, privacy, and integrations

- Smart replies can be limited by mode, channel allowlist, cooldown, personality, and engine.
- Homie only responds to messages that start with Homie or mention Homie when configured for mention-style replies.
- Optional smart memory can store explicit member, server, and channel context with view/clear controls.
- `/privacy export`, `/privacy delete`, and retention settings help manage stored data.
- `/apikey` creates revocable read-only integration keys scoped to one server.

Start with the [Public Server Setup Guide](PUBLIC_SERVER_SETUP_GUIDE.md), then use the [Feature Setup Playbook](FEATURE_SETUP_PLAYBOOK.md) and [Command Reference](COMMAND_REFERENCE.md) as needed.
