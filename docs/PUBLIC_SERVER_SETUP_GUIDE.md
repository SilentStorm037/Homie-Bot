# Homie Public Server Setup Guide

This guide is for server owners/admins who invite the verified public Homie bot to a Discord server and want to configure it from a clean state.

Homie is a verified public Discord community bot for moderation, welcome flows, streaming alerts, achievements, birthdays, colour roles, leveling, anonymous venting, giveaways, reminders, smart replies, reaction roles, starboard, utility commands, and community engagement.

Achievements and leveling are linked: when a member unlocks an achievement, Homie can award XP based on the achievement tier, helping achievement progress feed directly into the server's XP leaderboard.

## First-Time Setup Overview

When Homie joins a new server, it starts with no hard-coded server channels or roles. Each server must configure its own channels, roles, and feature settings.

Recommended first setup order:

1. Invite Homie with the required permissions.
2. Move Homie's role high enough in the role hierarchy.
3. If the server is empty and you want Homie to build it for you, use a server template.
4. Run `/setup` to see missing configuration.
5. Configure logging and moderation channels.
6. Configure welcome/leave messages.
7. Configure achievements.
8. Configure leveling and colour roles.
9. Configure Twitch/TikTok live alerts.
10. Configure optional community features.
11. Run test commands before announcing features publicly.

## Guided Dashboard Setup

The dashboard is the quickest way to configure a new server without memorising commands. Its **Get started** page checks permissions, explains the recommended order, and provides safe server-structure presets where available.

Recommended dashboard workflow:

1. Sign in with Discord.
2. Select the server from the server switcher.
3. Open **Get started** and review the permission check.
4. Use **Channels & roles** to connect destinations and managed roles.
5. Configure **Protection** before opening the server to new members.
6. Personalise **Welcome & rewards**.
7. Add optional **Member support**, **Connections**, and **Automation** tools.
8. Return to **Home** and review setup health.
9. Run `/setup` and `/config view` in Discord as a final check.

The dashboard never bypasses Discord permissions or role hierarchy. Homie's role must still be above every role it creates or assigns.

### Understanding Setup Completion

The **Home** and **Get started** pages display a Setup Completion checklist showing configured channel destinations and active features. This checklist is a guide to what has and has not been configured; it is not a requirement to reach 100%.

A server should configure only the features that are useful for its community. Optional destinations such as Forms, Modmail, creator alerts, appeals, or tickets may remain unconfigured without preventing other Homie features from working. The full scoring explanation, list of all checklist items, recommended workflow, and troubleshooting guidance are available in the [Setup Completion Checklist Guide](SETUP_COMPLETION_CHECKLIST.md).

## Required Bot Permissions

Homie works best with:

- View Channels
- Send Messages
- Embed Links
- Attach Files
- Read Message History
- Add Reactions
- Manage Messages
- Manage Roles
- Moderate Members
- Kick Members
- Ban Members
- Use Slash Commands

For colour roles, autoroles, reaction roles, and moderation roles, Homie's highest role must be above the roles it needs to manage.

If Homie says it cannot assign or move a role, move Homie's role higher in Server Settings -> Roles.

## Core Setup Commands

### `/setup`

Runs a setup audit for the server and reports missing configuration, permissions, and likely setup problems.

Use this immediately after inviting Homie:

```text
/setup
```

### `/config view`

Shows the current server configuration for Twitch, TikTok, announcements, updates, mod logs, smart replies, inactivity roles, and related bot settings.

```text
/config view
```

### `/serverconfig`

Configures general community features:

- welcome channel
- leave channel
- server log channel
- starboard channel
- autorole
- welcome messages
- starboard
- leveling

Useful first commands:

```text
/serverconfig welcome-channel channel:#welcome
/serverconfig leave-channel channel:#goodbye
/serverconfig server-log-channel channel:#server-logs
/serverconfig autorole role:@Member
/serverconfig lock-role role:@Member
```

Clear a setting:

```text
/serverconfig clear target:welcome channel
```

## Welcome And Leave System

Homie can post a welcome message when a member joins and a leave message when a member leaves.

