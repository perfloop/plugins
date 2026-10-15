# Perfloop

The Performance Machine. A stream of proven pull requests, and software that
stays fast.

Perfloop does always-on performance engineering on your system. It runs
performance experiments and only brings back a performance change with a
measurement against the base. Your engineers set the goals. This repository
connects your coding agent to Perfloop's MCP server at
`https://app.perfloop.ai/mcp`.

With it, your agent can submit a branch or a pull request and read the ranked
hypotheses Perfloop finds on the change. It can read a Case's evidence and
start or stop work on it. It can also steer the work with feedback. Perfloop opens pull requests.
It cannot approve or merge one, and it cannot deploy.

## First run

1. Get a Perfloop account at [perfloop.ai](https://perfloop.ai), or accept an
   invitation to a workspace.
2. An Admin connects a code host, such as GitHub, and selects repos in Setup
   in the Perfloop app. Perfloop works only on selected repos.
3. Install this plugin in your agent (below) and sign in with your Perfloop
   account.
4. Ask your agent to list your Perfloop Cases, or to submit your branch.

The agent guide, with each job as tool calls, is at
[perfloop.ai/docs/work/mcp](https://perfloop.ai/docs/work/mcp).

## Install

Claude Code:

```sh
claude plugin marketplace add perfloop/plugins
claude plugin install perfloop@perfloop
```

Then run `/mcp` and sign in to `perfloop`.

Codex:

```sh
codex plugin marketplace add perfloop/plugins
codex plugin add perfloop@perfloop
codex mcp login perfloop
```

Cursor: [Add to Cursor](https://cursor.com/install-mcp?name=perfloop&config=eyJ1cmwiOiJodHRwczovL2FwcC5wZXJmbG9vcC5haS9tY3AifQ%3D%3D),
then authenticate `perfloop` under Settings, Tools & MCP.

VS Code with GitHub Copilot: [Install in VS Code](https://vscode.dev/redirect/mcp/install?name=perfloop&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fapp.perfloop.ai%2Fmcp%22%7D),
then start the server and sign in when VS Code asks.

Every other agent: the steps are at
[perfloop.ai/docs/work/mcp](https://perfloop.ai/docs/work/mcp).

## What this plugin sends

The plugin holds no code and no credential. It only tells your agent where
the Perfloop MCP server is. Your agent signs in through Perfloop's sign-in
page at `auth.perfloop.ai`, then sends its tool calls and their arguments to
`app.perfloop.ai`. Perfloop does not receive your conversation history. Your
role in the workspace decides what the agent can read or change, and every
write is recorded under your account. Tools that start work say so, because
that work is paid from the workspace's Usage balance.

[Privacy](https://perfloop.ai/privacy) · [Terms](https://perfloop.ai/terms) ·
[Security](https://perfloop.ai/security) · [Support](https://perfloop.ai/contact)
