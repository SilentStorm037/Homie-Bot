# Homie Public Server Setup Guide

This is the step-by-step setup guide for server owners and administrators using the public Homie bot. It follows the same order a new server should normally use: install, check permissions, connect destinations, enable safety, then switch on community features.

Use this guide together with the [Feature Setup Playbook](FEATURE_SETUP_PLAYBOOK.md), [Command Reference](COMMAND_REFERENCE.md), [Setup Completion Checklist Guide](SETUP_COMPLETION_CHECKLIST.md), and [Dashboard User Guide](../dashboard/README.md).

## 1. Invite Homie and prepare permissions

1. Invite Homie with the bot and application-command scopes.
2. Open **Server Settings -> Roles**.
3. Move Homie's role above every role Homie needs to manage.
4. Give Homie the permissions needed for the features you will use.
5. Keep private staff channels hidden from normal members.

Recommended permissions for a full setup:

- View Channels
- Send Messages
- Embed Links
- Attach Files
- Read Message History
- Add Reactions
- Manage Messages
- Manage Channels
- Manage Roles
- Manage Nicknames
- Moderate Members
- Kick Members
- Ban Members
- View Audit Log
- Connect and Speak for music

Homie cannot bypass Discord. If its role is below a target role, Discord blocks role assignment/removal even if the command is correct.

## 2. Run the first checks

```text
/setup
/config view
```

`/setup` checks permissions and missing configuration. `/config view` shows the destinations Homie currently has saved for the server.

## 3. Set core channel destinations

Homie uses `/config set-X-channel` for saved channel destinations.

```text
/config set-welcome-channel channel:#welcome
/config set-leave-channel channel:#goodbye
/config set-announce-channel channel:#announcements
/config set-update-channel channel:#bot-updates
/config set-game-channel channel:#community
/config set-greetings-channel channel:#general
```

Private and staff destinations:

```text
/config set-user-log-channel channel:#user-logs
/config set-mod-log-channel channel:#mod-logs
/config set-message-log-channel channel:#messages-logs
/config set-server-log-channel channel:#server-logs
/config set-voice-log-channel channel:#voice-logs
/config set-modmail-channel channel:#modmail
```

Community feature destinations:

```text
/config set-starboard-channel channel:#starboard
/config set-suggestion-channel channel:#suggestions
/config set-vent-channel channel:#venting
/config set-anonymous-channel channel:#anonymous
/config set-anonymous-log-channel channel:#anonymous-logs
/config set-quote-channel channel:#quote-hall
/config set-achievements-channel channel:#achievements
/config set-birthday-channel channel:#birthdays
/config set-verification-channel channel:#verify
/config set-nsfw-channel channel:#nsfw-memes
/config set-twitch-channel channel:#live-now
/config set-tiktok-channel channel:#live-now
/youtubeconfig channel channel:#live-now
```

Most channel destinations use `/config set-X-channel`. YouTube live notifications use `/youtubeconfig channel` because YouTube has dedicated link, default-message, status, reset, and test commands.

## 4. Create and route logs

```text
/serverconfig setup-log-channels
```

Homie creates or reuses a private `HOMIE LOGS` category with:

- `#user-logs` for joins, leaves, member role changes, nicknames, and profile events.
- `#mod-logs` for warnings, timeouts, kicks, bans, moderation cases, and Automod actions.
- `#messages-logs` for deleted, edited, and bulk-deleted messages, including attachment previews where available.
- `#server-logs` for role, channel, invite, and server changes.
- `#voice-logs` for voice joins, leaves, and moves.

Optional custom category name:

```text
/serverconfig setup-log-channels category_name:Staff Logs
```

Review the category permissions after setup so only staff can see private logs.

## 5. Configure moderation

```text
/warn user:@Member reason:Reason here
/mute user:@Member minutes:30 reason:Reason here
/unmute user:@Member
/kick user:@Member reason:Reason here
/ban user:@Member reason:Reason here
/tempban user:@Member duration:7d reason:Reason here
/softban user:@Member reason:Reason here
/unban user:USER_ID reason:Reason here
/clear amount:20
/modtools slowmode seconds:10 channel:#general
/modtools lock channel:#general
/modtools unlock channel:#general
/cases recent limit:10
/cases user user:@Member
/note add user:@Member note:Staff context
```

## 6. Configure protection and verification

