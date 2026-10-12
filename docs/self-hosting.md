# What self-hosting gives a team: the open-source Kortix stack

Kortix is the open-source AI Operating System, and self-hosting puts the whole platform on infrastructure you control. What that ownership buys a team comes down to four things: your data, your models, your governance and your review gate.

## Ownership

The self-hosted instance is one Docker Compose stack that the `kortix self-host` CLI installs, configures and updates. What the team keeps:

- Agents, skills, memory and connectors are files in one git repo you own. Grep the whole company, diff any change, roll it back.
- Secrets are encrypted at rest with a key per project.
- Connector credentials are brokered server-side and never enter the machine.
- Run it on Kortix Cloud, in your VPC, or on your own on-prem network. Self-hosting is free.

## Your models

Any model provider with your own keys. Or the ChatGPT plan you already pay for. Or sign in with your OpenCode Console account for OpenCode Zen and Go. Pick the model per agent, per session or per message, and switch the day a better one lands.

## Governance

- Per-resource permissions for people and agents. Roles, groups, and an audit trail.
- Approval gates you set. Off until you set them.
- SAML 2.0 single sign-on and SCIM 2.0.
- Every action is recorded. Reading, exporting and streaming the audit log depend on the plan.

## Review

- One isolated sandbox per session. Each session has its own isolated machine and branch.
- Session work reaches `main` through a change request. Merge is default-deny for agents.
- Nothing merges itself: work lands through a change request a person approves, unless an admin granted the merge capability.

## What self-hosting does not change

Sessions run on a cloud sandbox provider (Daytona by default, or Platinum or E2B), not on the server, so the instance must be reachable from the internet. The stack has no Redis and no separate worker.

## Start

[Install the open-source stack](install.md) to stand up the full platform on a server you own, and read [Kortix vs OpenHands](kortix-vs-openhands.md) if you are moving from a coding-agent harness. Get started with [Kortix](https://kortix.com).
