# Test plugin marketplace

A basic GitHub Copilot plugin marketplace with two independent, dependency-free
test plugins. Neither plugin needs credentials, MCP servers, hooks, or scripts.

| Plugin | Skill | Expected response |
| --- | --- | --- |
| `test-hello` | `test-hello` | `Hello from test-hello!` |
| `test-checklist` | `test-checklist` | A four-item unchecked smoke-test checklist |

## Install

```sh
copilot plugin marketplace add taylorreis/plugin-marketplace
copilot plugin marketplace browse test-marketplace
copilot plugin install test-hello@test-marketplace
copilot plugin install test-checklist@test-marketplace
copilot plugin list
```

Start a new Copilot session after installation. Ask it to `run test-hello`, then
`run test-checklist`. Each skill should produce the response described above
without using tools or modifying files.

## Try a local checkout

From the repository root:

```sh
copilot --plugin-dir ./plugins/test-hello --plugin-dir ./plugins/test-checklist
```

## Layout

The marketplace catalog is in `.claude-plugin/marketplace.json`. Each entry points
to a directory under `plugins/` containing its own `.claude-plugin/plugin.json`
manifest and a skill under `skills/<skill-name>/SKILL.md`.

The catalog uses the relative-source layout demonstrated by
[GitHub's Copilot marketplace](https://github.com/github/copilot-plugins/blob/main/.claude-plugin/marketplace.json).

## Remove

```sh
copilot plugin uninstall test-hello@test-marketplace
copilot plugin uninstall test-checklist@test-marketplace
```
