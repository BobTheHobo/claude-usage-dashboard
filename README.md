Download: https://raw.githubusercontent.com/BobTheHobo/claude-usage-dashboard/main/install-usage-dashboard.js (right-click, Save link as)

Already installed? The dashboard checks for new versions itself and tells you in Claude Code; type `/usage-report update` there to install one.

# Claude Code usage dashboard: install

A local dashboard of your Claude Code token usage and estimated cost (by day, project, session, model, tool), built
from the transcripts Claude Code already keeps on your computer. Nothing is uploaded and building it makes no model
calls.

## You need
- Node.js 18 or newer (`node --version`; get it from https://nodejs.org).
- Claude Code 2.1.295 or newer (the desktop app ships its own up-to-date copy).

## Install
1. Save `install-usage-dashboard.js` anywhere (e.g. Downloads).
2. In a terminal, in that folder: `node install-usage-dashboard.js --open`
   It installs into your `~/.claude` folder (Windows: `C:\Users\<you>\.claude`), backs up `settings.json` before
   changing it, and opens a first report.
3. Start a **new** Claude Code session (terminal or desktop app) and type `/usage-report`. Readings of your plan
   limits are collected from then on, after each turn.

## Update, remove
- Update: when a new version is out, Claude Code shows a note at the start of a session; type `/usage-report update`
  (or run `node install-usage-dashboard.js --update`). Your data and any tags you added are kept.
- Remove: `node install-usage-dashboard.js --uninstall` (add `--purge` to also delete the collected data in
  `~/.claude/usage-report`).
- Not sure? Add `--dry-run` to any command to see what it would do.

## Optional: several computers
Off by default. To combine usage from several of your own computers, create an empty **private** git repo you can
push to without a password prompt, then run `node install-usage-dashboard.js --sync <its git url>` on each computer.
Each pushes its usage (token counts, session titles, project folders and branches; no prompt text) to a `usage-data` branch there.
