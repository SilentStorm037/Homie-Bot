# Homie Command Reference

This reference covers Homie's public, user-facing slash commands. Run `/help` inside Discord for contextual help based on the current server. Discord permissions, Homie's role position, and the server's enabled modules determine whether an action can run.

Commands marked **Admin** require elevated Discord permissions. Commands marked **Staff** are intended for configured moderation or support teams.

## Getting started and configuration

| Command | Access | Purpose and subcommands |
| --- | --- | --- |
| `/help` | Everyone | Shows dynamic help for the current server. |
| `/ping` | Everyone | Checks whether Homie is online and responding. |
| `/setup` | Admin | Audits permissions and highlights missing configuration. |
| `/config` | Admin | Views configuration and routes Twitch, TikTok, greetings, announcements, updates, moderation logs, games, and inactivity roles. Use `view` for the complete overview. |
| `/serverconfig` | Admin | Configures welcome/leave/log/starboard channels, autoroles, branding, lock role, welcome behavior, starboard emojis and threshold, and levelling. |
| `/language` | Admin | `set`, `status` — selects the language used for supported server responses. |
| `/stats` | Everyone | Displays server health and activity statistics. |

## Moderation and cases

| Command | Access | Purpose and subcommands |
| --- | --- | --- |
| `/warn` | Moderator | Warns a member and creates moderation history. |
| `/warninglist` | Moderator | Ranks members by active warning count. |
| `/warnings` | Moderator | `view`, `remove` — reviews or removes warnings. |
| `/cases` | Moderator | `view`, `user`, `recent`, `reason`, `void` — searches numbered moderation cases, updates reasons, and voids invalid cases. |
| `/mute` | Moderator | Applies a Discord timeout. |
| `/unmute` | Moderator | Removes a Discord timeout. |
| `/kick` | Moderator | Removes a member from the server. |
| `/ban` | Moderator | Permanently bans a member. |
| `/tempban` | Moderator | Bans a member until the durable expiry job unbans them. |
| `/softban` | Moderator | Bans and immediately unbans a member to remove recent messages. |
| `/unban` | Moderator | Removes an existing ban. |
| `/masskick` | Admin | Kicks members who have a selected role. Use with care. |
| `/clear` | Moderator | Deletes recent messages, optionally limited to one user. |
| `/modtools` | Moderator | `slowmode`, `lock`, `unlock` — controls channel slowmode and reversible permission locks. |
| `/note` | Moderator | `add`, `list`, `remove` — manages private staff notes about members. |
| `/addnickname` | Moderator | Changes a member's server nickname. |
| `/addrole` | Moderator | Assigns a manageable role to a member. |
| `/removerole` | Moderator | Removes a manageable role from a member. |
| `/createrole` | Admin | Creates a decorative role without elevated permissions. |
| `/deleterole` | Admin | Deletes a safe, manageable role below both Homie and the command user. |

## Automatic moderation and server security

| Command | Access | Purpose and subcommands |
| --- | --- | --- |
| `/automod` | Admin | `status`, `toggle`, `blockword`, `unblockword`, `limits`, `filters`, `domain`, `ignore-channel`, `ignore-role` — controls message filters, spam limits, warning DMs, domains, and exclusions. |
| `/security` | Admin | `status`, `anti-raid`, `roles`, `verification`, `lockdown` — configures join-rate monitoring, minimum account age, quarantine, verification, and emergency lockdown. |
| `/verify` | Everyone | Completes Homie's configured server verification flow. |

Automod can evaluate wildcard blocked phrases, excessive mentions, capital letters, invites, links, allowed or blocked domains, emoji floods, excess new lines, attachments, duplicate messages, and message-rate spam. Available punishments include deletion, warning, and timeout according to server configuration.

## Tickets, modmail, forms, suggestions, and appeals

| Command | Access | Purpose and subcommands |
| --- | --- | --- |
| `/ticket` | Everyone / Staff | `setup`, `panel`, `open`, `claim`, `add`, `remove`, `close`, `list` — configures and operates private support tickets with participants and transcripts. |
| `/modmail` | Admin / Staff | `setup`, `reply`, `close` — configures DM-based member support and staff replies. |
| `/suggest` | Everyone | Submits a suggestion to the configured channel. |
| `/suggestion` | Admin | `channel`, `review` — configures suggestions and records staff decisions. |
| `/form` | Everyone / Admin | `create`, `panel`, `open`, `list` — creates reusable modal forms and lets members submit them. |
| `/appeal` | Everyone / Staff | `submit`, `review` — submits or reviews a moderation appeal. |
| `/feedback` | Everyone / Admin | `good`, `bad`, `list` — rates Homie responses and lets staff review feedback. |