Welcome messages support placeholders:

- `{user}` - mentions the new member
- `{username}` - the user's username
- `{server}` - server name
- `{membercount}` - current member count

New lines use `\n`.

Example:

```text
/serverconfig welcome enabled:true image:true random:true
```

Random welcome messages:

```text
/serverconfig welcome enabled:true random:true
```

Custom welcome message:

```text
/serverconfig welcome enabled:true random:false message:Welcome {user} to {server}!\n\nYou are member #{membercount}.
```

Welcome image:

```text
/serverconfig welcome enabled:true image:true
```

Disable welcome images:

```text
/serverconfig welcome enabled:true image:false
```

Leave message:

```text
/serverconfig welcome enabled:true leave_message:{user} left {server}.
```

## Achievements System

Homie includes a full achievement system with unlock cards, public profiles, progress tracking, backfill scanning, and server-level configuration.

Achievements can be earned through:

- message activity
- server age
- boosting
- reactions
- commands
- birthdays
- voice activity
- events
- special actions
- milestone completion

### Configure Achievement Announcements

Set the achievement channel:

```text
/achievementconfig channel channel:#achievements
```

Enable achievement tracking:

```text
/achievementconfig toggle enabled:true
```

Enable unlock announcements:

```text
/achievementconfig announce enabled:true
```

View achievement setup:

```text
/achievementconfig view
```

### User Achievement Commands

View a user's unlocked achievements:

```text
/achievements view
/achievements view user:@Member
```

The view uses buttons for page navigation.

List available achievements:

```text
/achievements list
/achievements list category:messages
```

Check progress toward a specific achievement:

```text
/achievements progress achievement:250 Messages Sent
```

Show leaderboard:

```text
/achievements leaderboard
```

Preview an achievement card:

```text
/achievements test-card
```

### Achievement Backfill

Backfill scans existing accessible message history and current members to grant achievements that can be detected from existing Discord data.

Recommended first run:

```text
/achievements backfill messages-per-channel:1000 announce:false
```

Use `announce:false` for the first scan to avoid posting lots of unlock cards at once.

If achievement XP rewards were added after members already unlocked achievements, you can also sync missing XP during backfill:

```text
/achievements backfill messages-per-channel:1000 announce:false sync-xp:true xp-channel:#private-admin-channel
```

`sync-xp:true` awards XP for unlocked achievements that have not already paid XP. `xp-channel` is optional and is only used for that one backfill run, so admins can send the XP report to a private channel without pinging members.

Backfill can detect:

- message totals from scanned history
- daily/weekly message peaks from scanned history
- first message
- attachments
- stickers
- emojis in messages
- mentions
- exact 200-character messages
- wall-of-text messages
- polls if exposed by Discord history
- message-in-every-visible-channel progress
- server age achievements
- current server booster achievement

Backfill cannot reliably reconstruct old:

- voice time
- muted time
- reaction counts by user
- deleted messages
- historical boost streaks
- old command usage
- invite counts unless already tracked

Homie needs View Channel and Read Message History in any channel you want scanned.

## Leveling / XP

Homie gives XP for server messages when leveling is enabled. Users can view ranks and leaderboards.

Enable/disable leveling:

```text
/serverconfig leveling enabled:true
```

View rank:

```text
/level rank
/level rank user:@Member
```

View leaderboard:

```text
/level leaderboard
```

Admin XP controls:

```text
/level add-xp user:@Member amount:100
/level remove-xp user:@Member amount:50
/level set-xp user:@Member amount:1000
/level reset user:@Member
```

## Colour Roles

Homie can create and manage personal colour roles.

Recommended setup:

```text
/colour sync
```

This creates/verifies the managed colour roles.

Move colour roles above a target role:

```text
/colour position above:@Member
```

Users choose a colour:

```text
/colour set colour:Blue
```

Show colour palette:

```text
/colour list
```

Clear your colour:

```text
/colour clear
```

Admin custom colours:

```text
/colour add name:My Colour hex:#123abc
/colour add-gradient name:Sunset start:#ff3366 end:#ffaa00
/colour add-holographic name:Holo
/colour remove-custom name:My Colour
```

