# Perfloop

Always-on engineering. Every change proven.

Perfloop finds performance problems, bugs and security flaws in your code.
Perfloop measures each performance change it proposes against the original code.
A bug fix or security repair must fail its test on the original code and pass
after the change. Your plan and each repo's settings in Setup decide which kinds
of work Perfloop does. Setup is a page in the Perfloop app. Your team chooses
the repos Perfloop works on and what it should improve. This repository connects
your coding agent to Perfloop's MCP server at `https://app.perfloop.ai/mcp`.

With the MCP server connected, your agent can submit a branch or a pull request
and read the ranked hypotheses Perfloop finds on the change: possible problems,
not yet proven. A Case is Perfloop's record of one finding and the work on it.
Your agent can read a Case and its evidence, and start or stop that work. It can
also send Perfloop feedback on the work. Perfloop opens pull requests. It cannot
approve or merge one, and it cannot deploy.

Security work is defensive: Perfloop finds security flaws in the repos you
connect and proves fixes for them. It is available on the [Pro and Enterprise
plans](https://perfloop.ai/pricing), once the Perfloop team turns it on for your
workspace. Only members of your workspace can see a security Case, even for a
public repo. When Perfloop reviews a pull request on a public repo, the review
leaves out security findings. Perfloop does not open a pull request or issue for
a security fix on a public repo. Download the fix from the Case; if someone else
maintains the repo, send it to them privately. Read the [Security
guide](https://perfloop.ai/docs/work/security) before sharing a finding.

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

## Skill

`skills/perfloop/SKILL.md` tells your agent how to connect to Perfloop and
use it. Claude Code loads it with the plugin. For other agents, install only
the skill from perfloop.ai:

```sh
npx skills add https://perfloop.ai
```

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
