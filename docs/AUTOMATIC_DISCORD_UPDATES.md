# Automatic Discord update posts

Homie automatically posts newly deployed Git commits to each server's configured update channel when the production bot starts.

## Recommended one-command release

For a completely automatic release, run:

```powershell
npm run release:auto
```

This command sends the current uncommitted diff and untracked source files to Codex for read-only release-note analysis, as explicitly approved for this repository. Codex automatically generates:

1. Change type, such as `feat`, `fix`, or `update`.
2. A short changelog title.
3. A clear description of what changed for members.

It then runs tests, chooses the semantic version bump, previews production, versions and commits the changes, backs up the repository, registers slash commands when needed, deploys production, triggers the PM2-managed bot restart, and publishes the Discord changelog. No prompts or extra release commands are required.

The automatic workflow fails closed: if Codex analysis, tests, backup, slash registration, dependency installation, or deployment fails, it stops instead of prompting for guessed notes or requesting a production restart.

Version bumps are automatic: `feat` uses a minor version, `breaking` uses a major version, and other change types use a patch version.

The automatic restart watcher requires one final manual `pm2 restart homie-prod` when this feature is first installed. Every later `npm run release:auto` writes a deployment signal; the running bot acknowledges it, exits cleanly, PM2 restarts it, and the changelog posts during startup.

For a guided release that shows the generated notes and asks once before committing and deploying, run:

```powershell
npm run release -- -UseCodex
```

Without `-UseCodex`, or if Codex is unavailable, the workflow uses the three short manual prompts.

Configure the channel with:

```text
/config set-update-channel channel:#updates
```

The package version becomes the release version, while the short Git hash is shown only as a build reference. Commits are grouped automatically into **Added**, **Fixed**, **Changed & Updated**, **Security**, **Removed**, **Documentation**, and **Other Changes**. The commit body becomes the member-facing functionality description.

Use a category prefix in commit subjects:

```text
feat: add colour role selection
fix: prevent duplicate live alerts
update: improve starboard formatting
security: restrict mention handling
docs: explain server setup
remove: retire the legacy command
```

Use a clear subject and a useful body:

```text
feat: add colour role selection

Members can browse the colour palette, preview a colour, and assign their chosen colour role without staff assistance.
```

Set the release version in `package.json` before deployment. The production deployment script creates `pending-bot-update.json`. After `pm2 restart homie-prod`, the bot posts the update once and records delivery in `.homie-update-state.json`, preventing duplicate posts on later restarts.

Commits without a body are shown as concise bullet points. Runtime JSON state, `.env`, and other uncommitted files are not announced.

## Backfill existing history

To publish the complete existing Git history as a one-time changelog archive:

```powershell
npm run updates:backfill
```

Then restart production with `pm2 restart homie-prod`. The archive has a unique delivery ID, so it posts even if the current release was already announced. It is split across as many Discord embeds as necessary without dropping commits.

For only the most recent number of commits, pass a count directly:

```powershell
powershell -NoProfile -ExecutionPolicy Bypass -File scripts/backfill_discord_updates.ps1 -Count 25
```
