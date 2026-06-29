# contrib-tools

## Common guidance

Use the cueckoo MCP server's `guidance` tool to get the latest common
guidance for CUE project repos. The server is registered as the
`cueckoo` MCP server (via `cueckoo mcp`). Follow all instructions
returned by the `guidance` tool.

## Project-specific instructions

This repo provides general code and tools for contributors to the CUE
project. The main command is `cueckoo`.

### Building and testing

    go build ./...
    go test ./...
    go tool staticcheck ./...

### Setting up cueckoo for EduWarp projects

1. Install cueckoo:

       go install github.com/EduWarp/contrib-tools/cmd/cueckoo@latest

2. Add a `codereview.cfg` file to the root of your repo with the following
   format (adjusting the org/repo names as needed):

       # Code generated internal/ci/ci_tool.cue; DO NOT EDIT.

       github: https://github.com/EduWarp/<repo-name>
       gerrit: https://review.gerrithub.io/c/EduWarp/<repo-name>

   For example, for the eduwarp repo:

       github: https://github.com/EduWarp/eduwarp
       gerrit: https://review.gerrithub.io/c/EduWarp/eduwarp

3. Run `cueckoo guidance --install` to write the common guidance file.
