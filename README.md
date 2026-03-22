# Temporal CLI Skill Plugin for Claude Code

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Temporal](https://img.shields.io/badge/temporal-%23000000.svg?style=flat&logo=temporal&logoColor=white)](https://temporal.io/)

A Claude Code plugin that provides comprehensive knowledge for Temporal CLI workflow management. It teaches Claude how to use `temporal`, `base64`, and `jq` together for investigating problems and monitoring the health of a Temporal Cloud environment.

## What it's for

- Rapid workflow investigation: list, describe, history, stack traces, failure patterns
- Environment health checks: counts, filtered lists, query building/validation
- Encapsulated practices: safe list filters, prefix fallbacks, payload decoding, retry analysis

## What it's not

- Not a universal Temporal tool. It intentionally focuses on the `workflow` command group
- No dynamic workflow generation, SDK scaffolding, or broad orchestration features
- For executable MCP tools, see the companion [temporal-cli-mcp](https://github.com/eantyshev/temporal-cli-mcp) server

## Install

```bash
claude plugin install temporal-cli-skill
```

Or from a local clone:

```bash
claude --plugin-dir /path/to/temporal-cli-skill
```

## What's included

### Skill: `temporal-cli`

Invoked as `/temporal-cli` in Claude Code. Provides:

- **Command patterns** for all workflow operations (list, describe, start, signal, query, cancel, terminate, reset, history, stack trace)
- **Query construction** guide with 50+ examples and syntax rules
- **Custom search attributes** usage in queries
- **Payload decoding** recipes using base64 and jq
- **History filtering** patterns for managing large workflow histories
- **Smart patterns** like count-first, auto-retry, and validation
- **Error handling** for common Temporal CLI errors
- **Safety checks** for destructive operations (terminate, reset)

### Asset templates

Pre-built templates in `skills/temporal-cli/assets/`:
- `query-templates.json` — common query patterns
- `jq-filters.json` — reusable jq filters for parsing responses
- `event-types.json` — Temporal event type reference

## Common Investigation Questions

- How many workflows with BuildId X are currently running?
- Which specific workflow executions failed in the last hour?
- What events led to this workflow getting stuck?
- Are there workflows matching pattern Y that need cancellation?
- What's the current status of workflow ABC-123?
- Which workflows are waiting on signals or queries?
- How many retries has this workflow attempted?
- What was the exact input that caused this failure?
- Are there stuck workflows from a specific task queue?
- Which workflows can be safely reset to recover?

## Prerequisites

- **Temporal CLI v1.5.1+** installed and available in PATH
- **Configured environments** in `~/.config/temporalio/temporal.yaml`
- **base64** command-line tool (standard on most systems)
- **jq** JSON processor for parsing and filtering

## Companion MCP Server

For executable tool-based interaction (not just knowledge), use the [temporal-cli-mcp](https://github.com/eantyshev/temporal-cli-mcp) server which exposes Temporal CLI operations as MCP tools.

## License

MIT
