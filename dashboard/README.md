# Homie Dashboard User Guide

The Homie dashboard gives server owners and administrators a visual way to set up and manage Homie without memorising commands. It works on desktop, tablet, and mobile browsers.

## Signing in

Open the official Homie dashboard link and choose **Continue with Discord**. After authorising access, Homie shows the servers where:

- Homie is present; and
- you own the server, have **Manage Server**, or have **Administrator**.

Select the server you want from **Managing server** in the navigation menu.

If Homie is not in any server you manage, the dashboard displays **Add Homie to a server**. Select it, choose a server in Discord, review the requested access, and approve the installation. The dashboard returns automatically, waits for Discord to finish connecting the server, and opens it ready for setup.

If a server is still missing, select **I already added Homie** to refresh the list. Also confirm you are signed into the correct Discord account and have the required permission in that server.

## First visit

The welcome tour explains the main workflow:

1. Open **Get started**.
2. Review Homie's permissions and setup health.
3. Connect the channels and roles your features need.
4. Configure protection before opening a new server publicly.
5. Personalise welcome messages and community rewards.
6. Add optional support, automation, and creator features.
7. Return to **Home** to review anything unfinished.

Every page includes a short explanation, practical tips, and a recommended next destination.

## One-click server blueprints

On **Get started**, choose a blueprint when you want Homie to build a new or mostly empty server for you:

- **Essential launch** creates Homie's core channels, a sticky colour picker, permissionless colour roles, a general voice lounge, an AFK room, logs, and grouped managed roles.
- **Community server** creates onboarding, a sticky colour picker, permissionless colour roles, social, engagement, staff, and reward areas alongside general, chill, music, and AFK voice rooms.
- **Gaming community** adds a sticky colour picker, permissionless colour and interest roles, game discussion, looking-for-game, clips, game-night areas, squad rooms, and gaming voice lounges.
- **Creator community** adds a sticky colour picker, permissionless colour and interest roles, creator chat, promotion, collaborations, streams, resources, and dedicated creator, collaboration, recording, community, and AFK voice rooms.

The complete palette shown by `/colour list` is available immediately, while each permissionless Discord colour role is created safely only when a member first selects it. This keeps setup fast without reducing the available palette or filling the server with unused roles. Colour roles sit immediately below Homie's highest role and above the grouped Team, Staff, Member, and Interest roles so a selected colour remains visible. Colour and divider roles carry no permissions, and all of them are included in the tracked blueprint erase workflow.

After confirmation, Homie creates and tracks the blueprint's categories, channels, roles, starter messages, reaction roles, sticky guidance, and feature connections for the selected server. The work continues safely in the background while the dashboard follows its live status, so large templates are not interrupted by normal web-request time limits. Existing server resources are left untouched so the blueprint can be removed safely later. Members, conversations, moderation history, and private data are never copied from another Discord server.

Blueprints leave smart replies and memory disabled so the server owner can review and opt into those features separately.

### Erasing and rebuilding

After a blueprint is applied, **Get started** shows a tracked blueprint summary and disables the other blueprint buttons. Select **Erase this blueprint**, then type `ERASE` when prompted.

Homie removes the channels, categories, roles, starter messages, reaction bindings, and stickies recorded in that blueprint's manifest, then restores the settings that existed immediately before it was applied. Resources that existed before the blueprint and unrelated settings changed later are preserved. After erasing, the server can use any blueprint again.

If Discord interrupts setup or removal, the tracked blueprint remains available with an incomplete status. Correct Homie's channel or role permissions and run **Erase this blueprint** again to finish returning to the pre-blueprint state.

## Navigation

| Page | What it manages |
| --- | --- |
| Home | Server health, setup completion, activity, enabled modules, and shortcuts |
| Get started | Permission checks, guided setup, and the recommended configuration order |
| Channels & roles | Feature destinations, autoroles, managed roles, role creation, and core modules |
| Protection | Automod, blocked content, spam limits, anti-raid behavior, quarantine, verification, and lockdown |
| Welcome & rewards | Greetings, starboard, levelling, achievements, birthdays, colours, and economy |
| Smart replies | Reply modes, personality, cooldowns, allowed channels, taught replies, and memory controls |
| Connections | Twitch, TikTok, feeds, counters, and external content sources |
| Advanced settings | Searchable access to detailed server configuration |
| Member support | Tickets, modmail, suggestions, forms, and appeals |
| Automation | Reaction roles, role panels, polls, cleanup, voice hubs, sticky content, and workflows |
| Content library | Tags, custom replies, feedback, and reusable content |
| Publish | Plain messages, embeds, message editing, and scheduling |
| Activity log | Recent dashboard, moderation, and server activity |
| Data & API | Data export, privacy settings, and integration credentials |

## Setup completion checklist

The checklist on **Home** and **Get started** shows which channel destinations and feature switches are configured. It is a setup guide, not a requirement or bot-health score. Your server does **not** need to reach 100%.

Configure the features that are useful for your server and leave unused systems as **Not configured**. For example, Forms and Modmail can remain unused when the server does not need applications or private member-to-staff conversations. Missing items appear first, completed items are marked **Done**, and **Set up** buttons open the relevant dashboard page.

