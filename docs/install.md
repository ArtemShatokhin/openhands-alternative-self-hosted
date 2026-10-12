# Install and run the open-source Kortix stack

Kortix is the open-source AI Operating System, and `kortix self-host` installs the full platform on a server you control. Two paths get you running: the whole platform on your server, or the CLI against a project you own.

## What you need

The self-hosted instance is one Docker Compose stack that the `kortix self-host` CLI installs, configures and updates. Sessions run on a cloud sandbox provider, not on the server, so the server must be reachable from the internet.

| Requirement | Detail |
| --- | --- |
| Server | A Linux server with a public IP. |
| DNS | A and AAAA records for your domain and its api subdomain. |
| Ports | 80 and 443 open inbound. |
| Preview DNS | A wildcard `*.p.<domain>` record for sandbox previews. |
| Sandbox provider key | Daytona (the default), Platinum or E2B. Sessions do not start without one. |
| Model provider key | Added in the web app after the first sign-in. |

The bootstrap installs Docker Engine and the Compose plugin when they are missing.

## Path 1: the full platform on your server

### 1. Install the CLI and start the stack

```bash
curl -fsSL https://kortix.com/install | bash
kortix self-host init --domain kortix.example.com --admin-email you@example.com
kortix self-host start
```

`kortix self-host init` writes `docker-compose.yml`, `.env`, a Caddyfile and `updater.sh` into `~/.config/kortix/self-host/<instance>/`. `kortix self-host start` runs `docker compose up`. One Compose project, `kortix-<instance>`, holds every service.

### 2. Answer the setup questions

Run `kortix self-host configure`. It asks the setup questions in order, each pre-filled with the current value, so Enter keeps it:

- Reachability: domain or tunnel.
- Admin email: these people become platform admins.
- Restrict account creation: on by default, so only a platform admin can create a new account.
- Sandbox provider: `daytona`, `platinum` or `e2b`.
- Preview domain.

Then run `kortix self-host start` to apply the answers.

### 3. Sign up as the admin, right away

Open `https://kortix.example.com` and sign up with the admin email. Connect GitHub at `/admin/git`, create the team account and a project, then add a model key.

Do this as soon as the stack starts. Until you set `EMAIL_URL` or `DISABLE_SIGNUP=true`, anyone who reaches the instance can create a confirmed account for any address, the admin address included.

### 4. Check the instance

```bash
kortix self-host doctor
```

Fix every failing check before you invite anyone.

## Path 2: the CLI against a project

```bash
curl -fsSL https://kortix.com/install | bash
kortix login
kortix init my-agent
cd my-agent
kortix ship
kortix sessions new --prompt "Add a skill that drafts the weekly status report"
kortix cr ls
kortix cr diff 1
kortix cr merge 1
git pull
kortix doctor
```

- `kortix init` creates the project directory from the starter and runs `git init -b main`.
- `kortix ship` validates `kortix.yaml`, commits, asks for missing secrets and pushes the current branch.
- `kortix sessions new` starts the default agent on its own branch, named for the session.
- `kortix cr ls`, `kortix cr diff` and `kortix cr merge` review and land the change request the agent opens. `git pull` brings the merged work into your clone.
- `kortix doctor` checks your login and the project.

## What runs where

| Service | What it does |
| --- | --- |
| frontend | The web app. |
| kortix-api | The REST API at `/v1`. |
| llm-gateway | The standalone LLM gateway. |
| kortix-migrate | A one-shot job that migrates the database before `kortix-api` starts. |
| kortix-updater | Pulls new images once a day, migrates and rolls the app services. |
| supabase-* | The Supabase distribution: Postgres, auth, REST, realtime, storage and Kong. |
| caddy | Domain mode. Terminates TLS on ports 80 and 443 and routes traffic. |
| cloudflared | Tunnel mode. Publishes `kortix-api` through a Cloudflare tunnel. |

Reachability has three modes:

| Mode | How you set it | Sessions run |
| --- | --- | --- |
| domain | `--domain <domain>` | yes |
| tunnel | `--tunnel cloudflare` | yes |
| local | neither flag | no, the sandbox cannot reach the API |

Domain mode is the production setup. Tunnel mode is for evaluation on your own machine. Without a domain, the services publish loopback ports: frontend 13737, API 13738 and Supabase 13740.

## Good to know

- The stack has no Redis and no separate worker.
- The images are `kortix/kortix-frontend`, `kortix/kortix-api` and `kortix/kortix-gateway` on Docker Hub. Pulls need no credentials.
- The `kortix-updater` pulls new images once a day and rolls the app services.
- Self-hosting is free. The managed cloud is optional.

The full operator reference is in the [self-hosting docs](https://kortix.com/docs/host). Start with [Kortix](https://kortix.com).
