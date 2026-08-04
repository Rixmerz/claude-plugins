# Rixmerz Claude Code marketplace

Owner-namespace marketplace for the Rixmerz Claude Code plugins. This repo only
*indexes* the plugins — each one lives in and is installed from its own
repository.

## Install

```sh
claude plugin marketplace add Rixmerz/claude-plugins
claude plugin install livespec@rixmerz
claude plugin install vise@rixmerz
```

Restart Claude Code afterwards.

## Update

```sh
claude plugin marketplace update rixmerz   # re-read this index
claude plugin update livespec              # or: vise
```

A plugin update requires restarting Claude Code to take effect.

## Plugins

| Plugin | Source | What it does |
|---|---|---|
| `livespec` | [Rixmerz/livespec](https://github.com/Rixmerz/livespec) (`plugin/`) | Code intelligence + Spec traceability: MCP server, subagent, Skill |
| `vise` | [Rixmerz/vise](https://github.com/Rixmerz/vise) | Phase-gated workflows, cross-project experience memory, git snapshots |

## Why a separate repo

`rixmerz` is an owner namespace, not a plugin. Declaring it inside a plugin's
own repository means any *other* repo that also declares a marketplace named
`rixmerz` silently displaces it — Claude Code keys marketplaces by name, so the
last one registered wins and every plugin from the previous one stops
resolving. Keeping the index in its own repo makes the namespace
unambiguous: one manifest owns the name, and plugin repos only ship
`plugin.json`.
