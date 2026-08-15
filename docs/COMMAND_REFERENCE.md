# Homie Command Reference

This page reflects the current Homie command set. Slash commands are mainly used for setup, moderation, administration, and structured workflows. Fun, economy, meme, Quote Hall, ship, and marriage commands are prefix commands so the slash list stays focused.

Homie listens to `h!`, `!h`, and direct `!command` aliases for prefix commands. Examples below use `h!`.

## Recommended setup order

1. Invite Homie and move Homie's role above every role it must manage.
2. Run `/setup`.
3. Run `/config view`.
4. Set core destinations with `/config set-X-channel`.
5. Run `/serverconfig setup-log-channels` if you want Homie to create and route log channels automatically.
6. Configure moderation and safety with `/automod` and `/security`.
7. Configure welcome, leave, autoroles, roles, starboard, reaction roles, and role panels.
8. Configure support, tickets, suggestions, forms, anonymous posts, birthdays, achievements, creator alerts, automation, and smart replies only where needed.
9. Test each enabled feature before announcing it to members.

## Prefix commands

| Command | What it does |
| --- | --- |
| `h! daily` / `!h daily` | Claim daily Homie Coins once per UTC day and keep a visible streak. |
| `h! weekly` / `!weekly` | Claim a larger weekly Homie Coin bonus with an occasional random item drop. Cooldowns display as days, hours, minutes, and seconds. |
| `h! moneybag [@user]` | Check your own or another member balance. |
| `h! pay @user amount` | Transfer Homie Coins to another member. |
| `h! richest` | Show the Homie Coin leaderboard. |
| `h! mint @user amount reason` | Manage Server: add or remove coins manually. |
| `h! gamble all` / `h! gamble 250` / `h! gamble 25%` | Gamble coins with normal wins and a rare jackpot. |
| `h! shop` | Show the game shop. |
| `h! buy item [quantity]` | Buy shop items. Multi-word items can use spaces, for example `h! buy epic crate`. |
| `h! item help` | Show item usage, buying instructions, and aliases. Examples: `h! trap help`, `h! fishing rod help`, `h! epic crate help`. |
| `h! bag` / `h! inventory` | Show owned items and active effects. |
| `h! shield` | Activate a shield that blocks one steal or bomb. |
| `h! trap` | Activate a trap against the next steal attempt. |
| `h! lockpick` | Activate a one-use steal chance bonus. |
| `h! steal @user` | Attempt to steal coins. Base chance is 25%, cooldown is 5 minutes, and the daily limit is 3 attempts per UTC day. |
| `h! bomb @user` | Start the wire-cutting bomb game against an active member. |
| `h! raffle winners duration [prize] [each|split]` | Manage Messages: start a Homie Coin raffle. |
| `h! join` | Join the currently open raffle. |
| `h! scratch` | Use a scratch card. |
| `h! fish` | Fish with a rod. 30-minute cooldown, 3 uses per user per server per day. |
| `h! mine` | Mine with a pickaxe. 30-minute cooldown, 3 uses per user per server per day. |
| `h! hatch` | Start or collect a 48-hour pet egg hatch. |
| `h! pets` | View pets and claim daily pet finds. |
| `h! getquest` | Get one random quest scroll. |
| `h! startquest` | Start your pending quest. |
| `h! quest` | Check progress or claim a completed quest reward. |
| `h! timeskip fish|mine|scratch` | Use a Time Skip on side-activity cooldowns. It does not affect daily rewards or daily use limits. |
| `h! crate common|rare|epic|cursed` | Open a loot crate. |
| `h! meme [category]` / `h! memes [category]` | Post a meme. `nsfw` only works in allowed NSFW meme channels. |
| `h! quote` | Reply to a member message and save it as a Quote Hall card. |
| `h! ship @member` | Generate a daily ship card for yourself and another member. |
| `h! ship @member @member` | Generate a daily ship card for two members. A 100% result asks the shipped member or members to propose. |
| `h! joke` / `h! dadjoke` | Post a joke. |
| `h! fact` / `h! funfacts` | Post a fact. |
| `h! 3amthoughts` | Post a 3AM thought. |
| `h! 8ball question` | Ask the 8-ball. |
| `h! compliment @user` | Send a compliment. |
| `h! roast @user` | Send a playful roast. |
| `h! coinflip` | Flip a coin. |
| `h! afk [reason]` | Set or clear AFK status. |
| `h! avatarget [@user]` | Show a profile picture at full size. |
| `h! addnickname @user nickname` | Manage Nicknames: change a member nickname. |
| `h! marry @user` | Send a marriage proposal. |
| `h! divorce [@user]` | End a saved marriage. |
| `h! marriagecheck [@user]` | Check marriage status. |

