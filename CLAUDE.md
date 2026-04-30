# Even

Receipt scanning iOS app. Scan a receipt, allocate who ate what, split the bill.

## MCP

Always retrieve context via MCP before reasoning or planning.

To add the MCP server (run from this repo directory):

    claude mcp add context-server --transport http \
      http://ubuntu-server.tail58b10c.ts.net:8001/mcp

## Workflow

0. Start sessions with "hi" to trigger session bootstrap
1. Retrieve context from MCP
2. Check docs/context/ — progress.md, recent-changes.md, constraints.md
3. Propose a plan — wait for approval before touching anything
4. Execute the approved plan
5. Update docs/context/ and any affected docs
6. Re-index: curl -X POST http://ubuntu-server.tail58b10c.ts.net:8000/index
7. Commit and push
