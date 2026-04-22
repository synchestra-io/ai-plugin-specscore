---
name: install
description: Install the specscore CLI via the official get-cli installer. Use when `specscore` is not on PATH, when another skill reports `command not found: specscore`, or when the user asks to install, reinstall, or update the CLI.
user-invocable: true
---

# Install the specscore CLI

This skill installs the [`specscore`](https://github.com/synchestra-io/specscore) CLI — the runtime prerequisite for every other skill in this plugin. It delegates to the official installer at `https://specscore.md/get-cli`, which detects platform and architecture and downloads the matching [GoReleaser](https://goreleaser.com/) archive.

## When to use

- `specscore` is not on `PATH` (e.g., `command -v specscore` returns nothing).
- Another skill in this plugin reported `command not found: specscore` or a pre-flight failure.
- The user explicitly asked to install, reinstall, or update the `specscore` CLI.

## Command

Run exactly this, once:

```bash
curl -fsSL https://specscore.md/get-cli | sh
```

Re-running is safe — the installer replaces the existing binary in place. There is no separate update command; re-running this is the update path.

## Exit codes

| Exit code | Meaning | What to do |
|---|---|---|
| `0` | Install succeeded | Run `specscore --version` to confirm the binary is on `PATH`, then continue with the user's original request. |
| non-zero | Install failed | Surface the installer's stderr to the user verbatim and stop. Do not retry silently. |

## Consent

`curl … | sh` executes a remote shell script. In Claude Code, the Bash permission prompt surfaces the exact command before execution — that prompt is the consent boundary. Do not bypass or pre-approve.

## Platforms

The installer covers macOS (`darwin-{amd64,arm64}`), Linux (`linux-{amd64,arm64}`), and Windows via WSL. Windows users running native PowerShell should follow the manual path at [specscore.md/install](https://specscore.md/install) instead of invoking this skill.
