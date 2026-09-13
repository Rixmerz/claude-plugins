# Rixmerz Claude Code marketplace

Owner-namespace marketplace for the Rixmerz Claude Code plugins. This repo only
*indexes* the plugins — each one lives in and is installed from its own
repository.

## Install

```sh
claude plugin marketplace add Rixmerz/claude-plugins
claude plugin install flowtrace@rixmerz
claude plugin install livespec@rixmerz
claude plugin install vise@rixmerz
claude plugin install android-layout-inspector@rixmerz
```

Restart Claude Code afterwards.

## Update

```sh
claude plugin marketplace update rixmerz   # re-read this index
claude plugin update livespec              # or any other plugin name below
```

A plugin update requires restarting Claude Code to take effect.

## Plugins

| Plugin | Source | What it does |
|---|---|---|
| `flowtrace` | [Rixmerz/flowtrace-debugger](https://github.com/Rixmerz/flowtrace-debugger) (`plugin/`) | Runtime tracing for Java, Python, Node and TypeScript; analyzes `flowtrace.jsonl` |
| `livespec` | [Rixmerz/livespec](https://github.com/Rixmerz/livespec) (`plugin/`) | Code intelligence + Spec traceability: MCP server, subagent, Skill |
| `mini-vise` | [Rixmerz/mini-vise](https://github.com/Rixmerz/mini-vise) (`plugin/`) | Spec-first pipeline: dev, qa, review subagents walk your proposal |
| `vise` | [Rixmerz/vise](https://github.com/Rixmerz/vise) | Phase-gated workflows, cross-project experience memory, git snapshots |
| `eyes` | [Rixmerz/eyes-mcp](https://github.com/Rixmerz/eyes-mcp) | Visual eyes for agents on Hyprland/Wayland: capture monitors, windows or regions inline as PNG |
| `dwg-engine` | [Rixmerz/dwg-engine](https://github.com/Rixmerz/dwg-engine) | Generate real DWG files with no paid CAD — ezdxf + ODA File Converter in Docker |
| `layout-inspector` | [Rixmerz/layout-inspector-mcp](https://github.com/Rixmerz/layout-inspector-mcp) | Measures **web page** layout in a headless browser: overlaps, clipping, truncation, z-index |
| `android-layout-inspector` | [Rixmerz/android-layout-inspector-mcp](https://github.com/Rixmerz/android-layout-inspector-mcp) | Measures a **live Android UI** over adb: overlaps, clipping, sub-48dp touch targets, occluded and unlabeled controls |
| `rastro` | [Rixmerz/rastro](https://github.com/Rixmerz/rastro) | Browser for AI agents: minimal interactive view (~60 tokens a page), causal action-to-effect trace, investigation on demand |

## Why a separate repo

`rixmerz` is an owner namespace, not a plugin. Declaring it inside a plugin's
own repository means any *other* repo that also declares a marketplace named
`rixmerz` silently displaces it — Claude Code keys marketplaces by name, so the
last one registered wins and every plugin from the previous one stops
resolving. Keeping the index in its own repo makes the namespace
unambiguous: one manifest owns the name, and plugin repos only ship
`plugin.json`.
