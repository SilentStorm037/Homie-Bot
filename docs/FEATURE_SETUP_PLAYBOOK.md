# Homie Feature Setup Playbook

This playbook groups Homie by setup area. Use it when you already know which feature you want and need the shortest path to configure it.

## Setup order at a glance

1. **Foundation:** invite Homie, move its role, run `/setup`, and check `/config view`.
2. **Destinations:** set channels with `/config set-X-channel`.
3. **Logs:** run `/serverconfig setup-log-channels` or manually set log channels.
4. **Safety:** configure `/automod` and `/security`.
5. **Members:** configure welcome, leave, autoroles, verification, roles, and colour roles.
6. **Community:** configure starboard, reaction roles, role panels, birthdays, levels, achievements, Quote Hall, anonymous posts, and economy games.
7. **Support:** configure tickets, modmail, forms, suggestions, and appeals.
8. **Automation:** configure counters, cleanup, scheduled messages, voice hubs, and smart replies.

## Channel setup commands

All normal server destinations use this shape: `/config set-X-channel channel:#channel`.

- `/config set-welcome-channel`
- `/config set-leave-channel`
- `/config set-user-log-channel`
- `/config set-mod-log-channel`
- `/config set-message-log-channel`
- `/config set-server-log-channel`
- `/config set-voice-log-channel`
- `/config set-starboard-channel`
- `/config set-verification-channel`
- `/config set-suggestion-channel`
- `/config set-vent-channel`
- `/config set-anonymous-channel`
- `/config set-anonymous-log-channel`
- `/config set-quote-channel`
- `/config set-achievements-channel`
- `/config set-birthday-channel`
- `/config set-modmail-channel`
- `/config set-announce-channel`
- `/config set-update-channel`
- `/config set-game-channel`
- `/config set-greetings-channel`
- `/config set-twitch-channel`
- `/config set-tiktok-channel`
- `/config set-nsfw-channel`

## Logs

```text
/serverconfig setup-log-channels
```

Manual routes:

```text
/config set-user-log-channel channel:#user-logs
/config set-mod-log-channel channel:#mod-logs
/config set-message-log-channel channel:#messages-logs
/config set-server-log-channel channel:#server-logs
/config set-voice-log-channel channel:#voice-logs
```

## Moderation

Start with `/cases recent`, `/warninglist`, and `/config set-mod-log-channel`. Use `/warn`, `/mute`, `/kick`, `/ban`, `/tempban`, `/softban`, `/unban`, `/clear`, `/modtools`, and `/note` for day-to-day moderation.

## Roles

Use `/addrole`, `/removerole`, `/createrole`, `/deleterole`, `/serverconfig autorole`, `/serverconfig autorole-add`, `/serverconfig lock-role`, `/colour sync`, and `/colour position`. Homie's role must be above every managed role.

## Starboard

```text
/config set-starboard-channel channel:#starboard
/serverconfig starboard enabled:true threshold:3 emojis:star,fire,laugh
/serverconfig starboard-emojis
```

## Reaction roles and role panels

Use `/reactionrole add` when roles should be attached to reactions on an existing message. Use `/rolepanel create`, `/rolepanel add`, and `/rolepanel publish` for button menus.

## Welcome and leave

```text
/config set-welcome-channel channel:#welcome
/config set-leave-channel channel:#goodbye
/serverconfig welcome enabled:true image:true random:true message:Welcome {user} to {server}!
```

## Support workflows

- Tickets: `/ticket setup`, `/ticket panel`, `/ticket open`, `/ticket claim`, `/ticket close`.
- Modmail: `/config set-modmail-channel`, then staff use `/modmail reply` and `/modmail close`.
- Suggestions: `/config set-suggestion-channel`, `/suggest`, `/suggestion review`.
- Forms: `/form create`, `/form panel`, `/form open`, `/form list`.
- Appeals: `/appeal submit`, `/appeal review`.

## Community systems

- Quote Hall: `/config set-quote-channel`, then reply with `h! quote`.
- Anonymous posts: `/config set-anonymous-channel`, `/config set-anonymous-log-channel`, `/anonymous post`.
- Venting: `/config set-vent-channel`, `/vent`.
- Birthdays: `/config set-birthday-channel`, `/birthdayconfig toggle`, `/birthday set`.
- Levels: `/serverconfig leveling`, `/level reward-add`, `/level leaderboard`.
- Achievements: `/config set-achievements-channel`, `/achievementconfig toggle`, `/achievements view`.
- Creator alerts: `/config set-twitch-channel`, `/config set-tiktok-channel`, `/youtubeconfig channel`, then link creators with `/twitchlink`, `/tiktoklink`, or `/youtubelink`.
- Economy and games: `h! daily`, `h! weekly`, `h! shop`, `h! buy`, `h! steal`, `h! bomb`, `h! fish`, `h! mine`, `h! quest`.
- Memes and fun: `h! meme`, `h! ship`, `h! joke`, `h! 8ball`, `h! compliment`, `h! roast`.

## Automation and publishing

Use `/message send`, `/message schedule`, `/message edit`, `/announce`, `/update`, `/automation create`, `/cleanup set`, `/counter setup`, and `/voicehub setup`.

## Smart replies

For a safe non-intrusive setup, use:

```text
/smartconfig mode mode:mentions
/smartconfig cooldown seconds:60
/smartconfig add-channel channel:#bot-chat
```

Then add memory only if the server wants contextual conversations: `/smartmemory toggle`, `/smartmemory learning`, and the `remember-*` commands.