Enhanced gradient/holographic roles require Discord's enhanced role style support on the server. Solid colours work normally.

## Twitch Live Notifications

Users can link Twitch accounts. Homie checks live status and posts notifications.

Set default Twitch alert channel:

```text
/config set-twitch-channel channel:#live-alerts
```

Clear it:

```text
/config clear-twitch-channel
```

Set a special channel for one user:

```text
/config set-special-twitch user:@Streamer channel:#streamer-alerts
```

User links Twitch:

```text
/twitchlink username:twitchname
```

User unlinks:

```text
/twitchunlink
```

Check link:

```text
/twitchcheck
/twitchcheck user:@Member
```

Admin set/remove Twitch link:

```text
/twitchset user:@Member username:twitchname
/twitchremove user:@Member
```

Default Twitch message:

```text
/twitchdefault set message:{username} is LIVE on Twitch!\n\n{url} ping:member
```

Ping options:

- no one
- member
- everyone
- role

View default:

```text
/twitchdefault view
```

Clear default:

```text
/twitchdefault clear
```

Custom user Twitch message:

```text
/twitchmessage set message:{username} is live!\n\n{url}
```

Optional custom notification image can be attached when setting a custom Twitch message.

View/remove:

```text
/twitchmessage view
/twitchmessage remove
```

Test notification:

```text
/twitch test
/twitch test channel:#test-channel
```

## TikTok Live Notifications

TikTok notifications are separate from Twitch.

Set default TikTok alert channel:

```text
/config set-tiktok-channel channel:#live-alerts
```

Set a special channel for one user:

```text
/config set-special-tiktok user:@Creator channel:#creator-alerts
```

User links TikTok:

```text
/tiktoklink username:tiktokname
```

User unlinks:

```text
/tiktokunlink
```

Check link:

```text
/tiktokcheck
/tiktokcheck user:@Member
```

Admin set/remove TikTok link:

```text
/tiktokset user:@Member username:tiktokname
/tiktokremove user:@Member
```

Default TikTok message:

```text
/tiktokdefault set message:{username} is LIVE on TikTok!\n\n{url} ping:member
```

View/clear:

```text
/tiktokdefault view
/tiktokdefault clear
```

TikTok diagnostics:

```text
/tiktokdefault status
/tiktokdefault status user:@Member
```

Reset live state:

```text
/tiktokdefault reset-live
/tiktokdefault reset-live user:@Member
```

Test notification:

```text
/tiktokdefault test
/tiktokdefault test user:@Member channel:#test-channel
```

## Anonymous Venting

Homie can post anonymous vents into a configured channel without storing the author's identity in the vent post.

Set vent channel:

```text
/ventconfig channel channel:#anonymous-vent
```

View setup:

```text
/ventconfig view
```

Clear channel:

```text
/ventconfig clear
```

User submits a vent:

```text
/vent
```

Homie opens a private modal. Vents reject links, mentions, `@everyone`, and `@here`.

## Birthdays

Homie can store birthdays, post birthday celebrations, generate birthday cards, optionally show age, and assign temporary birthday roles.

User sets birthday:

```text
/birthday set day:15 month:1
/birthday set day:15 month:1 year:2000 visibility:public
```

Visibility options:

- public, show age if year is saved
- public, hide age
- private, no celebration

User views/removes birthday:

```text
/birthday view
/birthday remove
```

Upcoming/today:

```text
/birthday next
/birthday today
```

Change privacy:

```text
/birthday privacy visibility:no-age
```

Admin configuration:

```text
/birthdayconfig channel channel:#birthdays
/birthdayconfig toggle enabled:true
/birthdayconfig time time:09:00 timezone:Europe/London
/birthdayconfig age-visibility mode:user
```

Optional birthday role:

```text
/birthdayconfig role role:@Birthday
/birthdayconfig clear-role
```

Custom birthday text:

```text
/birthdayconfig message message:Happy birthday {user}! You are {ageWithSuffix} today!
```

Admin set birthday for a user:

```text
/birthdayconfig set-user user:@Member day:15 month:1 year:2000
```

