# Homie Setup Completion Checklist Guide

The **Setup Completion checklist** is a dashboard guide that shows which Homie destinations and feature switches have been configured for a Discord server. It appears on **Home** and **Get started**.

The checklist is informational. A server does **not** need to reach 100%, and a lower percentage does not mean Homie is broken or incorrectly installed. Configure only the tools that are useful for your community and leave everything else unconfigured.

## What the percentage means

The percentage describes how much of Homie's available configuration has been filled in:

- **Channel destinations contribute 62%** of the score.
- **Feature activation contributes 38%** of the score.
- The displayed percentage is rounded to the nearest whole number.

There are 20 channel-destination items and 8 feature-activation items. Reaching 100% means every listed destination has a channel and every listed feature is active. It is not a recommendation to enable everything.

For example, a server that does not need creator alerts, forms, tickets, appeals, or modmail should leave those items unconfigured. Its setup percentage will remain below 100%, but the server can still be fully configured for its own needs.

The percentage is not:

- a bot health or uptime score;
- a Discord permission score;
- a requirement for using commands;
- a requirement for receiving support;
- a quality rating for the server; or
- a prompt to enable features the community does not need.

## Reading the checklist

Each checklist item has one of two states:

- **Done** means the relevant destination is selected or the feature is active.
- **Set up** means it is currently unconfigured. Selecting the button opens the relevant dashboard page.

Missing items are shown before completed items so unfinished work is easy to find. The summary shows the number completed and the number remaining.

The checklist reads the server's current saved settings. It does not create channels, enable modules, or change settings by itself.

## Channel destinations

Channel destinations tell Homie where a particular type of message or workflow belongs. One Discord channel may be used for several related destinations, although private logs and staff submissions should use staff-only channels.

| Checklist item | What the destination is used for | Optional? |
| --- | --- | --- |
| Twitch live alerts | Twitch stream notifications | Yes |
| TikTok live alerts | TikTok live notifications | Yes |
| Greetings | General greeting messages | Yes |
| Announcements | Server-wide announcements sent through Homie | Yes |
| Homie updates | Public Homie release notes and feature updates | Yes |
| Welcome | Messages for members joining the server | Yes |
| Leave | Messages for members leaving the server | Yes |
| Starboard | Copies of messages that reach the configured reaction threshold | Yes |
| Achievements | Achievement unlock announcements | Yes |
| Venting | Anonymous vent submissions | Yes |
| Games | Game and event coordination messages | Yes |
| Moderation log | Warnings, timeouts, kicks, bans, and moderation cases | Recommended when using moderation |
| Server log | Supported member and server activity events | Recommended when using event logging |
| DM log | Messages sent directly to Homie that need an owner or staff record | Yes; keep private |
| Tickets | Ticket workflow destination | Yes |
| Ticket logs | Closed-ticket transcripts and history | Recommended when using tickets; keep private |
| Suggestions | Member suggestion posts | Yes |
| Forms | Completed form submissions such as applications and registrations | Yes; usually keep private |
| Appeals | Moderation appeal submissions | Yes; keep private |
| Modmail | Private member-to-staff modmail conversations | Yes; keep private |

### Forms

Forms are structured questionnaires created through Homie. They can be used for staff applications, partnerships, event registration, verification, feedback, or other organised submissions. The connected Forms channel receives completed submissions for review.

If the server does not use forms, leave **Forms** as **Not configured**. This is a valid completed setup decision even though the checklist will continue to show the item as unused.

### Modmail

Modmail gives members a private route to contact server staff. Homie forwards the conversation to the connected staff channel so staff can read and reply without using personal direct messages.

If the server already has another support process or does not need private modmail, leave **Modmail** as **Not configured**.

### Private destinations

The following destinations commonly contain sensitive information and should normally be hidden from ordinary members:

- Moderation log
- Server log, depending on the events recorded
- DM log
- Ticket logs
- Forms
- Appeals
- Modmail

Always review Discord channel permissions after selecting one of these destinations.

## Feature activation

Feature items are marked complete when their saved activation setting is on.

| Checklist item | Marked complete when | Should it always be enabled? |
| --- | --- | --- |
| Welcome system | Welcome messages are enabled | No |
| Starboard | Starboard is enabled | No |
| Leveling | XP and leveling are enabled | No |
| Achievements | Achievement tracking is enabled | No |
| Automod | Message protection is enabled | No; review limits first |
| Event logging | Server event logging is enabled | No; configure private logs first |
| Birthdays | Birthday celebrations are enabled | No |
| Smart replies | The reply mode is not set to Off | No; review channels and memory first |

Do not enable a feature solely to increase the percentage. Configure its channels, roles, limits, messages, and privacy choices first, then test it in Discord.

## Recommended setup workflow

1. Decide which Homie features the server will actually use.
2. Open **Channels & roles** and connect only the destinations required by those features.
3. Keep moderation, support, submission, and transcript channels private.
4. Configure each feature on its dedicated dashboard page before enabling it.
5. Return to **Home** or **Get started** and review the checklist.
6. Use the **Set up** button beside a missing item when it is relevant to the server.
7. Ignore unused items rather than enabling unnecessary systems.
8. Test the configured workflows with staff before announcing them to members.
9. Run `/setup` and `/config view` in Discord for an additional configuration review.

## Choosing a sensible stopping point

There is no universal target percentage. A sensible stopping point is reached when:

- every feature the server intends to use is configured;
- every enabled feature has the required channel and role destinations;
- staff-only information is routed to private channels;
- Homie has the Discord permissions needed for those workflows;
- member-facing messages and interactions have been tested; and
- the remaining checklist items represent features the server intentionally does not use.

At that point, the server's setup is complete for its own requirements, regardless of the displayed percentage.

## Blueprints and the checklist

A Homie blueprint connects many common channels and enables selected community features. It may raise the completion percentage substantially, but it is not designed to force the checklist to 100%.

Blueprints intentionally leave some optional or privacy-sensitive systems for the server owner to review. Smart replies and memory, for example, require an explicit decision. Forms, modmail, appeals, creator alerts, and other specialised workflows may also remain unconfigured.

## Troubleshooting the percentage

### A change is not reflected

1. Confirm the page displayed a successful save notification.
2. Refresh the dashboard.
3. Check that the selected channel or role still exists in Discord.
4. Confirm you are viewing the correct server in the server switcher.
5. Reopen **Home** or **Get started**.

### The score changed by only a few percent

Each destination and feature contributes only part of the total, and the final value is rounded. A saved item may therefore change the score by approximately three to five percentage points.

### A feature works but the score is below 100%

This is expected. Homie evaluates each workflow independently. An unconfigured optional feature does not stop an unrelated configured feature from working.

### Does permission readiness affect the percentage?

No. The permission-readiness panel is a separate check. A destination may be configured while Homie still lacks permission to use it, so both areas should be reviewed.

## Related documentation

- [Public Server Setup Guide](PUBLIC_SERVER_SETUP_GUIDE.md)
- [Dashboard User Guide](../dashboard/README.md)
- [Command Reference](COMMAND_REFERENCE.md)