## Prefix aliases

All action prefix commands also work as direct bang aliases, for example `!daily`, `!weekly`, `!steal @user`, `!fish`, `!mine`, `!crate epic`, and `!ship @member`.

| Normal command | Extra aliases |
| --- | --- |
| `h! 3amthoughts` | `h! 3am`, `h! 3am thoughts`, `!3amthoughts` |
| `h! 8ball` | `h! 8 ball`, `!8ball` |
| `h! dadjoke` | `h! dadjokes`, `h! dad joke`, `!dadjoke` |
| `h! funfacts` | `h! fun fact`, `h! fun facts`, `!funfacts` |
| `h! avatarget` | `h! avatar`, `h! ava`, `!avatarget` |
| `h! addnickname` | `h! nickname`, `h! nick`, `!addnickname` |
| `h! moneybag` | `h! balance`, `h! bal`, `h! coins`, `h! wallet`, `!moneybag` |
| `h! richest` | `h! leaderboard`, `h! leader board`, `h! lb`, `h! rich list`, `!richest` |
| `h! marriagecheck` | `h! marriage check`, `h! marriage`, `!marriagecheck` |
| `h! scratch` | `h! scratch card`, `!scratch` |
| `h! fish` | `h! fishing rod`, `h! fish rod`, `h! rod`, `!fish` |
| `h! mine` | `h! mining pickaxe`, `h! mining pickax`, `h! pickaxe`, `h! pickax`, `!mine` |
| `h! hatch` | `h! pet egg`, `h! egg`, `!hatch` |
| `h! getquest` | `h! get quest`, `h! quest scroll`, `!getquest` |
| `h! startquest` | `h! start quest`, `!startquest` |
| `h! timeskip` | `h! time skip`, `!timeskip` |
| `h! crate common` | `h! common crate`, `h! crate common`, `!crate common` |
| `h! crate rare` | `h! rare crate`, `h! crate rare`, `!crate rare` |
| `h! crate epic` | `h! epic crate`, `h! crate epic`, `!crate epic` |
| `h! crate cursed` | `h! cursed crate`, `h! crate cursed`, `!crate cursed` |

## Slash commands by setup area

## 01 First setup and server destinations

| Command | What it does | Main inputs |
| --- | --- | --- |
| `/config set-achievements-channel` | Set the achievement announcement channel | `channel:CHANNEL*` |
| `/config set-announce-channel` | Set the /announce output channel | `channel:CHANNEL*` |
| `/config set-anonymous-channel` | Set the anonymous post channel | `channel:CHANNEL*` |
| `/config set-anonymous-log-channel` | Set the anonymous staff trace log channel | `channel:CHANNEL*` |
| `/config set-birthday-channel` | Set the birthday celebration channel | `channel:CHANNEL*` |
| `/config set-game-channel` | Set the game/community channel used in help text | `channel:CHANNEL*` |
| `/config set-greetings-channel` | Set the scheduled greetings and 3AM thoughts channel | `channel:CHANNEL*` |
| `/config set-leave-channel` | Set the leave channel | `channel:CHANNEL*` |
| `/config set-message-log-channel` | Set the message log channel | `channel:CHANNEL*` |
| `/config set-mod-log-channel` | Set the moderation log channel | `channel:CHANNEL*` |
| `/config set-modmail-channel` | Set the staff modmail channel | `channel:CHANNEL*` |
| `/config set-nsfw-channel` | Admin: allow NSFW meme categories in a channel | `channel:CHANNEL*` |
| `/config set-quote-channel` | Set the Quote Hall channel | `channel:CHANNEL*` |
| `/config set-server-log-channel` | Set the general server log channel | `channel:CHANNEL*` |
| `/config set-starboard-channel` | Set the starboard channel | `channel:CHANNEL*` |
| `/config set-suggestion-channel` | Set the suggestion channel | `channel:CHANNEL*` |
| `/config set-tiktok-channel` | Set the default TikTok live alert channel | `channel:CHANNEL*` |
| `/config set-twitch-channel` | Set the default Twitch live alert channel | `channel:CHANNEL*` |
| `/config set-update-channel` | Set the /update output channel | `channel:CHANNEL*` |
| `/config set-user-log-channel` | Set the member/user log channel | `channel:CHANNEL*` |
| `/config set-vent-channel` | Set the anonymous vent channel | `channel:CHANNEL*` |
| `/config set-verification-channel` | Set the /verify channel | `channel:CHANNEL*` |
| `/config set-voice-log-channel` | Set the voice activity log channel | `channel:CHANNEL*` |
| `/config set-welcome-channel` | Set the welcome channel | `channel:CHANNEL*` |
| `/config view` | View this server configuration | - |
| `/language set` | Set the server language | `locale:STRING*` |
| `/language status` | Show the current server language | - |
| `/setup` | Audit bot setup and missing configuration | - |
| `/stats` | Show server health and activity statistics | - |