```text
/automod status
/automod toggle enabled:true
/automod limits mentions:6 caps_percent:80
/automod filters block_invites:true warning_dms:true max_links:3 spam_messages:5 spam_window:10 timeout_minutes:10
/automod ignore-channel channel:#staff ignored:true
/automod ignore-role role:@Staff ignored:true
/security status
/security roles quarantine:@Quarantine verified:@Verified
/security verification enabled:true
/security anti-raid enabled:true join_threshold:8 window_seconds:30 account_age_days:3 action:quarantine auto_lockdown:true
```

Members verify with `/verify`.

## 7. Configure welcome, leave, and autoroles

```text
/config set-welcome-channel channel:#welcome
/config set-leave-channel channel:#goodbye
/serverconfig welcome enabled:true image:true random:true dm:false message:Welcome {user} to {server}!
/serverconfig welcome enabled:true leave_message:{username} left {server}.
/serverconfig autorole role:@Member
/serverconfig autorole-add role:@New delay_minutes:0
/serverconfig autorole-add role:@Settled delay_minutes:60
/serverconfig autorole-list
```

Supported welcome placeholders include `{user}`, `{username}`, `{server}`, `{membercount}`, and `\n` for line breaks.

## 8. Configure roles, colour roles, starboard, and reaction roles

Role tools:

```text
/addrole user:@Member role:@Role
/removerole user:@Member role:@Role
/createrole name:New Role colour:#5865F2 mentionable:false
/deleterole role:@Role
h! addnickname @Member New Nickname
```

Colour roles:

```text
/colour sync
/colour list
/colour set colour:Blue
/colour add name:Midnight hex:#123ABC
/colour add-gradient name:Sunset start:#FF4D6D end:#FF9F1C
/colour add-holographic name:Holo Dream
/colour position above:@Member
```

Starboard:

```text
/config set-starboard-channel channel:#starboard
/serverconfig starboard enabled:true threshold:3 emojis:star,fire,laugh
/serverconfig starboard-emojis
```

Reaction roles and role panels:

```text
/reactionrole add message_id:MESSAGE_ID emoji:yes role:@Verified
/reactionrole list
/rolepanel create name:games title:Choose your games description:Pick what you play exclusive:false max_roles:5
/rolepanel add panel:games role:@Minecraft label:Minecraft
/rolepanel publish panel:games channel:#roles
```

## 9. Configure support workflows

```text
/ticket setup category:Tickets logs:#ticket-logs staff:@Staff
/ticket panel channel:#support
/ticket open subject:I need help
/ticket claim
/ticket close reason:Resolved
/config set-modmail-channel channel:#modmail
/modmail reply message:Thanks, staff are checking this now.
/modmail close message:Closing this conversation now.
/config set-suggestion-channel channel:#suggestions
/suggest idea:Add a movie night
/suggestion review number:1 status:considering response:Staff will discuss this.
/form create name:staff-app description:Staff application questions:Why apply?|Experience?|Timezone? destination:#applications
/form panel name:staff-app channel:#apply
/appeal submit statement:I would like this reviewed case:12
/appeal review id:1 status:accepted response:Appeal accepted.
```

## 10. Configure anonymous posts, venting, and Quote Hall

```text
/config set-vent-channel channel:#venting
/vent
/ventconfig view
/config set-anonymous-channel channel:#anonymous
/config set-anonymous-log-channel channel:#anonymous-logs
/anonymous post
/anonymous view
/config set-quote-channel channel:#quote-hall
h! quote
/quote reset-number confirm:RESET
```

Use `h! quote` while replying to the member message you want saved.

## 11. Configure levels, achievements, and birthdays

```text
/serverconfig leveling enabled:true
/level rank
/level leaderboard
/level reward-add level:10 role:@Level 10
/config set-achievements-channel channel:#achievements
/achievementconfig toggle enabled:true
/achievementconfig announce enabled:true
/achievements view
/achievements list
/config set-birthday-channel channel:#birthdays
/birthdayconfig message message:Happy birthday {user}!
/birthdayconfig time time:09:00 timezone:Europe/London
/birthdayconfig toggle enabled:true
/birthday set day:5 month:8 year:2000 visibility:server
```

## 12. Configure Homie Coins, games, memes, ship, and fun

Economy and games are prefix-based. Both `h!` and `!h` work.
Daily rewards are claimable once per UTC day, while the visible cooldown counts down until the next available claim.

```text
h! daily
h! weekly
h! moneybag
h! pay @Member 250
h! richest
h! mint @Member 500 event prize
h! shop
h! buy shield
h! bag
h! shield
h! trap
h! lockpick
h! steal @Member
h! bomb @Member
h! scratch
h! buy rod
h! fish
h! buy pickaxe
h! mine
h! timeskip fish
h! buy egg
h! hatch
h! pets
h! getquest
h! startquest
h! quest
h! gamble 250
h! gamble 25%
h! gamble all
```

