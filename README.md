# Kortix: the open-source AI Operating System for a self-hosted OpenHands alternative

Kortix is the open-source AI Operating System: your agents, skills, company memory and connectors live in one git repo you own, and every session runs on its own cloud computer.

If you run a coding-agent harness today and you are weighing an OpenHands alternative you can self-host and govern, start here. The guides below take Kortix from install to a governed platform: the open-source stack on your own server, the comparison with OpenHands, and the straight answers to the questions teams ask first.

OpenHands is a self-hosted developer control center for coding agents and automations ([OpenHands on GitHub](https://github.com/OpenHands/OpenHands)). Its job is code: agents read repositories, run terminals and tests, and open pull requests. Kortix is the open-source AI Operating System for the whole company. Agents, skills, memory and connector rules are files in one git repo, every session runs on its own isolated machine, and every change lands through a change request a person reads as a diff.

Both projects are open source and both self-host, so the deciding question is the job. If you need agents that change code in your repositories, OpenHands is a strong specialist. If you need to own and govern the agents, memory and connectors that run across a company, run Kortix.

## What is in this repository

| Guide | The question it answers |
| --- | --- |
| [Install the open-source stack](docs/install.md) | How do I install and run Kortix on my own server? |
| [Kortix vs OpenHands](docs/kortix-vs-openhands.md) | How does Kortix compare with OpenHands for a governed company platform? |
| [Self-hosting for a team](docs/self-hosting.md) | What does self-hosting actually give my team? |
| [FAQ](docs/faq.md) | Alternatives to OpenHands, its openness, and self-hosting an agent platform. |

## The shortest path

The full platform runs as one Docker Compose stack on a Linux server you own:

```bash
curl -fsSL https://kortix.com/install | bash
kortix self-host init --domain kortix.example.com --admin-email you@example.com
kortix self-host start
```

Then run `kortix self-host configure` to answer the setup questions and `kortix self-host doctor` to check the instance. [Install the open-source stack](docs/install.md) has the prerequisites, the DNS records and the CLI path in full.

## Why teams move to Kortix

- **One repo you own.** Agents and skills are markdown, memory is files, and connector rules and triggers are config in one git repo. Grep the whole company, diff any change, roll it back.
- **One gate to land work.** A session works on its own branch and reaches `main` only through a change request. Merge is default-deny for agents.
- **Any model, your keys.** Bring your own provider key, sign in with the ChatGPT subscription you already pay for, or point at your own OpenAI-compatible endpoint.
- **Every business tool.** 3,000+ apps in a click, plus any MCP, OpenAPI, GraphQL or HTTP API, with connector credentials brokered server-side and never entering the machine.
- **Self-host or cloud.** Run it on Kortix Cloud, in your VPC, or on your own on-prem network. Self-hosting is free.

Kortix is open source, and the source is at [Kortix on GitHub](https://github.com/kortix-ai/suna).

## Learn more

The head-to-head write-up is [Kortix vs OpenHands](https://kortix.com/blog/kortix-vs-openhands).

Self-hosting is free, and the managed cloud is there when you want it. Get started with [Kortix](https://kortix.com).