## Welcome, roles, colours, and self-service roles

| Command | Access | Purpose and subcommands |
| --- | --- | --- |
| `/reactionrole` | Admin | `add`, `remove`, `list` — binds message reactions to roles. |
| `/rolepanel` | Admin | `create`, `add`, `publish`, `list` — creates button-based self-service role menus. |
| `/colour` | Everyone / Admin | `set`, `list`, `sync`, `position`, `add`, `add-gradient`, `add-holographic`, `custom`, `remove-custom`, `clear` — manages personal and server-defined colour roles. |

Homie's highest Discord role must sit above every role it assigns or manages. Enhanced gradient and holographic role styles depend on Discord server capabilities.

## Levels, achievements, and economy

| Command | Access | Purpose and subcommands |
| --- | --- | --- |
| `/level` | Everyone / Admin | `rank`, `leaderboard`, `add-xp`, `remove-xp`, `set-xp`, `reset`, `reward-add`, `reward-remove`, `rewards`, `ignore-channel`, `ignore-role`, `multiplier` — manages XP progression and role rewards. |
| `/achievements` | Everyone / Admin | `view`, `list`, `progress`, `leaderboard`, `test-card`, `grant`, `set-stat`, `reset-user`, `backfill` — displays achievements and provides administrative progress tools. |
| `/achievementconfig` | Admin | `channel`, `clear-channel`, `toggle`, `announce`, `view` — configures achievement tracking and announcements. |
| `/economy` | Everyone / Admin | `balance`, `daily`, `pay`, `leaderboard`, `admin` — provides optional community currency and staff adjustments. |

Achievement unlocks can award XP, linking milestones to the server level system. Administrators can exclude channels or roles and set channel XP multipliers.

## Birthdays and member utilities

| Command | Access | Purpose and subcommands |
| --- | --- | --- |
| `/birthday` | Everyone | `set`, `view`, `remove`, `next`, `today`, `privacy` — manages a member's birthday and age privacy. |
| `/birthdayconfig` | Admin | `channel`, `message`, `role`, `clear-role`, `time`, `toggle`, `age-visibility`, `view`, `test`, `set-user` — configures daily birthday celebrations. |
| `/remind` | Everyone | `me`, `list`, `cancel` — creates durable personal reminders using durations such as `10m`, `2h`, or `1d`. |
| `/afk` | Everyone | Sets or clears AFK status; Homie informs members who mention an AFK user. |
| `/highlight` | Everyone | `add`, `remove`, `list` — sends a DM when configured keywords are mentioned. |
| `/invites` | Everyone | `user`, `leaderboard` — displays invite attribution and inviter rankings. |
| `/privacy` | Everyone | `export`, `delete`, `retention` — exports optional personal data, requests deletion, and explains retention. |

## Community content and engagement

| Command | Access | Purpose and subcommands |
| --- | --- | --- |
| `/poll` | Everyone | Creates an interactive timed poll. |
| `/giveaway` | Admin | `start`, `end`, `list`, `pause`, `resume`, `reroll` — operates durable giveaways and winner selection. |
| `/tag` | Everyone / Admin | `show`, `add`, `remove`, `list` — stores and publishes reusable server text. `\n` is converted to a new line. |
| `/marry` | Everyone | Sends a playful marriage request to another member. |
| `/divorce` | Everyone | Ends a saved marriage. |
| `/marriagecheck` | Everyone | Displays marriage information for a member. |
| `/vent` | Everyone | Opens a private anonymous vent form and publishes the content without retaining submitter identity. |
| `/ventconfig` | Admin | `channel`, `clear`, `view` — configures anonymous venting. |

## Twitch and TikTok alerts

| Command | Access | Purpose and subcommands |
| --- | --- | --- |
| `/twitchlink` | Everyone | Links the member's Twitch username. |
| `/twitchunlink` | Everyone | Removes the member's Twitch link. |
| `/twitchcheck` | Everyone | Checks a linked Twitch account. |
| `/twitchmessage` | Everyone | `set`, `remove`, `view` — manages a member-specific Twitch notification. |
| `/twitch` | Everyone | `test` — previews a Twitch notification. |
| `/twitchdefault` | Admin | `set`, `view`, `clear` — manages the server's default Twitch notification. |
| `/twitchset`, `/twitchremove` | Admin | Manages another member's Twitch link. |
| `/tiktoklink` | Everyone | Links the member's TikTok username. |
| `/tiktokunlink` | Everyone | Removes the member's TikTok link. |
| `/tiktokcheck` | Everyone | Checks a linked TikTok account. |
| `/tiktokmessage` | Everyone | `set`, `remove` — manages a member-specific TikTok notification. |
| `/tiktokdefault` | Admin | `set`, `view`, `clear`, `status`, `reset-live`, `test` — manages defaults and live-detection testing. |
| `/tiktokset`, `/tiktokremove` | Admin | Manages another member's TikTok link. |