## 02 Logging and server configuration

| Command | What it does | Main inputs |
| --- | --- | --- |
| `/serverconfig autorole` | Set the role given to new members | `role:ROLE*` |
| `/serverconfig autorole-add` | Add an immediate or delayed role for new members | `role:ROLE*, delay_minutes:INTEGER` |
| `/serverconfig autorole-list` | List immediate and delayed new-member roles | - |
| `/serverconfig autorole-remove` | Remove a role from the new-member role sequence | `role:ROLE*` |
| `/serverconfig branding` | Set Homie branding for this server | `name:STRING, accent:STRING, footer:STRING` |
| `/serverconfig clear` | Clear a community config value | `target:STRING*` |
| `/serverconfig clear-inactive-role` | Clear an inactivity role | `days:STRING*` |
| `/serverconfig leveling` | Enable/disable XP leveling | `enabled:BOOLEAN*` |
| `/serverconfig lock-role` | Set the role Homie denies Send Messages for when locking channels | `role:ROLE*` |
| `/serverconfig set-inactive-role` | Set an inactivity role | `days:STRING*, role:ROLE*` |
| `/serverconfig setup-log-channels` | Create Homie log channels and route each log type | `category_name:STRING` |
| `/serverconfig starboard` | Enable starboard and count reactions from allowed emojis | `enabled:BOOLEAN*, threshold:INTEGER, emojis:STRING` |
| `/serverconfig starboard-emojis` | View the current starboard emoji set and threshold | - |
| `/serverconfig welcome` | Enable/disable welcome messages and set the template | `enabled:BOOLEAN*, image:BOOLEAN, random:BOOLEAN, dm:BOOLEAN, message:STRING, leave_message:STRING` |

## 03 Moderation and cases

| Command | What it does | Main inputs |
| --- | --- | --- |
| `/ban` | Ban a user | - |
| `/cases reason` | Edit a case reason | `number:INTEGER*, reason:STRING*` |
| `/cases recent` | View recent server moderation cases | `limit:INTEGER` |
| `/cases user` | View recent cases for a user | `user:USER*, limit:INTEGER` |
| `/cases view` | View one moderation case | `number:INTEGER*` |
| `/cases void` | Void a case without deleting its audit history | `number:INTEGER*` |
| `/clear` | Delete messages (optionally from a specific user) | - |
| `/kick` | Kick a user | - |
| `/masskick` | Kick all members with a specific role | - |
| `/modtools lock` | Lock a channel for @everyone | `channel:CHANNEL` |
| `/modtools slowmode` | Set channel slowmode | `seconds:INTEGER*, channel:CHANNEL` |
| `/modtools unlock` | Unlock a channel for @everyone | `channel:CHANNEL` |
| `/mute` | Timeout user | - |
| `/note add` | Add a private mod note | `user:USER*, note:STRING*` |
| `/note list` | List mod notes | `user:USER*` |
| `/note remove` | Remove a mod note by ID | `user:USER*, id:STRING*` |
| `/softban` | Ban and immediately unban a user to remove recent messages | - |
| `/tempban` | Temporarily ban a user | - |
| `/unban` | Unban a user | - |
| `/unmute` | Remove timeout | - |
| `/warn` | Warn a user | - |
| `/warninglist` | View all users with warnings ranked by most warnings | - |
| `/warnings remove` | Remove warnings | `user:USER*, mode:STRING*, index:INTEGER, end:INTEGER` |
| `/warnings view` | View warnings | `user:USER*` |

## 04 Protection, verification, and automod

