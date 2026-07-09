# Homie Bot

Homie is a verified public Discord community bot for servers that want moderation, welcome messages, colour roles, achievements, levelling, birthdays, Twitch and TikTok alerts, anonymous vents, starboard, reminders, polls, reaction roles, smart replies, and community tools in one bot.

Homie is designed to be configured from inside Discord with slash commands. You add the bot to your server, run the setup commands, choose your channels and roles, and enable the features your community wants.

## Add Homie To Your Server

[Add Homie to your Discord server](https://discord.com/oauth2/authorize?client_id=1492673658567524353&permissions=8&integration_type=0&scope=bot+applications.commands)

## Support And Links

- [Support Server](https://discord.gg/RjuSrGXHSa)
- [Terms of Service](docs/TERMS_OF_SERVICE.md)
- [Privacy Policy](docs/PRIVACY_POLICY.md)
- [Full Public Setup Guide](docs/PUBLIC_SERVER_SETUP_GUIDE.md)

## What Homie Can Do

- Moderate your server with warnings, mutes, kicks, bans, mass kicks, message clearing, slowmode, channel locks, mod notes, and moderation logs.
- Welcome new members with configurable welcome messages, random welcome templates, member numbers, and welcome images.
- Give members colour roles from a managed palette, including solid colours, gradients, holographic styles, and custom server colours.
- Track achievements and XP so members can unlock milestones, view progress, earn achievement cards, and climb leaderboards.
- Celebrate birthdays with saved birthday dates, optional ages, random celebration messages, birthday cards, and optional birthday roles.
- Send Twitch and TikTok live alerts with default server messages, custom user messages, optional pings, embeds, and test commands.
- Let members vent anonymously through a private form, with no public command trace and no stored submitter identity.
- Run community features like starboard, reaction roles, polls, giveaways, reminders, custom tags, auto roles, and fun commands.
- Use smart replies that can respond when Homie is mentioned, spoken to by name, or allowed in selected channels.

## Before You Start

You should configure Homie from an account that has permission to manage the server. Some commands also need Discord permissions such as Manage Roles, Manage Messages, Kick Members, Ban Members, Moderate Members, or Administrator.

Homie's role must be placed high enough in your Discord role list. If Homie needs to add, remove, create, delete, or move roles, its own role must be above the roles it manages. Discord does not allow any bot to manage roles that are equal to or higher than the bot's highest role.

If a command says Homie cannot manage a role, open Discord Server Settings, go to Roles, and move Homie's role higher.

## First-Time Setup Checklist

1. Add Homie with the invite link above.
2. Move Homie's role high enough in your server role hierarchy.
3. Run `/setup` to let Homie audit the server setup.
4. Run `/config view` to see the current server configuration.
5. Set the main output channels with `/config`, `/serverconfig`, `/achievementconfig`, `/birthdayconfig`, and `/ventconfig`.
6. Configure welcome messages with `/serverconfig welcome`.
7. Configure starboard with `/serverconfig starboard`.
8. Configure levelling with `/serverconfig leveling`.
9. Configure achievements with `/achievementconfig`.
10. Configure birthdays with `/birthdayconfig`.
11. Configure colour roles with `/colour sync`, then optionally `/colour position`.
12. Configure Twitch alerts with `/config set-twitch-channel` and `/twitchdefault set`.
13. Configure TikTok alerts with `/config set-tiktok-channel` and `/tiktokdefault set`.
14. Configure smart replies with `/smartconfig`.
15. Run `/config view` again to confirm everything is set.

## Server Templates For Empty Servers

Homie can help build a new empty Discord server from a ready-made template. A template can create the main role structure, categories, channels, channel permissions, game reaction roles, welcome setup, starboard, birthdays, achievements, XP levelling, anonymous venting, smart replies, and useful starter messages.

Available template variants:

- `community` - a general community layout with welcome, rules, announcements, chat, engagement, achievements, birthdays, venting, and staff areas.
- `gaming` - a gaming-focused layout with game roles, gaming channels, polls, giveaways, events, achievements, XP, and community chat.
- `creator` - a creator/community layout for streamers, content creators, updates, creator spaces, engagement, achievements, and live-community features.

Template commands are normal message commands, not slash commands. Replace `<variant>` with `community`, `gaming`, or `creator`, and replace `<serverId>` with the Discord server ID.

Preview what Homie will build:

```text
server template tailored by homie preview <variant> <serverId>
```

Apply a template:

```text
server template tailored by homie apply <variant> <serverId>
```

Clear a previously applied template so the server can be rebuilt from scratch:

```text
server template tailored by homie scratch <variant> <serverId>
```

Before applying a template, make sure Homie is already in the target server and Homie's role is high enough to manage the roles and channels it creates. After applying, run `/setup` and `/config view` inside the server to confirm everything is ready.

## Important Template Placeholders

Some commands let you write reusable messages. These placeholders are replaced automatically when Homie sends the message.

- `{user}` mentions the Discord member.
- `{username}` shows the member's username.
- `{server}` shows the server name.
- `{url}` shows a Twitch or TikTok live URL where supported.
- `{age}` shows the birthday age where supported.
- `{ageWithSuffix}` shows ages like `21st`, `22nd`, or `30th` where supported.
- `\n` creates a new line in supported message templates.

Example:

```text
Welcome {user} to {server}!\nGrab your roles, read the rules, and make yourself at home.
```

## Recommended Setup Order

### 1. Basic Server Setup

Run:

```text
/setup
/config view
```

Use `/setup` to check what Homie can see and what may still be missing. Use `/config view` whenever you want to confirm how the server is configured.

### 2. Core Channels

Set the channels Homie should use:

```text
/serverconfig welcome-channel channel:#welcome
/serverconfig leave-channel channel:#goodbye
/serverconfig server-log-channel channel:#server-logs
/config set-mod-log-channel channel:#mod-logs
/config set-announce-channel channel:#announcements
/config set-update-channel channel:#updates
```

You only need to set the channels you want to use.

### 3. Welcome Messages

Enable welcome messages:

```text
/serverconfig welcome enabled:True image:True random:True message:Welcome {user} to {server}!\nYou are member #{memberNumber}.
```

Use `image:True` if you want Homie to include the welcome card image. Use `random:True` if you want Homie to rotate through welcome message variants.

### 4. Colour Roles

Create or verify the managed colour roles:

```text
/colour sync
```

Show the palette:

```text
/colour list
```

Move all managed colour roles above a chosen role:

```text
/colour position above:@RoleName
```

Members can then choose:

```text
/colour set colour:Rose
```

### 5. Starboard

Set the starboard channel:

```text
/serverconfig starboard-channel channel:#starboard
```

Enable it:

```text
/serverconfig starboard enabled:True threshold:10 emoji::crown:
```

When enough people react to a message with the configured emoji, Homie saves that message to the starboard channel.

### 6. Levelling And Achievements

Enable XP levelling:

```text
/serverconfig leveling enabled:True
```

Set achievement announcements:

```text
/achievementconfig channel channel:#achievements
/achievementconfig toggle enabled:True
/achievementconfig announce enabled:True
```

Members can view progress with:

```text
/achievements view
/level rank
```

### 7. Birthdays

Set the birthday channel:

```text
/birthdayconfig channel channel:#birthdays
```

Enable celebrations:

```text
/birthdayconfig toggle enabled:True
```

Set the daily post time:

```text
/birthdayconfig time time:09:00 timezone:Europe/London
```

Members can save their birthday:

```text
/birthday set day:15 month:1
```

If a member includes a year, Homie can calculate the age depending on the server and user privacy settings.

### 8. Twitch Alerts

Set the default Twitch alert channel:

```text
/config set-twitch-channel channel:#live-now
```

Set the default Twitch message:

```text
/twitchdefault set message:{user} is live!\nWatch here: {url} ping:No one
```

Members link their own Twitch:

```text
/twitchlink username:yourname
```

Members can also set their own custom Twitch live message:

```text
/twitchmessage set message:{user} is streaming!\nCome say hi: {url}
```

### 9. TikTok Alerts

Set the default TikTok alert channel:

```text
/config set-tiktok-channel channel:#live-now
```

Set the default TikTok message:

```text
/tiktokdefault set message:{user} is live on TikTok!\nWatch here: {url} ping:No one
```

Members link their TikTok:

```text
/tiktoklink username:yourname
```

### 10. Anonymous Venting

Set the anonymous vent channel:

```text
/ventconfig channel channel:#anonymous-vent
```

Members use:

```text
/vent
```

Homie opens a private form. The submitted vent is posted anonymously to the configured vent channel.

### 11. Smart Replies

Choose where Homie can reply:

```text
/smartconfig mode mode:mentions
```

Choose the reply engine:

```text
/smartconfig engine engine:hybrid
```

Set the cooldown:

```text
/smartconfig cooldown seconds:5
```

If you want Homie to reply only in certain channels, use:

```text
/smartconfig add-channel channel:#general
/smartconfig remove-channel channel:#general
```

Members can invoke Homie by mentioning the bot or by saying Homie's name, depending on the configured mode.

## Public Command Guide

These are commands regular members can use, depending on the permissions and features enabled in your server.

### `/help`

Shows dynamic help for the current server.

Use it when you want to see what Homie can do in that server.

### `/ping`

Checks whether Homie is online and responding.

### `/vent`

Opens a private anonymous vent form. After submission, Homie posts the vent anonymously in the configured vent channel.

Links, mentions, `@everyone`, and `@here` are blocked for safety.

### `/colour set`

Gives you one of the server's managed colour roles.

Example:

```text
/colour set colour:Rose
```

### `/colour custom`

Chooses a server custom colour by name.

Use `/colour list` first to see the available names.

### `/colour list`

Shows the available colour choices as a compact palette image.

### `/colour clear`

Removes your personal colour role.

### `/achievements view`

Shows a user's unlocked achievements.

Use it without a user to view your own achievements, or select another user to view theirs.

### `/achievements list`

Lists available achievements. You can optionally filter by category.

Categories include messages, voice, reactions, invites, commands, special, collection, and global.

### `/achievements progress`

Shows progress towards a specific achievement for yourself or another selected user.

### `/achievements leaderboard`

Shows the server achievement leaderboard.

### `/level rank`

Shows your XP rank, level, and progress. You can optionally select another user.

### `/level leaderboard`

Shows the XP leaderboard in an embed.

### `/birthday set`

Saves your birthday.

Required:

- `day`: day of the month.
- `month`: month number.

Optional:

- `year`: birth year, used for age if allowed.
- `visibility`: choose public with age, public without age, or private.

Example:

```text
/birthday set day:15 month:1 visibility:Public, hide age
```

### `/birthday view`

Shows your saved birthday and privacy setting.

### `/birthday remove`

Deletes your saved birthday.

### `/birthday next`

Shows upcoming server birthdays.

### `/birthday today`

Shows birthdays happening today.

### `/birthday privacy`

Changes who can see your birthday or age.

### `/twitchlink`

Links your Discord account to your Twitch username for live alerts.

Example:

```text
/twitchlink username:silentcrazystorm
```

### `/twitchunlink`

Removes your linked Twitch account.

### `/twitchcheck`

Checks your linked Twitch account or another member's linked account.

### `/twitchmessage set`

Sets your custom Twitch live notification message.

Use `{user}`, `{username}`, `{url}`, and `\n`.

You can optionally attach a custom image for your Twitch notification.

### `/twitchmessage view`

Shows your current custom Twitch live message.

### `/twitchmessage remove`

Removes your custom Twitch live message so the server default is used again.

### `/twitch test`

Sends a one-off Twitch notification test. You can optionally choose a channel for the test.

### `/tiktoklink`

Links your Discord account to your TikTok username for live alerts.

### `/tiktokunlink`

Removes your linked TikTok account.

### `/tiktokcheck`

Checks your linked TikTok account or another member's linked account.

### `/tiktokmessage set`

Sets your custom TikTok live notification message.

Use `{user}`, `{username}`, `{url}`, and `\n`.

### `/tiktokmessage remove`

Removes your custom TikTok live message so the server default is used again.

### `/marry`

Sends a marriage request to another user.

### `/divorce`

Divorces a selected partner. If you do not select a user, Homie uses your first saved partner where applicable.

### `/marriagecheck`

Checks who you or another member is married to.

### `/remind me`

Creates a personal reminder.

Example:

```text
/remind me in:2h text:Check the event signup
```

Supported duration examples include `10m`, `2h`, and `1d`.

### `/remind list`

Lists your active reminders.

### `/remind cancel`

Cancels one of your reminders by reminder ID.

### `/poll`

Creates a simple reaction poll with two required options and up to two extra options.

### `/tag show`

Shows a saved server tag.

### `/tag list`

Lists saved server tags.

### `/feedback good`

Marks a Homie response as helpful. You can include an optional note.

### `/feedback bad`

Reports a bad Homie response with a note.

### `/smartmemory remember-me`

Saves a memory about yourself for Homie to use in smart replies.

Example:

```text
/smartmemory remember-me memory:I prefer short replies.
```

### `/smartmemory my-view`

Shows memories saved about you.

### `/smartmemory my-clear`

Clears memories saved about you.

### Fun Commands

- `/dadjoke`: sends a dad joke.
- `/joke`: sends a random joke.
- `/coinflip`: flips a coin.
- `/8ball`: answers a question.
- `/roast`: roasts a selected user.
- `/compliment`: compliments a selected user.
- `/3amthoughts`: sends a random late-night thought.
- `/fact`: sends a random fact.
- `/funfacts`: sends a random fun fact.

## Admin And Moderator Command Guide

These commands are intended for server admins, moderators, or trusted staff. Discord permissions and Homie's role position still apply.

### `/setup`

Audits Homie's setup and shows missing or incomplete configuration.

Run this after adding Homie and after major server changes.

### `/config view`

Shows the server's Homie configuration, including important channels, feature toggles, smart reply settings, moderation settings, birthday settings, colour settings, and other saved options.

### `/config set-twitch-channel`

Sets the default channel for Twitch live alerts.

### `/config clear-twitch-channel`

Clears the default Twitch live alert channel.

### `/config set-special-twitch`

Sets a special Twitch alert channel for one Discord user.

Use this when one creator should post alerts somewhere different from the default Twitch channel.

### `/config clear-special-twitch`

Clears a user's special Twitch alert channel.

### `/config set-tiktok-channel`

Sets the default TikTok live alert channel.

### `/config clear-tiktok-channel`

Clears the default TikTok live alert channel.

### `/config set-special-tiktok`

Sets a special TikTok alert channel for one Discord user.

### `/config clear-special-tiktok`

Clears a user's special TikTok alert channel.

### `/config set-greetings-channel`

Sets the scheduled greetings and 3AM thoughts channel.

### `/config clear-greetings-channel`

Clears the scheduled greetings channel.

### `/config set-announce-channel`

Sets where `/announce` posts messages.

### `/config clear-announce-channel`

Clears the announcement output channel.

### `/config set-update-channel`

Sets where `/update` posts update messages.

### `/config clear-update-channel`

Clears the update output channel.

### `/config set-mod-log-channel`

Sets the moderation log channel.

### `/config clear-mod-log-channel`

Clears the moderation log channel.

### `/config set-game-channel`

Sets the game or community channel used in help text and server guidance.

### `/config clear-game-channel`

Clears the game or community channel.

### `/config set-inactive-role`

Sets a role that can be used for an inactivity threshold.

Required:

- `days`: inactivity day threshold.
- `role`: role to use.

### `/config clear-inactive-role`

Clears the inactivity role for a selected day threshold.

## Community Configuration

### `/serverconfig welcome-channel`

Sets the welcome channel.

### `/serverconfig leave-channel`

Sets the leave message channel.

### `/serverconfig server-log-channel`

Sets the general server log channel.

### `/serverconfig starboard-channel`

Sets the starboard output channel.

### `/serverconfig autorole`

Sets the role automatically given to new members.

Homie's role must be above the auto role.

### `/serverconfig clear`

Clears a selected community config value.

Use this when you want to disable or reset a saved channel or role.

### `/serverconfig welcome`

Enables or disables welcome messages and configures welcome behaviour.

Options:

- `enabled`: turns welcome messages on or off.
- `image`: includes or removes the welcome image.
- `random`: rotates random welcome message variants.
- `message`: sets the welcome message template.
- `leave_message`: sets the leave message template.

### `/serverconfig starboard`

Enables or disables starboard and sets the threshold and emoji.

Example:

```text
/serverconfig starboard enabled:True threshold:10 emoji::crown:
```

### `/serverconfig leveling`

Enables or disables XP levelling.

## Moderation Commands

### `/clear`

Deletes messages. You choose how many messages to scan and can optionally target one user.

### `/warn`

Warns a user with an optional reason.

Homie may try to send the warned user an automated moderation notice with the server name, reason, and moderator.

### `/warninglist`

Shows users ranked by number of warnings.

### `/warnings view`

Shows warnings for a selected user.

### `/warnings remove`

Removes warnings from a user.

Depending on the selected mode, you can remove one warning or a range.

### `/mute`

Times out a user for a selected number of minutes with an optional reason.

### `/unmute`

Removes a user's timeout.

### `/kick`

Kicks a user with an optional reason.

Homie may try to send the user an automated moderation notice before the kick is completed. If the user's Discord privacy settings block bot messages, the kick can still continue and staff will see that the notice failed.

### `/ban`

Bans a user with an optional reason.

Homie may try to send the user an automated moderation notice before the ban is completed. If the user's Discord privacy settings block bot messages, the ban can still continue and staff will see that the notice failed.

### `/unban`

Unbans a selected banned user with an optional reason.

### `/masskick`

Kicks every member with a selected role.

Optional:

- `whitelist_role`: members with this role will not be kicked.

Use this carefully. Homie will only be able to act on members below its role hierarchy.

For moderation actions such as warnings, kicks, bans, and mass kicks, Homie may send automated notices to affected users when Discord allows it.

### `/modtools slowmode`

Sets slowmode in the selected channel, or the current channel if no channel is selected.

Set seconds to `0` to remove slowmode.

### `/modtools lock`

Locks a channel for `@everyone`.

### `/modtools unlock`

Unlocks a channel for `@everyone`.

### `/note add`

Adds a private moderator note to a user.

### `/note list`

Lists moderator notes for a user.

### `/note remove`

Removes a moderator note by ID.

## Role Management Commands

### `/addrole`

Adds a role to a selected user.

Homie and the command user must have permission to manage the role.

### `/removerole`

Removes a role from a selected user.

### `/createrole`

Creates a decorative role with no permissions.

Required:

- `name`: role name.
- `colour`: colour from Homie's colour palette.

Optional:

- `mentionable`: whether members can mention the role.

This is intended for safe decorative roles, not permission roles.

### `/deleterole`

Deletes a role below both Homie's role and the command user's role.

Homie will not delete managed roles, integration roles, `@everyone`, or roles too high in the hierarchy.

## Colour Role Admin Commands

### `/colour sync`

Creates or verifies all managed Homie colour roles for the server.

Run this after adding Homie, after adding custom colours, or if a colour role was manually deleted.

### `/colour position`

Moves all managed colour roles above a selected role.

Example:

```text
/colour position above:@Shelter Seekers
```

Homie's role must be high enough to move every managed colour role.

### `/colour add`

Adds a custom solid colour by name and hex code.

Example:

```text
/colour add name:Midnight hex:#123ABC
```

### `/colour add-gradient`

Adds a custom gradient colour role.

Requires servers that support enhanced role styles.

### `/colour add-holographic`

Adds a custom holographic role style.

Requires servers that support enhanced role styles.

### `/colour remove-custom`

Removes a custom colour from Homie's managed list.

## Achievement Commands

### `/achievementconfig channel`

Sets the achievement announcement channel.

### `/achievementconfig clear-channel`

Clears the achievement announcement channel.

### `/achievementconfig toggle`

Turns achievement tracking on or off.

### `/achievementconfig announce`

Turns achievement unlock announcements on or off.

### `/achievementconfig view`

Shows achievement configuration.

### `/achievements test-card`

Previews an achievement unlock card.

### `/achievements grant`

Admin tool to manually unlock an achievement for a user.

### `/achievements set-stat`

Admin tool to set an achievement stat for a user.

Example stats may include values such as invite count or other tracked counters.

### `/achievements reset-user`

Resets a user's achievement stats and unlocks.

### `/achievements backfill`

Scans existing server history and member data for achievements.

Options:

- `messages-per-channel`: how many recent messages to scan in each channel.
- `announce`: whether to post unlock images during the scan.
- `sync-xp`: whether to award missing XP for achievements already unlocked.
- `xp-channel`: one-time channel for achievement XP sync messages.

Use `xp-channel` if you want XP sync messages to go into a private staff channel.

## Birthday Admin Commands

### `/birthdayconfig channel`

Sets the birthday celebration channel.

### `/birthdayconfig message`

Sets the birthday message template.

Supported placeholders include `{user}`, `{username}`, `{age}`, `{ageWithSuffix}`, and `{server}`.

### `/birthdayconfig role`

Sets the optional temporary birthday role.

### `/birthdayconfig clear-role`

Clears the birthday role.

### `/birthdayconfig time`

Sets the daily birthday post time and optional timezone.

Example:

```text
/birthdayconfig time time:09:00 timezone:Europe/London
```

### `/birthdayconfig toggle`

Turns birthday celebrations on or off.

### `/birthdayconfig age-visibility`

Controls server-wide age display behaviour.

Modes:

- User controlled.
- Always show saved ages.
- Always hide ages.

### `/birthdayconfig view`

Shows birthday configuration.

### `/birthdayconfig test`

Sends a test birthday celebration. You can choose a user and a one-off test channel.

### `/birthdayconfig set-user`

Admin command to set a birthday for another member.

## Twitch Admin Commands

### `/twitchdefault set`

Sets the default Twitch live notification message for the server.

Supported placeholders include `{user}`, `{username}`, `{url}`, and `\n`.

The `ping` option controls who gets pinged:

- No one.
- `@everyone`.
- A selected role.
- The member going live.

If `ping` is set to role, select the role in the `role` option.

### `/twitchdefault view`

Shows the current default Twitch message.

### `/twitchdefault clear`

Resets the default Twitch message.

### `/twitchset`

Admin command to set a Twitch username for a selected Discord user.

### `/twitchremove`

Admin command to remove a selected user's Twitch link.

## TikTok Admin Commands

### `/tiktokdefault set`

Sets the default TikTok live notification message for the server.

Supported placeholders include `{user}`, `{username}`, `{url}`, and `\n`.

The `ping` option controls who gets pinged:

- No one.
- `@everyone`.
- A selected role.
- The member going live.

### `/tiktokdefault view`

Shows the current default TikTok message.

### `/tiktokdefault clear`

Resets the default TikTok message.

### `/tiktokdefault status`

Checks TikTok live detection and stored live state for yourself or a selected linked user.

This is useful when testing whether Homie currently sees a TikTok account as live.

### `/tiktokdefault reset-live`

Clears TikTok already-live state so the next live check can notify again.

You can reset one user or all TikTok users.

### `/tiktokdefault test`

Sends a test TikTok notification using the saved default or custom message.

You can select a user and a one-off test channel.

### `/tiktokset`

Admin command to set a TikTok username for a selected Discord user.

### `/tiktokremove`

Admin command to remove a selected user's TikTok link.

## Anonymous Vent Admin Commands

### `/ventconfig channel`

Sets the channel where anonymous vents are posted.

### `/ventconfig clear`

Clears the anonymous vent channel.

### `/ventconfig view`

Shows anonymous vent setup.

## Smart Reply Admin Commands

### `/smartconfig mode`

Controls where smart replies are allowed.

Use this to decide whether Homie replies only when mentioned, in selected channels, or according to the available server modes.

### `/smartconfig engine`

Chooses how smart replies are generated.

Available choices may include rule-based, hybrid, or smarter reply modes depending on the current bot configuration.

### `/smartconfig add-channel`

Allows smart replies in a selected channel.

### `/smartconfig remove-channel`

Removes a channel from the smart reply allowed channel list.

### `/smartconfig personality`

Sets Homie's smart reply personality for the server.

### `/smartconfig cooldown`

Sets the smart reply cooldown in seconds.

Use a short cooldown for active testing and a longer cooldown for busy servers.

## Smart Memory Admin Commands

### `/smartmemory toggle`

Enables or disables smart memory.

### `/smartmemory learning`

Enables or disables natural memory learning.

When enabled, Homie can remember useful context from conversations.

### `/smartmemory remember-user`

Saves a memory about a selected user.

### `/smartmemory remember-server`

Saves a server-wide memory.

### `/smartmemory view-user`

Views memories saved about a selected user.

### `/smartmemory view-server`

Views server-wide memories.

### `/smartmemory view-channel`

Views memories saved from a selected channel, or the current channel if no channel is selected.

### `/smartmemory forget-user`

Deletes one saved memory for a selected user by memory ID.

### `/smartmemory forget-server`

Deletes one server-wide memory by memory ID.

### `/smartmemory clear-user`

Clears all memories about a selected user.

### `/smartmemory clear-server`

Clears all server-wide memories.

### `/smartmemory clear-channel`

Clears memories saved from a selected channel, or the current channel if no channel is selected.

## Custom Reply And Review Commands

### `/teach add`

Adds or updates a custom server reply.

Required:

- `trigger`: what Homie should listen for.
- `response`: what Homie should reply with.

### `/teach remove`

Removes a custom reply by trigger or ID.

### `/teach list`

Lists custom replies.

### `/unknown list`

Lists recent messages Homie did not understand.

### `/unknown stats`

Shows unknown-message stats.

### `/feedback list`

Admin command to list recent feedback.

## AutoMod Commands

### `/automod status`

Shows automod settings.

### `/automod toggle`

Turns automod on or off.

### `/automod blockword`

Adds a blocked word or phrase.

### `/automod unblockword`

Removes a blocked word or phrase.

### `/automod limits`

Sets mention and caps limits.

Options:

- `mentions`: maximum mentions allowed.
- `caps_percent`: caps percentage threshold.

## Reaction Role Commands

### `/reactionrole add`

Binds an emoji on a message to a role.

Required:

- `message_id`: the message ID to watch.
- `emoji`: the emoji users react with.
- `role`: the role Homie gives.

### `/reactionrole remove`

Removes a reaction role binding from a message and emoji.

### `/reactionrole list`

Lists reaction role bindings.

## Tag Commands

### `/tag add`

Adds or updates a reusable server tag.

### `/tag remove`

Removes a tag.

### `/tag list`

Lists tags.

### `/tag show`

Shows a tag.

## Giveaway Commands

### `/giveaway start`

Starts a giveaway.

Required:

- `duration`: examples include `10m`, `2h`, and `1d`.
- `winners`: number of winners.
- `prize`: giveaway prize.

Optional:

- `channel`: where to post the giveaway.

### `/giveaway end`

Ends a giveaway by giveaway ID or message ID.

### `/giveaway list`

Lists active giveaways.

## Announcement Commands

### `/say`

Sends a message to a selected channel.

### `/announce`

Sends an announcement to the configured announcement channel.

Set the channel first with `/config set-announce-channel`.

### `/update`

Sends an update message to the configured update channel.

Set the channel first with `/config set-update-channel`.

### `/reload`

Reloads data files such as jokes, facts, and roasts without needing a full bot restart.

## Troubleshooting

### Slash commands do not show up

Restart Discord or wait a few minutes for Discord to refresh slash commands. Make sure Homie was invited with the `applications.commands` scope.

### Homie cannot assign or move a role

Move Homie's role higher in Server Settings, then try again. Homie cannot manage roles equal to or higher than its own highest role.

### Colour roles are missing

Run:

```text
/colour sync
```

Then run:

```text
/colour list
```

### Twitch or TikTok alerts do not post

Check:

```text
/config view
/twitchcheck
/tiktokcheck
/tiktokdefault status
```

Make sure the alert channel is set and the user has linked the correct username.

### Birthday celebrations do not post

Check:

```text
/birthdayconfig view
/birthday view
```

Make sure birthdays are enabled, a birthday channel is set, and the user's birthday is public enough to celebrate.

### Smart replies are too quiet

Check:

```text
/smartconfig mode
/smartconfig cooldown
/smartconfig add-channel
```

Make sure the mode allows replies where you are testing and the cooldown is not too high.

### Configuration looks wrong

Run:

```text
/config view
/setup
```

These commands are the best first check whenever a server setting does not behave as expected.

## Privacy Notes

Homie stores only the information needed to provide enabled server features, such as configuration choices, warnings, reminders, birthdays, linked creator usernames, achievement progress, XP, and optional smart memory. Anonymous vents are posted without storing who submitted them.

Read the full details here:

- [Privacy Policy](docs/PRIVACY_POLICY.md)
- [Terms of Service](docs/TERMS_OF_SERVICE.md)

## Need Help?

Join the support server:

[https://discord.gg/RjuSrGXHSa](https://discord.gg/RjuSrGXHSa)
