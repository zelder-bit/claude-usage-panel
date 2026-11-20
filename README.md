# claude-usage-panel

Shows your Claude 5-hour and weekly usage in the XFCE panel, e.g. `5h 62%  wk 9%`.
Each figure turns yellow at 70% and red at 90%. Hover to see reset times; click to open claude.ai usage settings.

## Requirements

- `xfce4-genmon-plugin`
- Python 3 (standard library only)
- Claude Code logged in (the script reads its token from `~/.claude/.credentials.json`)

## Install

```bash
install -m 755 claude-usage-panel ~/.local/bin/
```

Right-click the panel → Add New Items → **Generic Monitor**, then in its Properties set
Command to `~/.local/bin/claude-usage-panel` (full path), Period to `300`, and untick the label.

## Notes

- Uses the undocumented `api.anthropic.com/api/oauth/usage` endpoint (what Claude Code's `/usage` reads); it may change.
- It does not refresh the token. If it expires, the panel shows `Claude ?` until Claude Code next runs.
- `claude-usage-panel --selftest` checks the formatting without a network call.