| Command | What it does | Main inputs |
| --- | --- | --- |
| `/automod blockword` | Add a blocked word or phrase | `word:STRING*` |
| `/automod domain` | Add or remove a blocked or allowed domain | `action:STRING*, domain:STRING*` |
| `/automod filters` | Configure spam, links, emoji and attachment filters | `block_invites:BOOLEAN, warning_dms:BOOLEAN, max_links:INTEGER, max_emojis:INTEGER, max_lines:INTEGER, max_attachments:INTEGER, spam_messages:INTEGER, spam_window:INTEGER, duplicates:INTEGER, timeout_minutes:INTEGER` |
| `/automod ignore-channel` | Add or remove an automod channel exemption | `channel:CHANNEL*, ignored:BOOLEAN*` |
| `/automod ignore-role` | Add or remove an automod role exemption | `role:ROLE*, ignored:BOOLEAN*` |
| `/automod limits` | Set mention and caps limits | `mentions:INTEGER, caps_percent:INTEGER` |
| `/automod status` | Show automod settings | - |
| `/automod strikes reset` | Reset a member's Automod escalation history | `user:USER*` |
| `/automod strikes view` | View a member's current strike level and next action | `user:USER*` |
| `/automod toggle` | Turn automod on or off | `enabled:BOOLEAN*` |
| `/automod unblockword` | Remove a blocked word or phrase | `word:STRING*` |
| `/security anti-raid` | Configure join-wave and new-account protection | `enabled:BOOLEAN*, join_threshold:INTEGER, window_seconds:INTEGER, account_age_days:INTEGER, action:STRING, auto_lockdown:BOOLEAN` |
| `/security lockdown` | Immediately lock or unlock public text channels | `enabled:BOOLEAN*` |
| `/security roles` | Set quarantine and verified roles | `quarantine:ROLE, verified:ROLE` |
| `/security status` | Show server security settings | - |
| `/security verification` | Enable or disable account-age verification | `enabled:BOOLEAN*` |
| `/verify` | Complete Homie server verification | - |

## 05 Welcome, leave, autoroles, roles, colours, and levels

| Command | What it does | Main inputs |
| --- | --- | --- |
| `/addrole` | Add a role to a user | - |
| `/colour add` | Admin: add a custom solid colour by hex code | `name:STRING*, hex:STRING*` |
| `/colour add-gradient` | Admin: add a custom gradient colour role | `name:STRING*, start:STRING*, end:STRING*` |
| `/colour add-holographic` | Admin: add a custom holographic role style | `name:STRING*` |
| `/colour clear` | Remove your personal colour role | - |
| `/colour custom` | Choose a server custom colour by name | `name:STRING*` |
| `/colour list` | Show available colour role choices | - |
| `/colour position` | Admin: move all managed colour roles above a selected role | `above:ROLE*` |
| `/colour remove-custom` | Admin: remove a custom colour from Homie | `name:STRING*` |
| `/colour set` | Choose one of the server colour roles | `colour:STRING*` |
| `/colour sync` | Admin: create or verify managed colour roles | - |
| `/createrole` | Create a decorative role with no permissions | - |
| `/deleterole` | Delete a role below your and Homie role hierarchy | - |
| `/level add-xp` | Admin: add XP to a user | `user:USER*, amount:INTEGER*` |
| `/level ignore-channel` | Admin: include or exclude a channel from XP | `channel:CHANNEL*, ignored:BOOLEAN*` |
| `/level ignore-role` | Admin: include or exclude a role from XP | `role:ROLE*, ignored:BOOLEAN*` |
| `/level leaderboard` | Show the XP leaderboard | - |
| `/level multiplier` | Admin: set a channel XP multiplier | `channel:CHANNEL*, value:NUMBER*` |
| `/level rank` | Show a user rank | `user:USER` |
| `/level remove-xp` | Admin: remove XP from a user | `user:USER*, amount:INTEGER*` |
| `/level reset` | Admin: reset a user level and XP | `user:USER*` |
| `/level reward-add` | Admin: add a level role reward | `level:INTEGER*, role:ROLE*` |
| `/level reward-remove` | Admin: remove a level role reward | `level:INTEGER*` |
| `/level rewards` | Show configured level role rewards | - |
| `/level set-xp` | Admin: set a user XP total | `user:USER*, amount:INTEGER*` |
| `/removerole` | Remove a role from a user | - |

## 06 Starboard, reaction roles, and role panels