Test celebration:

```text
/birthdayconfig test
/birthdayconfig test user:@Member channel:#test-channel
```

## Starboard

Starboard saves memorable messages when enough users react with the configured emoji set.

Set starboard channel:

```text
/serverconfig starboard-channel channel:#starboard
```

Enable starboard:

```text
/serverconfig starboard enabled:true threshold:10 emojis:👑 ⭐ 🔥
```

When a message gets the threshold number of matching reactions, Homie posts it to the starboard channel. If multiple emojis are configured, Homie counts the combined total across all allowed emojis.

View the current starboard emoji set:

```text
/serverconfig starboard-emojis
```

## Smart Replies

Homie uses context-aware smart replies instead of unreliable freeform AI mode. It reads direct mentions, replies, recent channel context, custom taught replies, and the selected personality style, then decides whether to answer or stay quiet.

Configure mode:

```text
/smartconfig mode mode:mentions
```

Choose the reply engine:

```text
/smartconfig engine engine:rules
```

Engine options:

```text
rules    - fastest and safest; uses Homie's built-in context engine
hybrid   - balanced smart reply engine for casual chat
local-ai - advanced smart reply engine when available
```

Allow a channel:

```text
/smartconfig add-channel channel:#chat
```

Remove a channel:

```text
/smartconfig remove-channel channel:#chat
```

Set personality:

```text
/smartconfig personality personality:sassy
```

Set cooldown:

```text
/smartconfig cooldown seconds:5
```

### Smart Memory

Smart memory is optional and off by default. It does not automatically learn from chat. Homie only remembers short notes that users or admins explicitly save, and those memories are used only as background context for smart replies.

Enable or disable smart memory:

```text
/smartmemory toggle enabled:true
/smartmemory toggle enabled:false
```

Enable or disable natural learning:

```text
/smartmemory learning enabled:true
/smartmemory learning enabled:false
```

Natural learning lets Homie save safe, simple preferences from normal chat, such as favourite games, nicknames, streaming platform, and "I prefer..." statements. It does not save every message, and it skips links, mentions, passwords/tokens, contact details, and sensitive personal categories.

Natural learning also stores where the memory came from by channel ID. Homie prefers memories from the current channel so meme-channel conversations stay meme-relevant, general-chat conversations stay general-relevant, and channel names can change without breaking context. If a topic from one channel is clearly discussed in another channel, Homie can still use related cross-channel memory.

Save a memory about yourself:

```text
/smartmemory remember-me memory:I like Valorant and usually stream on TikTok.
```

View or clear your own saved memories:

```text
/smartmemory my-view
/smartmemory my-clear
```

Admin: save server-wide context:

```text
/smartmemory remember-server memory:This server is an 18+ chill community called Homies Without Homes.
```

Admin: save, view, remove, or clear memories for a specific user:

```text
/smartmemory remember-user user:@Member memory:Member prefers short practical advice.
/smartmemory view-user user:@Member
/smartmemory forget-user user:@Member id:MEMORY_ID
/smartmemory clear-user user:@Member
```

Admin: view, remove, or clear server-wide memories:

```text
/smartmemory view-server
/smartmemory forget-server id:MEMORY_ID
/smartmemory clear-server
```

Admin: view or clear memories learned from a specific channel:

```text
/smartmemory view-channel channel:#memes
/smartmemory clear-channel channel:#memes
```

If no channel is selected, Homie uses the channel where the command was run.

## Custom Replies / Teaching Homie

Admins can teach Homie custom replies.

Add/update:

```text
/teach add trigger:hello response:Hey there!
```

Remove:

```text
/teach remove trigger:hello
```

List:

```text
/teach list
```

## Tags

Tags are reusable saved messages.

Show tag:

```text
/tag show name:rules
```

Admin add/update:

```text
/tag add name:rules content:Read the rules in #rules.
```

Admin remove:

```text
/tag remove name:rules
```

List:

```text
/tag list
```

## Reaction Roles

Bind an emoji on a message to a role.

Add binding:

```text
/reactionrole add message_id:123 emoji:✅ role:@Member
```