Live-message editors support relevant placeholders including `{user}`, `{username}`, `{url}`, and `\n`. Administrators may configure no ping, `@everyone`, a selected role, or the creator according to the command options.

## Publishing, feeds, and automation

| Command | Access | Purpose and subcommands |
| --- | --- | --- |
| `/say` | Admin | Sends a plain message to a selected channel. |
| `/announce` | Admin | Sends to the configured announcements channel. |
| `/update` | Admin | Sends to the configured updates channel. |
| `/message` | Admin | `send`, `edit`, `schedule` — creates and manages plain messages or embeds. |
| `/feed` | Admin | `add`, `remove`, `list` — subscribes channels to RSS, Atom, YouTube, GitHub, and compatible feeds. |
| `/automation` | Admin | `create`, `remove`, `list` — creates trigger/action workflows that can reply, send, react, or change roles. |
| `/cleanup` | Admin | `set`, `remove`, `list` — automatically removes messages after configured delays. |
| `/counter` | Admin | `setup`, `remove`, `list` — creates live server-stat channel counters. |
| `/voicehub` | Admin | `setup` — configures join-to-create temporary voice channels. |
| `/reload` | Admin | Reloads supported public content files without a full bot restart. |

## Shared voice music

| Command | Access | Purpose |
| --- | --- | --- |
| `/music play` | Everyone | Searches for or queues a supported song, video URL, or YouTube playlist. |
| `/music pause`, `/music resume` | Everyone | Pauses or resumes playback. |
| `/music skip` | Everyone | Skips the current track. |
| `/music remove` | Everyone | Removes a queued song by its displayed queue position. |
| `/music repeat` | Everyone | Selects `off`, repeat one, or repeat all. |
| `/music shuffle` | Everyone | Randomises the waiting queue. |
| `/music queue` | Everyone | Shows the current track and queued songs. |
| `/music volume` | Everyone | Changes playback volume within configured limits. |
| `/music stop` | Everyone | Stops playback, clears the queue, and disconnects Homie. |

Members must be in a voice channel. Homie needs **Connect** and **Speak** permissions in that channel.

## Smart replies, custom replies, and memory

| Command | Access | Purpose and subcommands |
| --- | --- | --- |
| `/smartconfig` | Admin | `mode`, `engine`, `add-channel`, `remove-channel`, `personality`, `cooldown` — controls where and how contextual replies run. |
| `/smartmemory` | Everyone / Admin | Member tools: `remember-me`, `my-view`, `my-clear`. Administrative tools manage server, user, and channel memories and learning. |
| `/teach` | Admin | `add`, `remove`, `list` — creates deterministic custom trigger/reply pairs. |
| `/unknown` | Admin | `list`, `stats` — reviews messages Homie did not understand. |

Members can inspect and clear memories explicitly associated with them. Server administrators control whether smart memory and natural learning are enabled.

## Integration API keys

| Command | Access | Purpose and subcommands |
| --- | --- | --- |
| `/apikey` | Admin | `create`, `revoke`, `list` — manages revocable, read-only integration credentials scoped to one server. |

API secrets are displayed once. They authenticate with `Authorization: Homie <key>` and only grant the scopes selected at creation.

## Fun commands

| Commands | Purpose |
| --- | --- |
| `/dadjoke`, `/joke` | Sends a random joke. |
| `/coinflip` | Flips a virtual coin. |
| `/8ball` | Answers a question with an 8-ball response. |
| `/roast`, `/compliment` | Sends a playful roast or compliment. |
| `/3amthoughts` | Sends a random late-night thought. |
| `/fact`, `/funfacts` | Sends a random fact. |

## Common command problems

### A command is missing

Run `/help`, restart Discord, and allow a few minutes after command registration. Confirm Homie was invited with the `applications.commands` scope.

### Homie cannot manage a role

Move Homie's highest role above the target role. The command user must also be allowed to manage it.

### A configured feature does not post

Run `/setup` and `/config view`, then confirm that the destination channel still exists and Homie can view and send messages there.

### Long configuration output

`/config view` publishes its configuration in several readable messages. Feature-specific configuration commands provide the most detailed view of an individual module.