| Command | What it does | Main inputs |
| --- | --- | --- |
| `/reactionrole add` | Bind an emoji on a message to a role | `message_id:STRING*, emoji:STRING*, role:ROLE*` |
| `/reactionrole list` | List reaction role bindings | - |
| `/reactionrole remove` | Remove a reaction role binding | `message_id:STRING*, emoji:STRING*` |
| `/rolepanel add` | Add a role choice | `panel:STRING*, role:ROLE*, label:STRING*, description:STRING, emoji:STRING` |
| `/rolepanel create` | Create a role panel | `name:STRING*, title:STRING*, description:STRING, exclusive:BOOLEAN, max_roles:INTEGER` |
| `/rolepanel list` | List role panels | - |
| `/rolepanel publish` | Publish or refresh a role panel | `panel:STRING*, channel:CHANNEL*` |

## 07 Tickets, modmail, forms, suggestions, appeals, and feedback

| Command | What it does | Main inputs |
| --- | --- | --- |
| `/appeal review` | Staff: review an appeal | `id:INTEGER*, status:STRING*, response:STRING*` |
| `/appeal submit` | Submit an appeal | `statement:STRING*, case:INTEGER` |
| `/feedback bad` | Report a bad bot reply | `note:STRING*` |
| `/feedback good` | Mark the bot as helpful | `note:STRING` |
| `/feedback list` | Admin: list recent feedback | - |
| `/form create` | Admin: create or update a form | `name:STRING*, description:STRING*, questions:STRING*, destination:CHANNEL*` |
| `/form list` | List available forms | - |
| `/form open` | Open a form | `name:STRING*` |
| `/form panel` | Admin: post a form button | `name:STRING*, channel:CHANNEL*` |
| `/modmail close` | Close the current modmail conversation | `message:STRING` |
| `/modmail reply` | Reply to the member from inside a modmail thread | `message:STRING*` |
| `/suggest` | Submit a community suggestion | - |
| `/suggestion review` | Accept, reject or consider a suggestion | `number:INTEGER*, status:STRING*, response:STRING*` |
| `/ticket add` | Staff: add a user to this ticket | `user:USER*` |
| `/ticket claim` | Staff: claim this ticket | - |
| `/ticket close` | Close this ticket and save a transcript | `reason:STRING` |
| `/ticket list` | Staff: list open tickets | - |
| `/ticket open` | Open a private support ticket | `subject:STRING*` |
| `/ticket panel` | Admin: post an open-ticket button | `channel:CHANNEL*` |
| `/ticket remove` | Staff: remove a user from this ticket | `user:USER*` |
| `/ticket setup` | Admin: configure tickets | `category:CHANNEL*, logs:CHANNEL*, staff:ROLE*` |

## 08 Birthdays, achievements, invites, reminders, and member utilities

| Command | What it does | Main inputs |
| --- | --- | --- |
| `/achievementconfig announce` | Turn achievement unlock announcements on or off | `enabled:BOOLEAN*` |
| `/achievementconfig toggle` | Turn achievement tracking on or off | `enabled:BOOLEAN*` |
| `/achievementconfig view` | View achievement setup | - |
| `/achievements backfill` | Admin: scan existing server history for achievements | `messages-per-channel:INTEGER, announce:BOOLEAN, sync-xp:BOOLEAN, xp-channel:CHANNEL` |
| `/achievements grant` | Admin: manually unlock an achievement | `user:USER*, achievement:STRING*` |
| `/achievements leaderboard` | Show the achievement leaderboard | - |
| `/achievements list` | List available achievements | `category:STRING` |
| `/achievements progress` | View progress for an achievement | `achievement:STRING*, user:USER` |
| `/achievements reset-user` | Admin: reset a user achievement stats and unlocks | `user:USER*` |
| `/achievements set-stat` | Admin: set an achievement stat | `user:USER*, stat:STRING*, value:INTEGER*` |
| `/achievements test-card` | Preview an achievement unlock card | `achievement:STRING` |
| `/achievements view` | View a user achievement profile | `user:USER` |
| `/birthday next` | Show upcoming server birthdays | - |
| `/birthday privacy` | Change your birthday visibility | `visibility:STRING*` |
| `/birthday remove` | Remove your saved birthday | - |
| `/birthday set` | Save your birthday | `day:INTEGER*, month:INTEGER*, year:INTEGER, visibility:STRING` |
| `/birthday today` | Show birthdays happening today | - |
| `/birthday view` | View your saved birthday | - |
| `/birthdayconfig age-visibility` | Set server age display behaviour | `mode:STRING*` |
| `/birthdayconfig clear-role` | Clear the birthday role | - |
| `/birthdayconfig message` | Set the birthday message template | `message:STRING*` |
| `/birthdayconfig role` | Set the optional temporary birthday role | `role:ROLE*` |
| `/birthdayconfig set-user` | Admin: set a birthday for someone | `user:USER*, day:INTEGER*, month:INTEGER*, year:INTEGER, visibility:STRING` |
| `/birthdayconfig test` | Send a test birthday celebration | `user:USER, channel:CHANNEL` |
| `/birthdayconfig time` | Set daily birthday post time | `time:STRING*, timezone:STRING` |
| `/birthdayconfig toggle` | Turn birthday celebrations on or off | `enabled:BOOLEAN*` |
| `/birthdayconfig view` | View birthday setup | - |
| `/highlight add` | Add a keyword | `keyword:STRING*` |
| `/highlight list` | List your highlight keywords | - |
| `/highlight remove` | Remove a keyword | `keyword:STRING*` |
| `/invites leaderboard` | View the invite leaderboard | - |
| `/invites user` | View invite count for a user | `user:USER` |
| `/privacy delete` | Delete or pseudonymize your stored data | `confirm:STRING*` |
| `/privacy export` | Download your stored data for this server | - |
| `/privacy retention` | Admin: set retention for expirable operational records | `days:INTEGER*` |
| `/remind cancel` | Cancel one of your reminders | `id:STRING*` |
| `/remind list` | List your reminders | - |
| `/remind me` | Set a reminder | `in:STRING*, text:STRING*, repeat:STRING` |