Channel destinations account for 62% of the displayed score and feature activation accounts for 38%. See the [Setup Completion Checklist Guide](../docs/SETUP_COMPLETION_CHECKLIST.md) for every checklist item, privacy recommendations, scoring details, and troubleshooting.

## Desktop navigation

The full navigation is shown on the left. The top search field jumps directly to any dashboard page. The status indicator shows whether Homie is connected.

Use the `?` button for help about the page currently open.

## Mobile navigation

The dashboard automatically switches to its mobile interface on phones and narrow screens.

The bottom navigation provides quick access to:

- Home
- Setup
- Support
- Tools
- More

Choose **More** or the menu button to open every dashboard section. Mobile controls use larger touch targets and account for the browser's visible viewport and safe areas.

## Saving changes

Dashboard forms do not save automatically.

1. Make the required changes.
2. Review the values and selected Discord destinations.
3. Select the page's **Save** button.
4. Wait for the success notification.

An **Unsaved changes** marker appears after editing a form. Homie warns before you change pages, switch servers, close the tab, or refresh with unsaved work.

## Channels and roles

Use **Channels & roles** to decide where Homie publishes each workflow and which roles it may manage.

- Leaving a destination unconfigured keeps that workflow inactive.
- Homie's Discord role must be above every role it assigns or manages.
- Private staff logs should always use private staff channels.
- Verify that Homie can View Channel, Send Messages, Embed Links, Attach Files, and Read Message History where needed.

The role inventory can also create safe decorative roles and remove roles Homie is allowed to manage.

## Protection

The Protection page combines message moderation and join security.

Message controls include:

- blocked words and phrases;
- spam and duplicate-message limits;
- mention and capital-letter limits;
- invite, link, and domain filtering;
- emoji, new-line, and attachment limits;
- ignored channels and roles;
- deletion, warning, or timeout responses.

Join controls include anti-raid thresholds, account-age checks, quarantine, verification roles, and emergency lockdown. Test protection settings with staff before enabling strict actions in a busy server.

## Welcome and rewards

Configure:

- welcome and leave messages;
- welcome images and random messages;
- autoroles;
- starboard destination, threshold, and allowed emojis;
- XP ranges, cooldowns, rewards, exclusions, and multipliers;
- achievement announcements;
- birthdays and age visibility;
- colour-role settings;
- optional community currency.

Message templates support the placeholders described in the [Public Server Setup Guide](../docs/PUBLIC_SERVER_SETUP_GUIDE.md).

## Member support

The support workspace manages tickets, suggestions, forms, appeals, and modmail.

For tickets, select a Discord **category** for new ticket channels, a private log channel, and one or more staff roles. After saving, publish a ticket panel where members can reach it.

Review the privacy of every destination before publishing a support workflow.

## Automation

The Automation workspace manages:

- reaction-role messages and emoji bindings;
- button-based role menus;
- interactive polls;
- automatic cleanup rules;
- temporary voice hubs;
- sticky content;
- trigger-and-action workflows.

Reaction-role messages can use an existing Discord message, plain text created by Homie, or supported Discord JSON. Homie adds the configured reactions and can update the emoji bindings afterward.

## Publishing

The publishing workspace can send plain messages, build embeds, edit managed messages, and schedule future content.

Always verify:

- the destination channel;
- message and embed text;
- images and links;
- schedule date and timezone;
- whether any mention is genuinely intended.

Homie suppresses unexpected mention expansion for safer dashboard publishing.

## Activity and data

The Activity log helps administrators understand what changed and when. Filter entries by action, user, or feature and open an entry for additional context.

Data & API provides user-facing exports, privacy controls, and scoped integration credentials. API secrets are shown once; store them safely and revoke any key that is no longer needed.

## Themes and accessibility

Use the theme button to switch between dark and light appearance. The dashboard follows reduced-motion preferences and removes non-essential animation when the browser requests it.

Keyboard shortcuts on desktop:

| Key | Action |
| --- | --- |
| `/` | Focus page search |
| `?` | Open contextual help |
| `Esc` | Close search results, menus, emoji picker, or help |

## Common problems

### A server is missing

Sign into the correct Discord account and confirm you own the server or have Manage Server/Administrator. Homie must also be present in that server.

### A setting will not save

Read the displayed validation message. Confirm the selected channel or role still exists and that Homie has the required Discord permission.

### Homie cannot assign a role

Move Homie's highest role above the target role in Discord Server Settings.

### A feature saves but does not post

Check that the feature is enabled, its destination is configured, and Homie can view and send messages in that channel. Use `/setup` and `/config view` for a second check.

### Discord login expires

Sign in again. Dashboard sessions expire automatically for account security.

### The mobile interface looks outdated

Refresh the page and reopen it in the current browser. The dashboard selects its layout using the device and current screen width.

## More help

- [Public Server Setup Guide](../docs/PUBLIC_SERVER_SETUP_GUIDE.md)
- [Command Reference](../docs/COMMAND_REFERENCE.md)
- [Privacy Policy](../docs/PRIVACY_POLICY.md)
- [Terms of Service](../docs/TERMS_OF_SERVICE.md)
- [Homie support server](https://discord.gg/RjuSrGXHSa)
