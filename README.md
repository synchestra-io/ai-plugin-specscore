# SpecScore AI Plugin

AI plugin for [SpecScore](https://github.com/synchestra-io/specscore) — skills that teach AI agents how to use the `specscore` CLI for spec navigation, linting, and lifecycle operations.

This repository contains the plugin source. It is installed on top of the [`specscore` CLI](https://github.com/synchestra-io/specscore); the CLI is a prerequisite.

## Contents

| Directory | Description |
|---|---|
| [`skills/`](skills/README.md) | Agent skills — one per SpecScore CLI resource group, progressively loaded per-verb |
| [`.claude-plugin/`](.claude-plugin/plugin.json) | Claude Code plugin manifest |

## Install

Via the Synchestra.io meta-marketplace:

```
/plugin marketplace add synchestra-io/ai-marketplace
/plugin install specscore-cli@synchestra-io
```

Requires Claude Code v2.1.110 or later if installed transitively as a dependency of another plugin.

## Relationship to the CLI

The plugin wraps the `specscore` CLI — it does not replace it. Skills encode *when* to call a command, *which* flags to pass, and *how* to interpret exit codes. The CLI contract (commands, flags, exit codes) is defined in [`synchestra-io/specscore`](https://github.com/synchestra-io/specscore).

A change in the CLI surface typically produces a matching skill update in this repository; the two evolve together but release independently.

## Relationship to other plugins

`specscore-cli` is a base-layer **CLI wrapper** plugin. Methodology plugins such as [`spec-driven-development`](https://github.com/synchestra-io/ai-plugin-sdd) depend on it to compose multi-step workflows. See [ADR-0004](https://github.com/synchestra-io/synchestra/blob/main/spec/decisions/0004-layered-plugin-architecture.md) for the full layering rationale.

Sister plugin: [`synchestra-cli`](https://github.com/synchestra-io/ai-plugin-synchestra) — wraps the `synchestra` CLI using the same structure.

## Releases

Releases are tagged as `specscore-cli--v<version>` on this repository to support Claude Code's dependency resolution. See [ADR-0004](https://github.com/synchestra-io/synchestra/blob/main/spec/decisions/0004-layered-plugin-architecture.md#follow-ups) for the convention.

## License

MIT — see [LICENSE](LICENSE).

## Outstanding Questions

None at this time.