## 09 Community content, anonymous posts, venting, Quote Hall, polls, giveaways, and tags

| Command | What it does | Main inputs |
| --- | --- | --- |
| `/anonymous post` | Open a private modal to submit an anonymous post | - |
| `/anonymous view` | View anonymous post setup | - |
| `/giveaway end` | End a giveaway by ID or message ID | `id:STRING*` |
| `/giveaway list` | List active giveaways | - |
| `/giveaway pause` | Pause an active giveaway | `id:STRING*` |
| `/giveaway reroll` | Choose new winners from an ended giveaway | `id:STRING*` |
| `/giveaway resume` | Resume a paused giveaway | `id:STRING*` |
| `/giveaway start` | Start a giveaway | `duration:STRING*, winners:INTEGER*, prize:STRING*, channel:CHANNEL, required_role:ROLE, account_age_days:INTEGER, bonus_role:ROLE, bonus_entries:INTEGER` |
| `/poll` | Create an interactive timed poll | - |
| `/quote reset-number` | Bot owner: clear Quote Hall saves so numbering starts again | `confirm:STRING*` |
| `/tag add` | Admin: add or update a tag | `name:STRING*, content:STRING*` |
| `/tag list` | List tags | - |
| `/tag remove` | Admin: remove a tag | `name:STRING*` |
| `/tag show` | Show a tag | `name:STRING*` |
| `/vent` | Submit an anonymous vent | - |
| `/ventconfig view` | View anonymous vent setup | - |

## 10 Creator alerts