Daily rewards reset once per UTC day. Weekly rewards give a larger random Homie Coin bonus, show cooldowns as days, hours, minutes, and seconds, and can occasionally include a bonus item. Steal has a 25% base success chance, a 5-minute cooldown, and 3 attempts per user per UTC day. Fishing and mining each have a 30-minute cooldown and 3 uses per user per server per day.

Fun and social commands:

```text
h! meme
h! meme ProgrammerHumor
h! meme nsfw
h! joke
h! dadjoke
h! fact
h! funfacts
h! 3amthoughts
h! 8ball Will this server survive tonight?
h! compliment @Member
h! roast @Member
h! coinflip
h! afk grabbing food
h! avatarget @Member
h! ship @Member
h! ship @MemberA @MemberB
h! marry @Member
h! divorce @Member
h! marriagecheck @Member
```

NSFW meme categories only work in Discord NSFW channels or channels explicitly allowed with `/config set-nsfw-channel`.

## 13. Configure creator alerts

Creator alerts support Twitch, TikTok, and YouTube. The dashboard **Connections** page shows each platform in its own tab.

Twitch:

```text
/config set-twitch-channel channel:#live-now
/twitchdefault set message:{username} is live! {url} ping:role role:@Live Ping
/twitchlink username:creatorname
/twitchmessage set message:{username} is live! {url}
/twitch test channel:#live-now
```

TikTok:

```text
/config set-tiktok-channel channel:#live-now
/tiktokdefault set message:{username} is live! {url} ping:role role:@Live Ping
/tiktoklink username:creatorname
/tiktokmessage set message:{username} is live! {url}
/tiktokdefault test user:@Member channel:#live-now
```

YouTube:

```text
/youtubeconfig channel channel:#live-now
/youtubedefault set message:{username} is live! {url} ping:role role:@Live Ping
/youtubelink channel:@creatorhandle
/youtubemessage set message:{username} is live! {url}
/youtubedefault test user:@Member channel:#live-now
```

YouTube live alerts require a YouTube Data API v3 key in `.env` as `YOUTUBE_API_KEY`. Handles can be entered with or without `@`; direct live/watch URLs can be used as fallbacks from the dashboard.

## 14. Configure publishing, automation, counters, voice hubs, and music

```text
/say channel:#general message:Hello everyone
/announce
/update
/message send channel:#announcements title:Event description:Tonight at 8 colour:#5865F2
/message edit channel:#announcements message_id:MESSAGE_ID content:Updated text
/message schedule channel:#announcements in:2h title:Reminder description:Event soon
/automation create name:rules phrase:rules action:reply message:Read #rules
/cleanup set channel:#bot-spam after_seconds:3600 bots_only:true
/counter setup channel:VoiceChannel type:members name:Members: {count}
/voicehub setup hub:Join To Create category:Voice name:{username}'s room limit:5
/music play query:song or YouTube URL
/music queue
/music stop
```

## 15. Configure smart replies carefully

Recommended non-intrusive start:

```text
/smartconfig mode mode:mentions
/smartconfig cooldown seconds:60
/smartconfig add-channel channel:#bot-chat
/smartconfig personality personality:friendly and concise
```

Memory controls:

```text
/smartmemory toggle enabled:true
/smartmemory learning enabled:false
/smartmemory remember-me memory:I prefer short answers.
/smartmemory my-view
/smartmemory my-clear
/smartmemory remember-server memory:Server-wide context
/smartmemory clear-server
```

## 16. Privacy, API keys, and maintenance

```text
/privacy export
/privacy delete confirm:DELETE
/privacy retention days:90
/apikey create name:dashboard-reader scope:read
/apikey list
/apikey revoke id:KEY_ID
/reload
/config view
/setup
```

## Final pre-launch checklist

1. `/setup` shows no important permission problems.
2. `/config view` shows the channels you actually intend to use.
3. Private logs, appeals, forms, tickets, modmail, and anonymous logs are staff-only.
4. Homie's role is above every managed role.
5. Welcome, leave, starboard, logging, tickets, forms, and announcements were tested.
6. Automod and anti-raid limits are reviewed before opening the server.
7. Smart replies are limited to mentions or approved channels if enabled.
8. Staff know where logs and cases are stored.
9. Members receive a short announcement explaining the features they can use.

