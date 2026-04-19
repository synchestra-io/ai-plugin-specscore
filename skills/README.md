# Skills

SpecScore skills wrap the `specscore` CLI's command surface. Each skill covers a single CLI resource group; per-verb detail lives under `references/` and loads on demand.

See the [agent-skills feature spec](https://github.com/synchestra-io/synchestra/blob/main/spec/features/agent-skills/README.md) for design principles and the progressive-disclosure model. See [ADR-0002](https://github.com/synchestra-io/synchestra/blob/main/spec/decisions/0002-progressive-disclosure-skills.md) and [ADR-0003](https://github.com/synchestra-io/synchestra/blob/main/spec/decisions/0003-skill-naming-plugin-namespace.md) for the structural and naming rules.

## Invocation

All skills are prefixed with the plugin's manifest name. Users invoke them as:

```
/specscore-cli:<skill-name>
```

## Planned skill catalogue

The skill catalogue mirrors the `specscore` CLI surface. One resource-level skill per command group, per-verb `references/<verb>.md` inside each.

| Skill | Wraps | Verbs |
|---|---|---|
| `feature/` | `specscore feature ...` | `info`, `list`, `tree`, `deps`, `refs`, `new` |
| `task/` | `specscore task ...` | `list`, `info`, `new` |
| `spec/` | `specscore spec ...` | `lint` |
| `code/` | `specscore code ...` | `deps` |
| `idea/` | `specscore idea ...` | TBD — pending CLI migration to strict resource+verb pattern |

The Synchestra.io CLI ecosystem (synchestra, specscore, rehearse) is standardising on a strict `resource + verb` command shape. The top-level `specscore new` command is legacy from before this convention and is not wrapped here; it will be replaced by the appropriate `<resource> new` form in the CLI.

The exact shape of each resource skill follows the template defined in [`agent-skills` feature spec](https://github.com/synchestra-io/synchestra/blob/main/spec/features/agent-skills/README.md#skill-file-format):

```
<resource>/
  SKILL.md         ← index table: user intent → reference file
  references/
    <verb>.md      ← full instructions for one CLI invocation
```

## Status

**Scaffold only.** No skills are implemented yet. This README records the planned catalogue; individual skills ship incrementally as they are authored.

## Outstanding Questions

- The final per-verb list tracks the `specscore` CLI's evolving surface. When new CLI commands land, a corresponding reference file is added here in the same release cycle.
- Whether to ship a `design/` skill in this plugin is **parked**. There is no `specscore design` CLI command today. If one is added later, a wrapping skill lands in the same release. Until then, "design" is purely a methodology concept and lives in the [`spec-driven-development`](https://github.com/synchestra-io/ai-plugin-sdd) plugin.
- Final shape of the `idea/` skill depends on the `specscore` CLI migrating fully to the resource+verb pattern (e.g., `specscore idea new <slug>` instead of the current `specscore idea <slug>`).