| Command | What it does | Main inputs |
| --- | --- | --- |
| `/tiktokcheck` | Check TikTok link for a user (or yourself) | - |
| `/tiktokdefault clear` | Reset the default TikTok live notification message | - |
| `/tiktokdefault reset-live` | Clear TikTok already-live state so the next live check can notify again | `user:USER` |
| `/tiktokdefault set` | Set the default TikTok live notification message | `message:STRING*, ping:STRING*, role:ROLE` |
| `/tiktokdefault status` | Check TikTok live detection and stored live state | `user:USER` |
| `/tiktokdefault test` | Send a test TikTok notification using the saved default/custom message | `user:USER, channel:CHANNEL` |
| `/tiktokdefault view` | View the current default TikTok live notification message | - |
| `/tiktoklink` | Link your TikTok account | - |
| `/tiktokmessage remove` | Remove custom TikTok message | - |
| `/tiktokmessage set` | Set custom TikTok live message | `message:STRING*` |
| `/tiktokremove` | Admin: remove a user TikTok link | - |
| `/tiktokset` | Admin: set TikTok link for a user | - |
| `/tiktokunlink` | Remove your linked TikTok account | - |
| `/twitch test` | Send a one-off test Twitch live notification | `channel:CHANNEL` |
| `/twitchcheck` | Check Twitch link for a user (or yourself) | - |
| `/youtubedefault clear` | Reset the default YouTube live notification message | - |
| `/youtubedefault reset-live` | Clear YouTube already-live state so the next live check can notify again | `user:USER` |
| `/youtubedefault set` | Set the default YouTube live notification message | `message:STRING*, ping:STRING*, role:ROLE` |
| `/youtubedefault status` | Check YouTube live detection and stored live state | `user:USER` |
| `/youtubedefault test` | Send a test YouTube notification using the saved default/custom message | `user:USER, channel:CHANNEL` |
| `/youtubedefault view` | View the current default YouTube live notification message | - |
| `/youtubelink` | Link your YouTube channel | `channel:STRING*` |
| `/youtubeunlink` | Remove your linked YouTube channel | - |
| `/youtubecheck` | Check YouTube link for a user | `user:USER` |
| `/youtubeconfig channel` | Set the default YouTube live alert channel | `channel:CHANNEL*` |
| `/youtubemessage remove` | Remove custom YouTube message | - |
| `/youtubemessage set` | Set custom YouTube live message | `message:STRING*, image:ATTACHMENT` |
| `/youtubemessage view` | View your custom YouTube live message | - |
| `/youtubeset` | Admin: set YouTube link for a user | `user:USER*, channel:STRING*` |
| `/youtuberemove` | Admin: remove a user YouTube link | `user:USER*` |
| `/twitchdefault clear` | Reset the default Twitch live notification message | - |
| `/twitchdefault set` | Set the default Twitch live notification message | `message:STRING*, ping:STRING*, role:ROLE` |
| `/twitchdefault view` | View the current default Twitch live notification message | - |
| `/twitchlink` | Link your Twitch account | - |
| `/twitchmessage remove` | Remove custom Twitch message | - |
| `/twitchmessage set` | Set custom Twitch live message | `message:STRING*, image:ATTACHMENT` |
| `/twitchmessage view` | View your custom Twitch live message | - |
| `/twitchremove` | Admin: remove a user Twitch link | - |
| `/twitchset` | Admin: set Twitch link for a user | - |
| `/twitchunlink` | Remove your linked Twitch account | - |

## 11 Publishing, automation, counters, cleanup, and voice hubs

| Command | What it does | Main inputs |
| --- | --- | --- |
| `/announce` | Send announcement | - |
| `/automation create` | Create a message-triggered automation | `name:STRING*, phrase:STRING*, action:STRING*, message:STRING, channel:CHANNEL, role:ROLE` |
| `/automation list` | List automations | - |
| `/automation remove` | Remove an automation | `name:STRING*` |
| `/cleanup list` | List cleanup rules | - |
| `/cleanup remove` | Remove a cleanup rule | `channel:CHANNEL*` |
| `/cleanup set` | Automatically delete new messages in a channel | `channel:CHANNEL*, after_seconds:INTEGER*, bots_only:BOOLEAN` |
| `/counter list` | List counter channels | - |
| `/counter remove` | Stop updating a counter channel | `channel:CHANNEL*` |
| `/counter setup` | Use a voice channel as a live counter | `channel:CHANNEL*, type:STRING*, name:STRING*` |
| `/feedback bad` | Report a bad bot reply | `note:STRING*` |
| `/feedback good` | Mark the bot as helpful | `note:STRING` |
| `/feedback list` | Admin: list recent feedback | - |
| `/message edit` | Edit a message previously sent by Homie | `channel:CHANNEL*, message_id:STRING*, content:STRING, title:STRING, description:STRING, colour:STRING` |
| `/message schedule` | Schedule a message or embed | `channel:CHANNEL*, in:STRING*, content:STRING, title:STRING, description:STRING, colour:STRING` |
| `/message send` | Send a managed message or embed | `channel:CHANNEL*, content:STRING, title:STRING, description:STRING, colour:STRING` |
| `/reload` | Reload data files (jokes, facts, roasts, etc.) without restarting | - |
| `/say` | Send a message to a selected channel | - |
| `/update` | Send update | - |
| `/voicehub setup` | Configure a voice hub | `hub:CHANNEL*, category:CHANNEL, name:STRING, limit:INTEGER` |

## 12 Music

