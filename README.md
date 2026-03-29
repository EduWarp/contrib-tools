## `contrib-tools`

`contrib-tools` provides general code and tools for contributors to the [EduWarp](https://github.com/EduWarp) project.

### Issues

Please file issues related to this repo at the [EduWarp contrib-tools issue
tracker](https://github.com/EduWarp/contrib-tools/issues) using a
`contrib-tools:` subject prefix.

### `cueckoo` MCP server

The `cueckoo` command includes an MCP server that exposes EduWarp project tools to AI
assistants like Claude Code. Available tools:

- **gerrit_comments** — fetch review comments from a GerritHub change
- **trybot_result** — fetch the latest trybot (CI) result for a GerritHub change
- **guidance** — return the latest common guidance for EduWarp project repos
- **discord_thread** — fetch a Discord thread

#### Setup

Install `cueckoo`:

```
go install github.com/EduWarp/contrib-tools/cmd/cueckoo@latest
```

Add the MCP server to Claude Code:

```
claude mcp add --transport stdio --scope user cueckoo -- cueckoo mcp
```

Some tools have additional requirements:

- `gerrit_comments` and `trybot_result` use `git credential` for GerritHub authentication
- `trybot_result` requires the `gh` CLI to be installed and authenticated
- `discord_thread` requires the `DISCORD_TOKEN` environment variable
