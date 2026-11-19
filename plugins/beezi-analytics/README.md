# Beezi analytics for GitHub Copilot

This plugin shows your own Beezi usage analytics inside GitHub Copilot: spend, sessions, top model, a status and up to three recommendations, for the last 7 or 30 days. It is read-only. It records nothing and changes nothing in Beezi.

## Requirements

A Beezi account. The plugin signs in as you, and the summary covers your default Beezi workspace.

## Install

From Beezi's marketplace:

```
copilot plugin marketplace add Beezi-AI/beezi-copilot-plugin
copilot plugin install beezi-analytics@beezi-copilot
```

## Sign in

Run `/mcp`, choose the `beezi` server, then sign in. A browser window opens for your Beezi sign-in. Until you have signed in, the summary replies with the same instruction.

## Usage

```
/beezi-analytics
/beezi-analytics 30d
/beezi-about
```

`/beezi-analytics` prints the summary for the period you give; with no period it uses 7 days. Key numbers cover all your coding agents; recommendations cover GitHub Copilot unless you ask for all agents. `/beezi-about` explains what the plugin does and where the numbers come from.

## What it connects to

The plugin declares one MCP server, `beezi`, at `https://api.beezi.ai/api/mcp`. It sends the header `X-Beezi-Agent: copilot` so Beezi knows the request comes from GitHub Copilot, and `X-Beezi-Plugin: light` so Beezi offers it only your personal summary. Sign-in goes through `https://clerk.beezi.ai`. The plugin has no hooks, scripts or local code, and it sends nothing from your conversations. It can read only your personal summary; questions about other people are declined.

## The full Beezi plugin

Sessions come from the full Beezi plugin, `beezi`, in this marketplace, which records GitHub Copilot usage. It includes this summary, so install one or the other.

## Links

- Documentation: https://docs.beezi.ai/coding-tool/beezi-analytics-plugin
- Privacy policy: https://beezi.ai/privacy-policy
- Terms: https://beezi.ai/terms-and-conditions
- Support: https://beezi.ai/contact-us

## License

Apache License 2.0. See `LICENSE`.