| Command | What it does | Main inputs |
| --- | --- | --- |
| `/music pause` | Pause playback | - |
| `/music play` | Play a search result or supported YouTube URL | `query:STRING*` |
| `/music queue` | Show the current queue | - |
| `/music remove` | Remove an upcoming song by its queue number | `position:INTEGER*` |
| `/music repeat` | Repeat one song or the entire queue | `mode:STRING*` |
| `/music resume` | Resume playback | - |
| `/music shuffle` | Shuffle all upcoming songs | - |
| `/music skip` | Skip the current track | - |
| `/music stop` | Stop and clear the queue | - |
| `/music volume` | Set playback volume | `percent:INTEGER*` |

## 13 Smart replies, memory, teaching, unknowns, and API keys

| Command | What it does | Main inputs |
| --- | --- | --- |
| `/apikey create` | Create a key; its secret is shown once | `name:STRING*, scope:STRING*` |
| `/apikey list` | List active API keys without their secrets | - |
| `/apikey revoke` | Revoke an API key | `id:STRING*` |
| `/smartconfig add-channel` | Allow smart replies in a channel | `channel:CHANNEL*` |
| `/smartconfig cooldown` | Set smart reply cooldown seconds | `seconds:INTEGER*` |
| `/smartconfig engine` | Choose how smart replies are generated | `engine:STRING*` |
| `/smartconfig mode` | Control where smart replies are allowed | `mode:STRING*` |
| `/smartconfig personality` | Set smart reply personality | `personality:STRING*` |
| `/smartconfig remove-channel` | Remove a smart reply allowed channel | `channel:CHANNEL*` |
| `/smartmemory clear-channel` | Admin: clear memories saved from a channel | `channel:CHANNEL` |
| `/smartmemory clear-server` | Admin: clear all server-wide memories | - |
| `/smartmemory clear-user` | Admin: clear all memories about a user | `user:USER*` |
| `/smartmemory forget-server` | Admin: delete one saved server memory | `id:STRING*` |
| `/smartmemory forget-user` | Admin: delete one saved user memory | `user:USER*, id:STRING*` |
| `/smartmemory learning` | Admin: enable or disable natural memory learning | `enabled:BOOLEAN*` |
| `/smartmemory my-clear` | Clear memories saved about you | - |
| `/smartmemory my-view` | View memories saved about you | - |
| `/smartmemory remember-me` | Save a memory about yourself for Homie to use | `memory:STRING*` |
| `/smartmemory remember-server` | Admin: save a server-wide memory | `memory:STRING*` |
| `/smartmemory remember-user` | Admin: save a memory about a user | `user:USER*, memory:STRING*` |
| `/smartmemory toggle` | Admin: enable or disable smart memory | `enabled:BOOLEAN*` |
| `/smartmemory view-channel` | Admin: view memories saved from a channel | `channel:CHANNEL` |
| `/smartmemory view-server` | Admin: view server-wide memories | - |
| `/smartmemory view-user` | Admin: view memories saved about a user | `user:USER*` |
| `/teach add` | Add or update a custom reply | `trigger:STRING*, response:STRING*` |
| `/teach list` | List custom replies | - |
| `/teach remove` | Remove a custom reply by its trigger | `trigger:STRING*` |
| `/unknown list` | List recent unknown messages | - |
| `/unknown stats` | Show unknown-message stats | - |

## 14 Other slash commands

| Command | What it does | Main inputs |
| --- | --- | --- |
| `/coinflip` | Flip a coin | - |
| `/help` | Show dynamic help for this server | - |
| `/ping` | Check if bot is online | - |

## Private bot-owner DM routing commands

These are registered privately for the home/support server when configured.

| Command | What it does | Main inputs |
| --- | --- | --- |
| `/dmconfig clear-appeal-contact` | Clear the moderation appeal contact | - |
| `/dmconfig clear-log-channel` | Clear the home-server DM log channel | - |
| `/dmconfig set-appeal-contact` | Set the user mentioned in moderation appeal DMs | `user:USER*` |
| `/dmconfig set-log-channel` | Set the home-server channel where bot DMs are forwarded | `channel:CHANNEL*` |

## Common fixes

- If a slash command is missing, restart Discord and wait a few minutes after deployment because Discord caches command lists.
- If Homie cannot assign, remove, or move a role, move Homie's highest role above that role and confirm the command user can manage it too.
- If a feature does not post, run `/config view`, confirm the destination channel still exists, and check Homie can view and send messages there.
- If a prefix command does not respond, use `h! command` or `!h command` with a space after the prefix, and confirm the feature is allowed in that server/channel.

