# Install Perfloop as an MCP server

These steps are for an AI agent, such as Cline, that sets up MCP servers for
its user.

Perfloop is a hosted MCP server at `https://app.perfloop.ai/mcp`. There is
nothing to clone or build, and no API key to paste. The user signs in with
their Perfloop account through OAuth.

## Before you start

The user needs a Perfloop account in a workspace with a connected GitHub
repo. If they have none, they get an account at https://perfloop.ai, and an
Admin connects GitHub and selects repos in Setup in the Perfloop app.

## Add the server

Add this entry under `mcpServers` in the MCP settings file
(`cline_mcp_settings.json` for Cline):

```json
{
  "mcpServers": {
    "perfloop": {
      "type": "streamableHttp",
      "url": "https://app.perfloop.ai/mcp",
      "disabled": false,
      "autoApprove": []
    }
  }
}
```

Keep `"type": "streamableHttp"`; without it, Cline uses the older SSE
transport. Do not add an `Authorization` header. The client finds the sign-in
through the server's 401 response and its OAuth metadata.

## Sign in

When the server asks for authorization, start the OAuth sign-in for
`perfloop`. In the Cline CLI, run `cline mcp` and choose "Authorize OAuth".
The user signs in on Perfloop's page at `auth.perfloop.ai` in the browser.

## Check

List the server's tools, then call `cases`, a read tool. It lists the Cases in
the user's workspace and starts no work. Tools that start work say so, because
that work is paid from the workspace's Usage balance; ask the user before you
call one.

Perfloop opens pull requests. It cannot approve or merge one, and it cannot
deploy. The agent guide, with each job as tool calls, is at
https://perfloop.ai/docs/work/mcp.
