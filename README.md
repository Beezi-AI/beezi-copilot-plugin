# Beezi plugins for GitHub Copilot

Official Beezi plugin for GitHub Copilot — track the cost of AI-assisted work per repository and
branch without leaving the conversation.

| Plugin | Platform | What you get |
| --- | --- | --- |
| `beezi` | Copilot CLI, VS Code (Copilot Agent Host) | Automatic session analytics per repository and branch |

The plugin signs in with your own Beezi account — you must already be a Beezi user, and
everything happens as you, on your tenant.

## GitHub Copilot — `beezi`

Requires Node.js on your `PATH`: the plugin's hooks and MCP server run `node`.

### 1. Install

```bash
copilot plugin marketplace add Beezi-AI/beezi-copilot-plugin
copilot plugin install beezi@beezi-copilot
```

Start a new Copilot session so the plugin loads.

### 2. Link your machine

```
/beezi-login
```

Approve the sign-in in your browser. That's it — from now on, your Copilot sessions are tracked
automatically; you don't need to run anything else.

### Commands

| Command | Purpose |
| --- | --- |
| `/beezi-login` | Link this machine via browser sign-in; run it again to link another account. |
| `/beezi-status` | Show which Beezi accounts are linked here, and whether capture is working. |
| `/beezi-logout` | Unlink one account, or all of them — revokes access and removes the stored credentials. |
| `/beezi-sync` | Upload past Copilot sessions Beezi doesn't have yet; safe to repeat. |
| `/beezi-settings` | Routing rules per repo or folder, default account and Copilot plan, crash reports, status line. |

Skills are prefixed `beezi-` because Copilot already has `/login`, `/logout` and `/settings`.

### Personal analytics summary

Run `/beezi-analytics` for a short read on your own usage — spend, sessions, top model, an alert
status, and up to three recommendations. `/beezi-analytics 30d` widens the window from the default
7 days. The summary always covers just you, whatever your role or plan.

### Updating

```bash
copilot plugin marketplace update beezi-copilot
copilot plugin update beezi
```

Then start a new Copilot session.

### Optional configuration

| Variable | Default | Purpose |
| --- | --- | --- |
| `BEEZI_API_URL` | `https://beezi-api-prod.azurewebsites.net/api` | Beezi API base URL. |
| `BEEZI_MCP_URL` | `<BEEZI_API_URL>/mcp` | Beezi MCP server backing `/beezi-analytics`. |
| `BEEZI_COPILOT_HOME` | `~/.beezi-copilot` | Local state root (queue, cursors, credentials). |

## Privacy

The plugin reports token counts, AI credits, tool-call counts, durations, branch, the sanitized
origin remote, and the session name. Your prompts, code, and your GitHub or Copilot tokens never
leave the machine. Full details: [`plugins/beezi/README.md`](plugins/beezi/README.md#what-this-plugin-sends).

## License

Licensed under the [Apache License, Version 2.0](LICENSE).
