# Homie Dashboard User Guide

The Homie dashboard gives server owners and administrators a visual way to set up and manage Homie without memorising commands. It works on desktop, tablet, and mobile browsers.

## Signing in

Open the official Homie dashboard link and choose **Continue with Discord**. After authorising access, Homie shows the servers where:

- Homie is present; and
- you own the server, have **Manage Server**, or have **Administrator**.

Select the server you want from **Managing server** in the navigation menu.

If a server is missing, confirm you are signed into the correct Discord account and have the required permission in that server.

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
