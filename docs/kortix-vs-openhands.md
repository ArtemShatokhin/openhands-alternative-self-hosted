# Kortix vs OpenHands: the open-source company platform or a coding-agent harness

Kortix is the open-source AI Operating System for a whole company; OpenHands is the self-hosted developer control center for coding agents and automations. For a team that runs OpenHands today, the decision is whether to keep those agents on repositories or move them onto a governed company platform.

## Start with the job

OpenHands describes itself as the self-hosted developer control center for coding agents and automations. It runs OpenHands, Claude Code, Codex, Gemini, Pi, OpenCode or any ACP-compatible agent across local, remote and cloud backends ([OpenHands on GitHub](https://github.com/OpenHands/OpenHands)). Its agents read repositories, run terminals and tests, and open pull requests. That is the job it is built for, and it does it well.

Kortix is the open-source AI Operating System. Agents, skills, company memory and connector rules are files in one git repo you own, and every session runs on its own isolated machine. Its job is the whole company, across every department.

## Side by side

| | Kortix | OpenHands |
| --- | --- | --- |
| Open source | Yes | Yes |
| Built for | A whole company's agent workforce | Coding agents and developer automations |
| Where agents run | An isolated machine per session | A local machine, Docker, a VM or a cloud backend |
| Choose your models | Any model, your keys | Any LLM |
| Shared memory | Memory, agents and skills in one git repo | Per-conversation and workspace state |
| Review gate | Every change lands as a reviewed change request | Pull requests on code |
| Self-hosting | Free, on your server, VPC or on-prem | Local, Docker, a VM or company infrastructure |
| Coding depth | Coding is one of the jobs it runs | Deep focus on repos, terminals, tests and pull requests |

## Where Kortix is the fit

- **One repo you own.** Agents and skills are markdown, memory is files, and connector rules and triggers are config in a single git repo. Grep the whole company, diff any change, roll it back.
- **One gate to land work.** A session runs on a branch named after it, the agent commits, and the work reaches `main` only through a change request a person reads as a diff. Merge is default-deny for agents.
- **Any model, your keys.** Pick a model per agent, per session or per message: a provider key you hold, the ChatGPT subscription you already pay for, or your own OpenAI-compatible endpoint.
- **Every business tool.** 3,000+ apps in a click, plus any MCP, OpenAPI, GraphQL or HTTP API. Connector credentials are brokered server-side and never enter the machine, and you set allow, ask or block per tool call.
- **Governance across departments.** Per-resource permissions for people and agents, roles, groups, an audit trail, SAML 2.0 single sign-on and SCIM 2.0. Approval gates you set, off until you set them.
- **Self-host or cloud.** Run it on Kortix Cloud, in your VPC, or on your own on-prem network. Self-hosting is free.

## Where OpenHands is the right call

If your problem is coding agents working on your own repositories, OpenHands is the right tool for the job. It is open source, runs any model, isolates execution with Docker, and ships on a fast release cadence. Its docs also cover a managed cloud and an enterprise offering for teams that do not want to run the backend themselves. A team that wants a self-hosted development control center for code, and nothing beyond it, should start there.

## Making the move

Moving from a coding-agent harness to a company platform changes the question from "can the agent change this code?" to "who owns the agent, what may it touch, and who approves its work?". Kortix answers that with files in a repo you own and one reviewed gate to `main`. The [install guide](install.md) walks through the whole stack on your own server.

The full head-to-head write-up is [Kortix vs OpenHands](https://kortix.com/blog/kortix-vs-openhands). Get started with [Kortix](https://kortix.com).
