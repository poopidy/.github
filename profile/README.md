# poopidy

Source for a Discord bot developed by a group of friends, along with its supporting services and websites. Features are requested in Discord, tracked as todos and job cards, then implemented, tested, and submitted, preferably as pull requests.

## Repositories

| Repository | Contents |
| --- | --- |
| [backend](https://github.com/poopidy/backend) | Everything that runs on the services host, as one uv workspace: the Discord bot and its `hg` commands (`packages/discord`), shared paths, settings, database layer and migrations (`packages/core`), the trading sleeves ledger (`packages/trading`), standalone services (`packages/services`), and deployment (`ops/`). |
| [agent](https://github.com/poopidy/agent) | Agent instructions and supporting tooling: wake prompts, routines, skills, handoff documentation. |
| [web](https://github.com/poopidy/web) | Websites, one app per folder in `apps/`, including the daily puzzle leaderboard (`apps/dle`). |

### Retired

`core`, `discord`, `services` and `infra` were consolidated into **backend** (backend PR #1) and are no longer developed. Make changes in backend instead.

## Architecture

- **backend** holds all runtime code. Its packages share the `poopidy.*` namespace and a single virtual environment.
- **web** does not import backend code; it reads data the bot exports or stores in the shared database.
- **agent** contains prompts, documentation, and supporting tooling; it calls the bot through `hg`. Live data stays in the database.
- Deployment (supervisors, systemd units, database, backups) lives in backend's `ops/`.

## Contributing

- `main` is not protected. Pull requests are optional but preferred.
- Commits follow [Conventional Commits](https://www.conventionalcommits.org/).
- Feature requests are raised in Discord before work begins.
- Secrets are never committed. Each repository runs a secret scan.