Remove binding:

```text
/reactionrole remove message_id:123 emoji:✅
```

List:

```text
/reactionrole list
```

Homie needs Manage Roles and its role must be above the target role.

## Automod

Automod can delete/warn/timeout messages based on blocked words, mention limits, and caps limits.

View status:

```text
/automod status
```

Enable/disable:

```text
/automod toggle enabled:true
```

Add blocked word:

```text
/automod blockword word:badword
```

Remove blocked word:

```text
/automod unblockword word:badword
```

Set limits:

```text
/automod limits mentions:5 caps_percent:80
```

## Moderation

Clear messages:

```text
/clear amount:100
/clear amount:100 user:@Member
```

Warn:

```text
/warn user:@Member reason:Rule break
```

Homie may try to send the warned user an automated moderation notice with the server name, reason, and moderator.

Warnings:

```text
/warnings view user:@Member
/warnings remove user:@Member index:1
/warninglist
```

Timeout/mute:

```text
/mute user:@Member minutes:10 reason:Cooldown
/unmute user:@Member
```

Kick/ban/unban:

```text
/kick user:@Member reason:Reason
/ban user:@Member reason:Reason
/unban user:User reason:Reason
```

For kicks and bans, Homie may try to send the affected user an automated moderation notice before the action is completed. If Discord blocks the message because of the user's privacy settings, the moderation action can still continue.

Mass kick by role:

```text
/masskick role:@Inactive reason:Cleanup whitelist_role:@DoNotKick
```

Mass kicks can also attempt moderation notices for affected users where Discord allows it.

Role management:

```text
/addrole user:@Member role:@Role
/removerole user:@Member role:@Role
```

Mod tools:

```text
/modtools slowmode seconds:10 channel:#chat
/modtools lock channel:#chat
/modtools unlock channel:#chat
```

`/modtools lock` denies `Send Messages` for the configured channel lock role. Set it with `/serverconfig lock-role`, usually to your verified/member role. If no lock role is set, Homie falls back to the autorole, then `@everyone`.

`/modtools unlock` restores the saved permission snapshot from the last Homie lock, returning the channel to its previous role overwrite setup.

Moderator notes:

```text
/note add user:@Member note:Context here
/note list user:@Member
/note remove user:@Member id:noteid
```

## Giveaways

Start giveaway:

```text
/giveaway start duration:1h winners:1 prize:Nitro channel:#giveaways
```

List active giveaways:

```text
/giveaway list
```

End giveaway:

```text
/giveaway end id:giveawayid
```

## Reminders

Create reminder:

```text
/remind me in:10m text:Check stream
/remind me in:2h text:Post update
/remind me in:1d text:Birthday setup
```

List:

```text
/remind list
```

Cancel:

```text
/remind cancel id:reminderid
```

## Polls

Create simple reaction poll:

```text
/poll question:What should we play? option1:Minecraft option2:Valorant option3:Fortnite
```

## Announcements And Updates

Set announcement channel:

```text
/config set-announce-channel channel:#announcements
```

Set update channel:

```text
/config set-update-channel channel:#updates
```

Send announcement:

```text
/announce
```

Send update:

```text
/update
```

Send a message to any selected channel:

```text
/say channel:#general
```

## Moderation Logs

Mod log channel:

```text
/config set-mod-log-channel channel:#mod-logs
```

## Inactivity Roles

Set inactivity roles:

```text
/config set-inactive-role days:7 role:@Inactive 7d
/config set-inactive-role days:30 role:@Inactive 30d
```

Clear:

```text
/config clear-inactive-role days:7
```

## Fun And Social Commands

Fun commands:

```text
/joke
/dadjoke
/coinflip
/8ball question:Will today be good?
/3amthoughts
/fact
/funfacts
/roast user:@Member
/compliment user:@Member
```

Marriage commands:

```text
/marry user:@Member
/divorce user:@Member
/marriagecheck
/marriagecheck user:@Member
```

Ping:

```text
/ping
```

## Support And Operations Setup

After the core community is working, configure any operational tools your staff needs.

### Tickets

Run `/ticket setup` with:

- a Discord **category** where Homie creates private ticket channels;
- a text channel for ticket logs and transcripts; and
- the staff role that should see and claim tickets.

Then publish a member-facing panel with `/ticket panel`. Staff can claim, add participants, remove participants, close, and list tickets through `/ticket` or the dashboard.

### Suggestions, Forms, Appeals, And Modmail

- `/suggestion channel` selects the suggestion destination.
- `/form create` defines an application or questionnaire; `/form panel` publishes access.
- `/appeal submit` opens the member appeal workflow and `/appeal review` supports staff decisions.
- `/modmail setup` connects private member DMs to a staff workflow.

Configure private staff destinations before publishing panels to members.

### Publishing And Scheduled Content

Use `/message send`, `/message edit`, and `/message schedule` for managed content. The dashboard provides plain-text, embed, and Discord JSON editors with previews. Homie suppresses unexpected mentions and records dashboard publishing activity.

### Automations, Feeds, Cleanup, And Counters

- `/automation create` builds a trigger-and-action workflow.
- `/feed add` subscribes a channel to a compatible RSS or Atom source.
- `/cleanup set` removes channel messages after a configured delay.
- `/counter setup` creates a live member or server-stat channel.
- `/voicehub setup` creates temporary voice rooms when members join a configured hub.

Start with one workflow at a time, test it in a staff channel, then use each command's `list` subcommand to confirm the saved configuration.

### Economy And Music

The optional economy provides balances, daily rewards, transfers, leaderboards, and audited staff adjustments through `/economy`.

The shared music player uses `/music play` to queue searches, URLs, and supported YouTube playlists. Members can inspect the queue, remove a song by position, pause, resume, skip, shuffle, repeat one/all, set volume, or stop playback. Homie needs **Connect** and **Speak** in the voice channel.

### Privacy And Integrations

Members can use `/privacy export`, `/privacy delete`, and `/privacy retention`. Administrators can create read-only, single-server integration credentials with `/apikey`; each secret is displayed only once and can be revoked.

The full list of operational commands and subcommands is maintained in the [Command Reference](COMMAND_REFERENCE.md).

## Public Server Setup Checklist

Use this checklist after adding Homie:

```text
1. Move Homie's role high enough.
2. Run /setup.
3. Run /config view.
4. Set mod log:
   /config set-mod-log-channel channel:#mod-logs
5. Set server log:
   /serverconfig server-log-channel channel:#server-logs
6. Set welcome channel:
   /serverconfig welcome-channel channel:#welcome
7. Enable welcome:
   /serverconfig welcome enabled:true image:true random:true
8. Set leave channel:
   /serverconfig leave-channel channel:#goodbye
9. Set autorole if needed:
   /serverconfig autorole role:@Member
   /serverconfig lock-role role:@Member
10. Set achievements channel:
   /achievementconfig channel channel:#achievements
11. Enable achievements:
   /achievementconfig toggle enabled:true
12. Enable achievement announcements:
   /achievementconfig announce enabled:true
13. Backfill achievements:
   /achievements backfill messages-per-channel:1000 announce:false
14. Sync colour roles:
   /colour sync
15. Position colour roles:
   /colour position above:@Member
16. Enable leveling:
   /serverconfig leveling enabled:true
17. Set starboard:
   /serverconfig starboard-channel channel:#starboard
   /serverconfig starboard enabled:true threshold:10 emojis:👑 ⭐ 🔥
18. Set vent channel:
   /ventconfig channel channel:#anonymous-vent
19. Set birthday channel:
   /birthdayconfig channel channel:#birthdays
   /birthdayconfig toggle enabled:true
20. Set live alert channels:
   /config set-twitch-channel channel:#live-alerts
   /config set-tiktok-channel channel:#live-alerts
21. Run /setup again.
```

## Suggested Public Announcement After Setup

```text
Homie is now fully set up in the server.

Homie handles welcome messages, achievements, colour roles, levels, birthdays, Twitch/TikTok live alerts, reminders, giveaways, polls, starboard, anonymous vents, and more.

Use /help to see what Homie can do.
```
