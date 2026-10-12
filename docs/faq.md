# FAQ: OpenHands alternatives and open-source self-hosting

Kortix is the open-source AI Operating System. The answers below cover the first questions a team asks when it is weighing an OpenHands alternative it can self-host and govern.

## What are some alternatives to OpenHands?

The alternatives fall into three shapes.

- **Kortix** is the open-source AI Operating System for a whole company. Agents, skills, memory and connector rules are files in one git repo you own, every session runs on its own isolated machine, and every change lands through a change request a person reads as a diff. Choose Kortix when you need to own and govern an agent workforce across departments, not just code. The [install guide](install.md) covers the whole stack on your own server.
- **OpenHands Cloud and OpenHands Enterprise** are the same project's managed cloud and its enterprise option for teams that need a managed deployment or commercial support ([OpenHands on GitHub](https://github.com/OpenHands/OpenHands)). They stay inside the coding-agent job.
- **OpenClaw** is an open-source assistant that runs on your own hardware and meets you in the chat apps you already use ([OpenClaw on GitHub](https://github.com/openclaw/openclaw)). It is built around a personal or small shared setup, not a governed company control plane with roles, permissions and review.

For a company that wants one governed system whose agents, memory and connectors live in a repo it owns, Kortix is the pick.

## Is OpenHands open source?

Yes. OpenHands is open source and self-hostable, and it runs on a local machine, in Docker, on a VM or in your company's infrastructure ([OpenHands on GitHub](https://github.com/OpenHands/OpenHands)). Its docs describe a browser client and control center, a Python software agent SDK and agent server, a managed cloud and an enterprise offering. OpenHands is a strong choice when the job is coding agents on your repositories.

Kortix is also open source, and it is the choice when the job is the whole company. Its agents, skills, memory and connectors are files in one git repo you own, and every session runs on its own isolated machine.

## Can you self-host an agent platform?

Yes. Both Kortix and OpenHands self-host, and the difference is what you get from it.

Kortix self-hosts as one Docker Compose stack on a Linux server you own, installed and updated with the `kortix self-host` CLI:

```bash
curl -fsSL https://kortix.com/install | bash
kortix self-host init --domain kortix.example.com --admin-email you@example.com
kortix self-host start
```

Self-hosting a full platform gives you:

- **Ownership.** The repo, the secrets and the configuration stay on your infrastructure. Secrets are encrypted at rest with a key per project, and connector credentials are brokered server-side so they never enter the machine.
- **Your models.** Point Kortix at any model provider with your own keys, use the ChatGPT subscription you already pay for, or sign in with your OpenCode Console account for OpenCode Zen and Go.
- **Governance.** Per-resource permissions for people and agents, roles, groups, an audit trail, SAML 2.0 single sign-on and SCIM 2.0.
- **Review.** Session work reaches `main` through a change request. Merge is default-deny for agents.

Sessions run on a cloud sandbox provider such as Daytona, Platinum or E2B, not on the server, so the instance must be reachable from the internet. The [self-hosting guide](self-hosting.md) covers what that ownership buys a team, and the [install guide](install.md) has the steps.

Get started with [Kortix](https://kortix.com).
