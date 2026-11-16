---
name: perfloop
description: Work with Perfloop, which finds performance problems, bugs and security flaws in the user's code and proves changes. Use when the user asks about Perfloop Cases or the Perfloop Inbox, or wants a branch or pull request checked for these problems.
---

# Perfloop

Perfloop finds performance problems, bugs and security flaws in the user's code.
Perfloop measures each performance change it proposes against the original code.
A bug fix or security repair must fail its test on the original code and pass
after the change. The plan and each repo's settings in Setup, a page in the
Perfloop app, decide which kinds of work Perfloop does. A Case is Perfloop's
record of one finding and the work on it.

Security work is defensive: Perfloop finds security flaws in the repos the user
connects and proves fixes for them. It is available on Pro and Enterprise, once
the Perfloop team turns it on for the user's workspace. Only members of the
user's workspace can see a security Case, even for a public repo. When Perfloop
reviews a pull request on a public repo, the review leaves out security
findings. Perfloop does not open a pull request or issue for a security fix on a
public repo. Tell the user they can download the fix from the Case and, if
someone else maintains the repo, send it to them privately. Before you or the
user share a finding, read https://perfloop.ai/docs/work/security.

Perfloop opens pull requests. It cannot approve, merge or deploy.

You use Perfloop through its hosted MCP server.

## Connect

1. The user: get a Perfloop account. Sign up at https://perfloop.ai, or accept
   an invitation to a workspace.
2. An Admin, in the Perfloop app (not you): connect a code host, such as GitHub,
   and select repos in Setup.
3. You: add the remote MCP server `https://app.perfloop.ai/mcp` with the
   Streamable HTTP transport. Do not add an API key or an `Authorization`
   header.
4. Your MCP client opens the sign-in page itself, using the server's OAuth
   metadata. The user signs in with their Perfloop account in the browser.

When the user who signed in is an Admin, you can also choose which repos
Perfloop works on, with the `setup` and `setRepositories` tools. This works for
GitHub and for Cursor Origin. Cursor Origin is another code host, which the
Perfloop team turns on per workspace.

The steps for each coding agent are at https://perfloop.ai/docs/work/mcp.

## Use

- The server's instructions and its guide resource give each job as tool
  calls, in order. Follow the guide for the job the user asked for, and do
  only that job.
- Tools that start work say so in their descriptions, because that work is
  paid from the workspace's Usage balance. Ask the user before you call one.
- Report results as the tools return them, with the Case link. Do not invent
  numbers.

The full agent guide is at https://perfloop.ai/docs/work/mcp.
